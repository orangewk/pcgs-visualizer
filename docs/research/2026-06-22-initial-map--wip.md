# PCGS 初回観察 論点地図（WIP）

- 作成: 2026-06-22
- 観察者: nu-room の席
- 状態: Phase 1 初回観察。読了範囲は README, AGENTS, TASKS, CODEX_PROMPT, complex_gaussian_splat_note_v4_hidden_spaces.md, pcgs_compact_standalone_note.md, pcgs_concept_note.md, gaussian_splat_quantum_sampling_note.md, pcgs_toy_simulator.html。

この地図は、リポジトリのノート群が何を主張しているか、その主張がどの強さで提示されているかを並べ替えるためのもの。物理理論の評価ではなく、翻訳フレーム/可視化/未検証仮説の境界を引くことが目的。

---

## 0. リポジトリの自己宣言（プロジェクトが取っている姿勢）

リポジトリ本体は、自分自身を「新しい物理理論」ではなく「翻訳フレーム」として位置づけている。AGENTS.md と README.md の「重要な制約」節がもっとも強い境界線である。

> 3DGS の語彙に「位相=矢印」を足すと、量子干渉・density render / event render・デコヒーレンス・隠れ自由度を一貫した可視化語彙で説明できる。

明示的に避ける言い回し（AGENTS.md より）:

- 「標準模型を導出した」
- 「世界の実体が splat cloud だと証明した」
- 「観測問題を解いた」
- 「Born rule を導出した」

この境界はリポジトリ全体で比較的よく守られている。混乱は主に v3 → v4 の修正点（隠れ空間 4 種類の分解）に集中している。

---

## 1. claim level による論点分け

### A. 既存物理から借用している主張（外部に出典がある）

これらは PCGS 固有の主張ではない。ノートが既存の枠組みを採用していることを明示している。

| 主張 | 出典の所在 | コメント |
|---|---|---|
| Born rule \(P=\lvert\Psi\rvert^2\) | 標準量子力学 | ノートは「採用している外部ルール」と明示。「なぜ二乗か」「なぜ一回性か」は導出しない。 |
| Gaussian wavepacket は最小不確定波束 \(\Delta x\Delta p\geq\hbar/2\) | 標準量子力学/量子光学のコヒーレント状態 | compact note §6.2、concept note §3.3。 |
| 高次元 Gaussian は周辺化しても Gaussian | 多変量正規分布の基本性質 | compact note §6.3。 |
| Kaluza-Klein モード \(E_n\sim\hbar c\lvert n\rvert/R\) | KK 理論／余剰次元レビュー | v4 §4.1、concept note §4.2。 |
| プランク長 \(\ell_P=\sqrt{\hbar G/c^3}\approx 1.616255\times 10^{-35}\,\mathrm{m}\) | NIST CODATA 2022 | 値は CODATA 2022 と一致。 |
| デコヒーレンス（環境 trace out で off-diagonal が抑制） | Zurek 系のレビュー | sampling note §4.3、§5。 |
| 多数自由度の \(1/\sqrt N\) 揺らぎ縮小 | 中心極限的議論 | sampling note §4.2。 |
| 標準模型ゲージ群 \(SU(3)_c\times SU(2)_L\times U(1)_Y\) | 標準模型 | v4 §4.2、§4.3。 |
| Hopf 描像と spin 1/2 の 720 度回帰 | スピノル幾何の標準 | v4 §4.3。 |

これらは PCGS の主張ではなく、PCGS が前提として借りているもの。

### B. 翻訳フレーム（PCGS 固有の言い換え）

物理的に新しいわけではないが、3DGS 語彙に量子側を貼り付ける「読み替え辞書」として PCGS が提供している部分。

| 翻訳 | 翻訳元（量子側） | 翻訳先（3DGS 側） |
|---|---|---|
| 複素位相 | global / local phase | phase arrow |
| \(\lvert\Psi\rvert^2\) | 確率分布 | density render |
| \(x_{obs}\sim P\) | 一回の測定 | event render |
| \(\hat P_N\to P\) | 統計収束 | accumulation |
| 干渉項 \(2\mathrm{Re}(\psi_1^*\psi_2)\) | 重ね合わせの off-diagonal | 矢印を足してから長さを測る |
| 隠れ自由度の trace out | marginalization | hidden projection / hidden feature pruning |
| デコヒーレンス | environment entanglement | coherence knob λ（toy では干渉項だけスケール） |
| 内部状態 \(\chi_j\) | spin / gauge / particle species | splat の feature channel |

claim level: **低（語彙の貼り付けに留まり、物理的内容を増やしてはいない）**。

### C. 可視化／toy として実装済みのもの

`pcgs_toy_simulator.html` が実装している範囲。これは「翻訳フレームに沿った 1D toy」で、物理的導出ではない。

