# Codex Entry Prompt

あなたはこのリポジトリを引き継ぐ coding agent です。目的は、会話から生まれた「Complex Gaussian Splat Cloud / PCGS」フレームを、読めるドキュメントと動く可視化プロトタイプに整理することです。

## 立ち位置

このプロジェクトは新しい物理法則の証明ではありません。主張は以下です。

> 3D Gaussian Splatting の語彙に「位相=矢印」を足すと、量子干渉、density render / event render、デコヒーレンス、隠れ自由度を直感的に翻訳できる。

この区別を守ってください。

- OK: 「翻訳フレーム」「認知モデル」「可視化モデル」「toy simulation」
- NG: 「標準模型を導出した」「世界の実体が splat cloud だと証明した」「新しい物理理論として完成した」

## 最初に読むファイル

1. `README.md`
2. `complex_gaussian_splat_note_v4_hidden_spaces.md`
3. `pcgs_toy_simulator.html`
4. `TASKS.md`
5. `AGENTS.md`

## 実装の第一目標

`pcgs_toy_simulator.html` を、保守しやすい小さな静的サイトにする。

推奨構成:

```text
/index.html
/src/main.js
/src/math.js
/src/render.js
/src/sampling.js
/src/ui.js
/docs/concept.md
/docs/hidden-spaces.md
/docs/simulation-grammar.md
/assets/
```

外部依存は最小にしてください。まずは vanilla HTML/CSS/JS で十分です。

## 実装すべき機能

### Prototype 1: complex Gaussian interference

- 1D canvas に2つの Gaussian wavepacket を描画。
- sliders:
  - separation
  - width
  - momentum k
  - phase delta
  - coherence lambda
  - sample count
- 表示:
  - wavepacket density components
  - interference probability field \(P=|\psi_1+\psi_2|^2\)
  - event samples
  - accumulated histogram

### Prototype 2: decoherence knob

干渉項だけを以下のように制御する。

```math
P_\lambda(x)=|\psi_1|^2+|\psi_2|^2+2\lambda\mathrm{Re}(\psi_1^*\psi_2)
```

- \(\lambda=1\): coherent interference
- \(\lambda=0\): classical mixture

### Prototype 3: hidden coordinate projection

余力があれば、2D grid \((r,y)\) で \(\Psi(r,y)\) を作り、

```math
P_{vis}(r)=\int dy\,|\Psi(r,y)|^2
```

を可視化する。

## ドキュメント化

以下を短く、単体で読めるように書く。

- `docs/concept.md`: 3DGS + phase arrow の主張
- `docs/simulation-grammar.md`: density render / event render / accumulation / decoherence
- `docs/hidden-spaces.md`: 隠れ空間の分解
- `docs/limits.md`: 未閉鎖点、過剰主張の禁止

## 品質条件

- 数式とコードの対応を明記する。
- UI の用語はノートの語彙と揃える。
- 乱数 sampling は seedable にするか、reset ボタンを置く。
- ブラウザでローカル実行できること。
- 物理的主張を強めすぎないこと。

## 終了条件

Codex のタスク完了時には、以下を報告してください。

1. 変更したファイル一覧
2. 実装した機能
3. 実行方法
4. 既知の制限
5. 次にやるべきこと