| 実装機能 | 数式 | 備考 |
|---|---|---|
| 2 つの complex Gaussian の重ね合わせ | \(\psi_1=G(x+d/2)e^{+ikx}\), \(\psi_1=G(x-d/2)e^{-ikx+i\Delta\phi}\) | 1D。両方とも同じ width σ。 |
| density render | \(P=\lvert\psi_1\rvert^2+\lvert\psi_2\rvert^2+2\lambda\,\mathrm{Re}(\psi_1^*\psi_2)\) | toy 用に λ を直接挿入。 |
| event render | 累積分布から逆変換 sampling | LCG (`1664525, 1013904223`) + 区間内 jitter。 |
| accumulation | event 数 n のヒストグラム | bins=120, 範囲 [-5, 5]。 |
| coherence knob | λ ∈ [0,1] で干渉項のみスケール | 物理的なデコヒーレンス過程は実装していない。あくまで toy 表示。 |
| phase arrow 描画 | 各 splat と sum を矢印で描く | 教育的可視化。 |

未実装（TASKS.md にあるが未着手）:

- リファクタ後の `/src/*.js` 構成、`index.html`
- hidden coordinate \(y\) のマージナル化 (Prototype 3)
- export PNG
- seedable / reset の整理（現在は LCG seed 固定 + reset で初期値復帰のみ）

### D. 未検証仮説 / 未閉鎖の論点（PCGS 自身が明示）

ノートが「ここはまだ閉じていない」と認めている部分。これは肯定的に列挙する。

| 論点 | 出所 | 何が足りないか |
|---|---|---|
| splat 分解の非一意性 | v4 §12.1, compact §9.1, concept §5.3 | 同じ \(\Psi\) を異なる splat cloud で表せる。実在は splat list ではなく \(\Psi\) に置くと表明。 |
| Hamiltonian / action が未指定 | v4 §12.2, compact §9.2 | 時間発展 \(i\hbar\partial_t\Psi=\hat H\Psi\) は書くが \(\hat H\) を与えていない。 |
| Born rule の一回性 | v4 §12.3, sampling §9 | \(\lvert\Psi\rvert^2\) は採用、しかし \(x_{obs}\sim P\) の一回性は外部ルール。 |
| 内部ゲージ群の選択 | v4 §12.4, concept §7.1 | なぜ \(SU(3)\times SU(2)\times U(1)\) かは導出していない。 |
| スピンと弱 SU(2) の分離の 3DGS 的可視化 | v4 §12.5 | 分離は正確化として行ったが、3DGS 語彙では未着地。 |
| 重力／動的計量 | v4 §12.6, concept §7 | \(g_{\mu\nu}\) を動的にするなら splat の置き場が変わる。未着手。 |
| 反証可能性 | v4 §12.7, compact §9.8 | 既存量子論との差分予測が無い。 |
| \(R\sim\ell_P\) の安定化機構 | concept §7 (10.9 相当), compact §9.7 | コンパクト化半径を固定するポテンシャル未指定。 |
| フェルミオン反対称性 | concept §5.5 | Slater 化や反対称化未実装。 |
| 多粒子・場の理論への拡張 | v4 §4.4, sampling §9, compact §9.4 | 配置空間／場の汎関数空間に splat を置く話は語彙のみ。 |

### E. v3 から v4 で意図的に弱められた主張（旧主張は破棄）

v3 の「隠れ空間で矢印が巻く」絵を v4 が比喩に格下げしている。これは PCGS 内部の自己修正であり、特に重要。

| v3 の主張 | v4 の格下げ後 |
|---|---|
| 電荷は隠れ次元の円を巻く回数 | 内部 U(1) fiber の変換性。「物理的余剰空間の円」と同一視しない。\(Q=T_3+Y/2\) で記述する電弱破れ後の組み合わせ。 |
| スピンは球を回す Hopf 的な巻き方 | 局所フレームに対するスピノルの変換性。Hopf 図は可視化補助に留める。 |
| 色荷は三本の矢印を混ぜる | SU(3) 内部 fiber の三成分対称性。可視空間や物理的余剰空間の方向ではない。 |
| スピン SU(2) ≈ 弱 SU(2) | **明示的に分離**。spin SU(2) = 空間回転／局所フレーム、weak \(SU(2)_L\) = 内部ゲージ fiber。 |

この修正は、3DGS 語彙の「splat に矢印が付いている」絵を、物理的余剰空間とは独立な内部 fiber に再配置することに相当する。

---

## 2. 用語の混同しやすい点（ノート v4 が明示している boxed 主張）

ノート v4 自身が boxed で強調している切り分け。これは PCGS を読み解く上での「赤線」。

1. \(\text{物理的余剰空間次元} \neq \text{内部ゲージ fiber}\)
2. \(\text{スピンの } SU(2) \neq \text{標準模型の弱 } SU(2)_L\)
3. \(\text{物理空間上の splat cloud} \neq \text{状態空間上の splat cloud}\)
4. \(\ell_P\text{ で小さい} \Rightarrow \text{物理的余剰空間次元の話}\)
5. \(\text{内部状態が見えない} \neq \ell_P\text{ で小さい}\)

これらは PCGS の「翻訳フレームとしての精度」が乗っている命題。これを薄めると、フレームは物理理論の主張に化けてしまう。

---

## 3. 外部出典が必要な箇所（読者向けに claim を裏付けるなら）

`docs/source-notes/` に置きたい候補。すでに pcgs_concept_note.md §11 が NIST と PDG の URL を列挙しているのが起点。

- **3D Gaussian Splatting 元論文**: Kerbl, Kopanas, Leimkühler, Drettakis (2023), SIGGRAPH / ACM TOG 42(4). フレームの 3DGS 側の語彙はここから借りている。
- **NIST CODATA 2022 Planck length**: \(1.616255(18)\times 10^{-35}\,\mathrm{m}\)。ノートの値は CODATA と一致。
- **Kaluza-Klein コンパクト化レビュー**: 例えば PDG の "Extra Dimensions" レビュー。\(E_n\sim\hbar c\lvert n\rvert/R\) と KK モード塔の標準的扱い。
- **コヒーレント状態 / Gaussian states レビュー**: 量子光学の標準テキスト（Walls & Milburn など）。最小不確定波束の根拠。
- **デコヒーレンス**: Zurek (Rev. Mod. Phys. 2003 など)。off-diagonal 抑制と pointer state の議論。
- **電弱統一における \(Q=T_3+Y/2\)**: 標準的テキスト（Peskin & Schroeder, Cheng & Li）。

これらは「主張の出典」ではなく「PCGS が借りている既存物理の出典」として置く。

---

## 4. 実装側のマッピング（toy simulator が何を見せて何を見せていないか）

`pcgs_toy_simulator.html` が見せているもの:

- 1D で 2 つの complex Gaussian の干渉
- coherence knob による干渉項のみのスケール
- event sample のヒストグラム化
- phase arrow による「矢印を足してから長さを取る」絵

`pcgs_toy_simulator.html` が **見せていない**もの（しかしノートが語彙としては言っている）:

- hidden coordinate \(y\) の周辺化（2D の \(\lvert\Psi(r,y)\rvert^2\) と \(P_{vis}(r)\)）
- 環境との絡みに由来する真のデコヒーレンス（今は λ を直接掛けるだけ）
- 多粒子・もつれ（配置空間に splat を置く話）
- 時間発展（自由 / 二次ポテンシャルでの Gaussian の center / width / chirp の変化）
- KK モード（\(y\) 方向の Fourier 展開）

つまり toy が示せているのは PCGS の翻訳フレームの **density / event / accumulation / λ knob** という横断面のみで、「隠れ空間の 4 種類の分解」は実装側にはまだ降りていない。

---

## 5. 次に確認したい問い（地図の継ぎ目）

地図を引いて見えた、まだ自分の中で解消していない問い。優先順位順。

1. **toy における coherence λ の意味付け**: λ は「干渉項を消す係数」だが、これは density level での toy であり、ρ の off-diagonal 抑制とは導出的につながっていない。λ を物理的なデコヒーレンス時間や環境結合と「写像する／しない」の方針をどこに書くか。
2. **splat 分解の非一意性に対する toy 上の扱い**: 同じ確率場 \(P\) を異なる splat の組で再現できる。toy 上で「splat の数や配置が違っても同じ \(P\) が出る」例を見せる価値があるか。
3. **hidden coordinate \(y\) の toy（Prototype 3）の最小形**: 2D heatmap と 1D marginal の対応を出すなら、KK モードを 1 段だけ重ねるのが教育的。
4. **「事象の階層」と「翻訳の階層」の図**: density render / event render / accumulation / decoherence の 4 段のうち、どこまでが「翻訳」でどこからが「ヒューリスティック」か、図にしてしまった方が claim level 表が読みやすい。
5. **chat.md / notes.md に残すべき外部観測の見分け**: chat.md は「外から届いた言葉が観測として置かれる」と明示されているが、現状空。観測が来たら、ノート側に「届いたものの id」「自分の独白」「研究への影響」を分けて残す形にしておきたい。

---

## 6. この地図の使い方（自分宛て）

- これは WIP。読み終わったら finalize 版を `docs/research/2026-06-22-initial-map.md` に切り出す。
- claim level 表（A〜E）は、新しい節を加えるたびに更新する。
- 外部出典が必要な箇所が増えたら §3 に積み、`docs/source-notes/` に該当ファイルを起こす。
- toy simulator 側に何かを足す前に、まずこの地図に「どの claim level の話か」を書き足す。
