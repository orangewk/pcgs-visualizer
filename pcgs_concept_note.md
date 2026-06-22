# Planck-Compact Complex Gaussian Splat Model（PCGS）概念ノート

**版:** 0.1  
**目的:** 会話から生まれた仮説を、他者に見せられる形で整理する。  
**位置づけ:** これは確立済み物理理論ではなく、量子・余剰次元・観測世界を「complex Gaussian splat cloud」として再記述するための思考モデルである。

---

## 0. 要約

このノートの中心仮説は次である。

> 観測可能な世界は、有限分解能で見ると局所的な blob / splat の集合として現れる。  
> したがって、世界状態を **複素 anisotropic Gaussian splat の点群**として表現する。  
> 観測できない余剰次元はプランク長スケールにコンパクト化され、低エネルギーでは励起されず、観測時には積分消去される。

最小定式化は以下。

\[
M = \mathbb{R}^3 \times K_6,\qquad \mathrm{size}(K_6)\sim \ell_P
\]

\[
\Psi(r,y,t)=\sum_{j=1}^{K} c_j(t)\,g_j(r,y,t)\,\chi_j
\]

\[
g_j(z,t)=N_j
\exp\left[
-\frac12(z-q_j)^T A_j(z-q_j)
+\frac{i}{\hbar}p_j^T(z-q_j)
+i\phi_j
\right]
\]

\[
z=(r,y),\qquad r\in\mathbb{R}^3,\quad y\in K_6
\]

観測可能な3次元分布は、隠れ次元を積分して得る。

\[
P_{\mathrm{vis}}(r,t)=\int_{K_6}dy\,\Psi^\dagger(r,y,t)\Psi(r,y,t)
\]

低エネルギーでは、隠れ次元の非ゼロモードが励起されないため、通常の3次元量子論に近い形へ落ちる。

\[
\Psi(r,y,t)\approx \psi_0(r,t)\eta_0(y)
\]

\[
P_{\mathrm{vis}}(r,t)\approx |\psi_0(r,t)|^2
\]

---

## 1. 会話の経緯：話者弁別ログ

### 1.1 プランク長と「全部が一点にあること」の違い

**User:**  
プランク長の次元とは、全部が一点にあることと何が違うのか。この概念は何を解決しているのか。

**Assistant:**  
プランク長は「全部が一点に重なっている」という主張ではない。むしろ、空間を無限に細かく区別できるという想定が破綻する可能性を示すスケールである。  
「全部が一点」は距離が全てゼロという主張だが、プランク長は「それ以下の距離差を物理的に定義・測定できるか怪しい」という境界である。

**整理:**

- 「全部が一点」: 空間的区別が消える。
- 「プランク長」: 空間的区別の分解能限界、または理論の適用限界。
- 解決対象: 特異点、無限大、量子論と重力の衝突点。

---

### 1.2 なぜプランク長が出るのか

**User:**  
なぜその概念を必要としたのか。整合のためだったのか。

**Assistant:**  
量子論では、小さい距離を測るには高エネルギーが必要になる。一般相対論では、エネルギーは重力源であり、極小領域に集中するとブラックホール化する。  
したがって、量子論・相対論・重力を同時に考えると、通常の「距離を測る」という操作があるスケールで自壊する。その境界としてプランク長が現れる。

\[
\ell_P=\sqrt{\frac{\hbar G}{c^3}}
\]

**整理:**

- プランク長は追加された空間次元ではない。
- \(\hbar\)、\(G\)、\(c\) を組み合わせると自然に出る長さスケール。
- これは「理論がここで怪しくなる」という警告線であり、実験で余剰次元のサイズとして測られた値ではない。

---

### 1.3 余剰次元は本当にプランク長なのか

**User:**  
量子論と重力を整合させるにはプランク長の次元が必要だったということか。確か複数次元をプランク長に設定したのではないか。

**Assistant:**  
それはおそらく弦理論やKaluza-Klein型の余剰次元の話である。超弦理論では10次元時空、M理論では11次元時空が現れ、観測されない空間次元を小さく丸める。  
ただし、余剰次元のサイズが必ずプランク長である必要はない。プランク長や弦長程度に小さいと見えない、というだけである。

**整理:**

- プランク長: 量子重力スケール。
- 余剰次元: 理論の整合性から出る可能性がある追加空間方向。
- コンパクト化: 余剰次元を小さく丸め、低エネルギー世界から隠す操作。
- サイズはモデル依存であり、必ず \(\ell_P\) ではない。

---

### 1.4 ground truth はどこか

**User:**  
プランク長である根拠が見当たらない。もっと長くても前提を充足できないのか。ground truth はどこなのか。

**Assistant:**  
その疑問は妥当。余剰次元のサイズがプランク長でなければならないという観測的根拠はない。  
必要条件は「見えていないこと」であり、必ずしも「プランク長であること」ではない。もっと大きな余剰次元を仮定するモデルも存在する。

**整理:**

余剰次元が半径 \(R\) の円にコンパクト化されていると、余剰次元方向のモードはKaluza-Kleinモードとして現れる。

\[
\Psi(r,y)=\sum_{n\in\mathbb{Z}}\psi_n(r)e^{iny/R}
\]

非ゼロモードのエネルギーは概略的に

\[
E_n\sim \frac{\hbar c |n|}{R}
\]

となる。したがって、\(R\) が小さいほど励起エネルギーは大きくなり、低エネルギー実験では見えない。

**ground truth:**

- 観測可能な世界は3空間+1時間に見えている。
- 余剰次元は未発見。
- サイズ・形・数は未確定。
- プランク長は安全で自然な候補だが、観測で確定したサイズではない。

---

### 1.5 量子は見えない次元を使って壁を通り抜けるのか

**User:**  
光子やその他の量子は、見えていない次元を使って、壁通り抜けや波動/粒子的な不思議な結果を生み出しているのか。

**Assistant:**  
標準的な理解では、そうではない。トンネル効果や干渉は、余剰次元を使った迂回ではなく、3次元空間上の複素確率振幅の性質で説明される。  
壁抜けは、波動関数の tail が障壁の向こう側にも非ゼロで残るために起こる。

\[
\psi(x)\sim e^{-\kappa x}
\]

**整理:**

- 量子トンネルは「別次元の隠し通路」ではない。
- 量子は測定前に一点粒子として経路を持つというより、確率振幅として広がる。
- 余剰次元が存在しても、通常の量子現象の説明には不要。

---

### 1.6 量子とは Gaussian splat のようなものか

**User:**  
もっと何が何だかを理解したい。量子とは gaussian splat みたいなものか。

**Assistant:**  
比喩としてかなり近い。ただし、普通の密度雲ではなく、複素数の確率振幅を持つ splat と見る必要がある。  
Gaussian wavepacket は以下のように表せる。

\[
\psi(x)=A e^{-\frac{(x-x_0)^2}{4\sigma^2}} e^{ikx}
\]

前半が位置の広がり、後半が位相・運動量を表す。

**整理:**

- Gaussian splat 的: 中心と幅を持つ。
- 量子的: 位相を持つため干渉する。
- 観測: 広がった分布全体ではなく、1点イベントとして検出される。

---

### 1.7 10D Gaussian splat と見た場合のパラメータ

**User:**  
10D Gaussian splat と見たら、パラメータは何を持っているのか。

**Assistant:**  
普通の10D Gaussianなら、中心10個、共分散55個、重み1個を持つ。量子版なら、さらに運動量、位相、複素共分散、内部状態が必要になる。

1個の量子 Gaussian primitive:

\[
g_j(x,t)=N_j
\exp\left[
-\frac12(x-q_j)^T A_j(x-q_j)
+\frac{i}{\hbar}p_j^T(x-q_j)
+i\phi_j
\right]
\]

\[
A_j=\Gamma_j+iK_j
\]

**パラメータ:**

| 記号 | 意味 |
|---|---|
| \(q_j\) | 中心位置 |
| \(p_j\) | 運動量、位相勾配 |
| \(\Gamma_j\) | 実際の広がり、楕円体形状 |
| \(K_j\) | 位相曲率、chirp、収束・発散 |
| \(c_j\) | 複素重み |
| \(\phi_j\) | 位相 |
| \(\chi_j\) | スピン、偏光、電荷、色荷などの内部状態 |

---

### 1.8 世界記述理論として整合するか

**User:**  
これは世界を記述する理論として整合するか。

**Assistant:**  
表現形式としては整合しうる。量子状態を複素 Gaussian splat の重ね合わせとして表すことは自然である。  
ただし、それだけでは完成した基礎理論ではない。時間発展、相互作用、観測規則、標準模型、フェルミオン、ゲージ対称性、重力などを定義する必要がある。

**整理:**

- 「量子状態を complex Gaussian splat cloud で表す」なら整合的。
- 「世界の根本実体が Gaussian splat そのもの」なら追加原理が必要。
- 特に、splat 分解の非一意性が問題になる。

---

### 1.9 点群として考えていたという補足

**User:**  
最初から点群のつもりだった。世界は1個の楕円 blob ではなく、大量の anisotropic Gaussian primitive で近似するという意味だった。

**Assistant:**  
その前提なら、かなり筋が通る。  
ただし、各点は物理空間内の小物体ではなく、量子状態を構成する primitive と見る方が安全である。

\[
\Psi(x)=\sum_j c_jg_j(x)
\]

CG対応:

| CG Gaussian splat | 量子版 |
|---|---|
| position | 状態中心 |
| covariance / scale / rotation | 不確定性楕円体 |
| opacity | 振幅の重み |
| color / feature | 内部量子数 |
| alpha blending | 複素振幅の重ね合わせ |
| rendered image | 測定確率分布 |
| camera | 測定基底 |
| rasterizer | Born rule / 観測演算子 |

---

### 1.10 理論としてまとめるならどうなるか

**User:**  
理論としてまとめるならどうなるか。出力形式自体も謎だが、数式がよいか。

**Assistant:**  
理論骨格は以下の3本で書ける。

状態:

\[
\Psi(x,t)=\sum_j c_j(t)g_j(x,t)\chi_j
\]

時間発展:

\[
i\hbar\partial_t\Psi=\hat H\Psi
\]

観測:

\[
P(a)=\langle\Psi|E_a|\Psi\rangle
\]

つまり、splat cloud、dynamics、renderer を定義する必要がある。

---

### 1.11 なぜ Gaussian splat なのか

**User:**  
なぜ Gaussian splat なのか。世界がそう見えるからという素朴主義が出発点である。観測できない次元をプランク長と仮定し、見えている現実にそぐうように理論を組むならどうなるか、という話の敷衍である。

**Assistant:**  
その場合、Gaussian は「世界が本当に Gaussian でできている」という断定ではなく、「有限分解能で観測される世界を再現するための最小表現 primitive」として採用するのが筋がよい。  
隠れ次元をプランク長スケールにコンパクト化し、低エネルギーではゼロモードだけが残るようにすれば、見えている3次元世界と矛盾しにくい。

**整理:**

Gaussian を採用する理由:

1. 有限分解能で得られる情報は中心・広がり・向き・強度程度である。
2. 平均と共分散だけを指定したとき、Gaussian は最大エントロピー分布である。
3. Gaussian wavepacket は最小不確定波束になる。
4. 高次元 Gaussian は周辺化・射影しても Gaussian になる。
5. 自由運動や二次ポテンシャルでは Gaussian は形を保ちやすい。

---

## 2. 提案理論：PCGSの基本構成

### 2.1 基本姿勢

PCGSは、次の素朴主義から始まる。

> 世界は観測上、点的なものではなく、有限分解能の局所的 blob / splat の集合として見える。  
> ならば、その見え方を基本 primitive として採用し、高次元量子状態を Gaussian splat cloud として表す。

ここでの Gaussian splat は、CGにおける可視密度 primitive ではなく、**複素確率振幅 primitive**である。

---

### 2.2 空間構造

可視空間を \(r\)、隠れ次元を \(y\) とする。

\[
z=(r,y)
\]

\[
r\in\mathbb{R}^3
\]

\[
y\in K_6
\]

10次元時空を想定するなら、構造は概略的に

\[
3\text{ visible space}+6\text{ hidden space}+1\text{ time}
\]

である。

隠れ次元はプランク長程度の大きさにコンパクト化されていると仮定する。

\[
\mathrm{size}(K_6)\sim\ell_P
\]

単純化して6個の円として扱うなら、

\[
K_6=(S^1_{\ell_P})^6
\]

\[
y^a\sim y^a+2\pi\ell_P
\]

---

### 2.3 状態

世界状態を高次元空間上の複素 Gaussian splat cloud とする。

\[
\Psi(r,y,t)=\sum_{j=1}^{K} c_j(t)\,g_j(r,y,t)\,\chi_j
\]

ここで、

| 記号 | 意味 |
|---|---|
| \(K\) | splat数 |
| \(c_j(t)\) | 複素重み |
| \(g_j\) | Gaussian primitive |
| \(\chi_j\) | 内部状態 |
| \(\Psi\) | 全体の量子状態 |

---

### 2.4 1個の Gaussian primitive

\[
g_j(z,t)=N_j
\exp\left[
-\frac12(z-q_j)^TA_j(z-q_j)
+\frac{i}{\hbar}p_j^T(z-q_j)
+i\phi_j
\right]
\]

\[
A_j=\Gamma_j+iK_j
\]

\[
\Gamma_j=\mathrm{Re}(A_j)\succ0
\]

\(\Gamma_j\) は広がり・楕円体形状を決め、\(K_j\) は位相曲率を決める。

1個の primitive は以下を持つ。

\[
\boxed{(q_j,p_j,A_j,c_j,\phi_j,\chi_j)}
\]

---

### 2.5 観測：高次元 splat の3D周辺化

観測者が見るのは \(r\) だけであり、\(y\) は見えない。したがって観測可能な分布は、隠れ次元を積分消去して得られる。

\[
P_{\mathrm{vis}}(r,t)=\int_{K_6}dy\,\Psi^\dagger(r,y,t)\Psi(r,y,t)
\]

これは「高次元 splat cloud の3D投影」または「周辺化」と見なせる。

ただし、量子では密度を先に足すのではない。先に複素振幅を足し、その絶対値二乗を取る。

\[
\Psi=\sum_j c_jg_j
\]

\[
P=|\Psi|^2
\]

したがって、

\[
|\Psi|^2=
\sum_j |c_jg_j|^2+
\sum_{i\neq j}c_i^*c_jg_i^*g_j
\]

第2項が干渉項である。

---

### 2.6 時間発展

最小限、標準的な量子時間発展を仮定する。

\[
i\hbar\partial_t\Psi=\hat H\Psi
\]

\(\hat H\) は物理エンジンであり、ポテンシャル、相互作用、内部自由度、隠れ次元構造を含む。

固定基底で係数だけを時間発展させるなら、重なり行列 \(S\) を用いて

\[
i\hbar S\dot c=Hc
\]

となる。

\[
S_{ij}=\langle g_i\chi_i|g_j\chi_j\rangle
\]

\[
H_{ij}=\langle g_i\chi_i|\hat H|g_j\chi_j\rangle
\]

動く splat として扱うなら、変分原理で

\[
\delta\int dt\,\langle\Psi|i\hbar\partial_t-\hat H|\Psi\rangle=0
\]

から \(q_j,p_j,A_j,c_j,\phi_j\) の更新式を得る。

---

## 3. なぜ Gaussian なのか

### 3.1 観測上の素朴主義

出発点は次である。

> 世界は、有限分解能の観測では局所的な blob / splat の点群として見える。

人間の視覚、センサー、画像再構成、物体認識はいずれも、連続世界を有限解像度の局所構造として扱う。そこから「Gaussian splat を primitive とする」発想が出る。

これは、世界の実体が Gaussian であると断定するものではなく、観測可能世界の記述形式を Gaussian から始めるという主義である。

---

### 3.2 最大エントロピー性

平均と共分散だけが与えられたとき、最も余計な仮定を加えない連続分布は Gaussian である。

したがって、観測で得られる情報が中心・広がり・向き・強度程度なら、Gaussian は自然な最小 primitive になる。

---

### 3.3 最小不確定波束

量子論では位置と運動量を同時に鋭くできない。

\[
\Delta x\,\Delta p\geq\frac{\hbar}{2}
\]

この下限をきれいに満たす代表的な波束が Gaussian である。

したがって、Gaussian splat は単なる視覚的 blob ではなく、量子的な最小不確定 primitive としても意味を持つ。

---

### 3.4 射影・周辺化に対する安定性

高次元 Gaussian は、低次元に射影・周辺化しても Gaussian になる。

したがって、

> 高次元に本体があるが、観測者には3D blobとして見える

という構造と相性がよい。

---

### 3.5 時間発展で扱いやすい

自由粒子や調和振動子では、Gaussian wavepacket は Gaussian のまま発展する。  
一般ポテンシャルでは変形や分裂が起こるが、多数の Gaussian primitive の重ね合わせで近似できる。

---

## 4. プランク長コンパクト化の役割

### 4.1 仮定

隠れ次元 \(K_6\) のサイズをプランク長程度に置く。

\[
\mathrm{size}(K_6)\sim\ell_P
\]

プランク長は

\[
\ell_P=\sqrt{\frac{\hbar G}{c^3}}
\]

で定義される。

### 4.2 低エネルギーで見えない理由

隠れ次元が半径 \(R\) の円にコンパクト化されていると、波動関数は

\[
\Psi(r,y,t)=\sum_{m\in\mathbb{Z}^6}\psi_m(r,t)e^{im_a y^a/R_a}
\]

のように展開できる。

非ゼロモードのエネルギーは概略的に

\[
E_m\sim\frac{\hbar c |m|}{R}
\]

である。

\[
R\sim\ell_P
\]

なら、

\[
E_m\sim\frac{\hbar c}{\ell_P}
\]

となり、プランクエネルギー級になる。低エネルギーでは \(m\neq0\) のモードを励起できず、ゼロモードだけが残る。

\[
\Psi(r,y,t)\approx\psi_0(r,t)\eta_0(y)
\]

その結果、

\[
P_{\mathrm{vis}}(r,t)
=\int dy\,|\psi_0(r,t)
\eta_0(y)|^2
\approx |\psi_0(r,t)|^2
\]

となり、通常の3D量子分布に見える。

---

## 5. 重要な注意点

### 5.1 「余剰次元は必ずプランク長」ではない

このモデルでは、見えている現実にそぐうように \(R\sim\ell_P\) と仮定する。  
しかしこれは観測で確定した値ではない。大きな余剰次元モデルのように、\(R\) がプランク長よりはるかに大きい可能性を扱う理論もある。

したがって、PCGSにおける \(R\sim\ell_P\) は、

> 見えない次元を確実に低エネルギー世界から隠すための仮定

である。

---

### 5.2 隠れ次元を自由通路にしない

隠れ次元方向に Gaussian で強く局在すると、

\[
\Delta y\sim\ell_P
\]

となり、不確定性原理により

\[
\Delta p_y\sim\frac{\hbar}{\ell_P}
\]

のプランク運動量が発生する。

したがって、通常の低エネルギー粒子を説明するなら、隠れ次元方向は次のどちらかが自然である。

1. 隠れ次元ではゼロモードとして広がっている。
2. 標準模型粒子がブレーン近傍に束縛されている。

量子トンネルや干渉は、隠れ次元を使った迂回として説明する必要はない。

---

### 5.3 splat分解は一意ではない

同じ \(\Psi\) は、異なる splat cloud で表せる可能性がある。

\[
\sum_j c_jg_j = \sum_k c'_kg'_k
\]

したがって、物理的実在を splat のリストそのものに置くと非一意性問題が出る。

安全な立場は、

\[
\{c_j,g_j\}\sim\{c'_k,g'_k\}
\quad\text{if}\quad
\sum_j c_jg_j=\sum_k c'_kg'_k
\]

と同一視することである。

つまり、実在するのは splat のリストではなく、それが表す状態 \(\Psi\) である。

---

### 5.4 多粒子系では配置空間に移る

1粒子なら \(z\in\mathbb{R}^D\) 上の splat cloud でよい。  
しかし \(N\) 粒子なら、状態は

\[
\Psi(z_1,z_2,\dots,z_N)
\]

であり、splat が乗る空間は

\[
D N
\]

次元の配置空間になる。

もつれは、複数粒子の座標を結合する高次元 Gaussian の共分散構造として表せる。

---

### 5.5 フェルミオンには反対称性が必要

同種フェルミオンでは、粒子交換で波動関数が符号反転しなければならない。

\[
\Psi(\dots,z_a,\dots,z_b,\dots)
=
-\Psi(\dots,z_b,\dots,z_a,\dots)
\]

したがって、電子やクォークを扱うには、Gaussian primitive に反対称化を組み込む必要がある。

---

## 6. このモデルが説明しようとすること

PCGSが狙う説明は以下。

### 6.1 見える世界が blob / object / field の集合に見える理由

高次元の複素 Gaussian splat cloud を3Dに周辺化し、有限分解能で観測するため。

### 6.2 隠れ次元が見えない理由

隠れ次元がプランク長スケールにコンパクト化され、非ゼロKaluza-Kleinモードの励起エネルギーがプランク級になるため。

### 6.3 量子的な干渉が起こる理由

Gaussian primitive は密度ではなく複素振幅として足されるため。

\[
P=\left|\sum_j c_jg_j\right|^2
\]

### 6.4 古典世界が現れる理由

多数の splat が局所化し、位相干渉が粗視化・デコヒーレンスされると、中心 \(q_j\) の運動が古典粒子的に見えるため。

---

## 7. このモデルがまだ説明していないこと

以下は未解決、または追加理論が必要な点である。

1. なぜ標準模型のゲージ群が \(SU(3)\times SU(2)\times U(1)\) なのか。
2. 電子、クォーク、ニュートリノなどの質量・混合角がなぜその値なのか。
3. 測定でなぜ1つの結果だけが現れるのか。
4. Born rule を仮定ではなく導出できるか。
5. 重力、特に動的な時空計量 \(g_{\mu\nu}\) をどう入れるか。
6. splat 数 \(K\) は保存されるのか、生成消滅するのか。
7. Gaussian 分解の正規形をどう決めるか。
8. Lorentz 対称性と因果律をどう厳密に保つか。
9. 隠れ次元の形 \(K_6\) を何にするか。
10. なぜ \(R\sim\ell_P\) なのかを仮定以上に説明できるか。

---

## 8. 他者向けの短い説明

### 8.1 一文版

> PCGSは、世界状態を高次元空間上の複素 Gaussian splat cloud として表し、観測可能な3D世界をその周辺化として得る、という量子状態の表現モデルである。

### 8.2 少し長い版

> 観測可能な世界は有限解像度では blob / splat の集合として現れる。PCGSでは、この見え方を出発点にし、量子状態を複素 anisotropic Gaussian primitive の重ね合わせとして表す。隠れ次元はプランク長程度にコンパクト化され、低エネルギーではゼロモードしか見えない。観測は高次元状態から隠れ次元を積分消去し、測定基底に射影する操作として扱われる。

### 8.3 注意書き付き版

> これは標準模型や量子重力を完成させる理論ではなく、量子状態・余剰次元・観測世界を Gaussian splat 的に再記述するための概念フレームである。物理理論として成立させるには、時間発展、相互作用、測定、ゲージ対称性、フェルミオン、重力を追加定義する必要がある。

---

## 9. 用語対応表

| 用語 | このノートでの意味 |
|---|---|
| Gaussian splat | 中心・広がり・向き・重みを持つ局所 primitive |
| complex Gaussian splat | 複素振幅・位相・運動量を持つ量子版 splat |
| splat cloud | 多数の Gaussian primitive の点群的集合 |
| 可視空間 \(r\) | 観測可能な3次元空間 |
| 隠れ次元 \(y\) | 観測されないコンパクト次元 |
| \(K_6\) | 6次元の隠れ空間 |
| \(\ell_P\) | プランク長 |
| ゼロモード | 隠れ次元方向に非ゼロ運動量を持たない低エネルギーモード |
| KKモード | 隠れ次元方向の運動量を持つ高エネルギーモード |
| Born rule | \(P=|\Psi|^2\) または \(P(a)=\langle\Psi|E_a|\Psi\rangle\) |
| renderer | 量子状態から観測確率を出す規則 |
| camera | 測定基底、観測装置の設定 |
| feature channel | スピン、偏光、電荷、色荷など |

---

## 10. 最小公理案

PCGSを理論骨格として書くなら、次のように置ける。

### 公理1: 高次元状態空間

\[
M=\mathbb{R}^3\times K_6
\]

\[
\mathrm{size}(K_6)\sim\ell_P
\]

### 公理2: 状態は複素 Gaussian splat cloud

\[
\Psi(r,y,t)=\sum_{j=1}^{K} c_j(t)g_j(r,y,t)\chi_j
\]

### 公理3: primitive は complex anisotropic Gaussian

\[
g_j(z,t)=N_j
\exp\left[
-\frac12(z-q_j)^T A_j(z-q_j)
+\frac{i}{\hbar}p_j^T(z-q_j)
+i\phi_j
\right]
\]

\[
\mathrm{Re}(A_j)\succ0
\]

### 公理4: 時間発展はユニタリ

\[
i\hbar\partial_t\Psi=\hat H\Psi
\]

### 公理5: 観測は隠れ次元の周辺化と測定射影

\[
P_{\mathrm{vis}}(r,t)=\int_{K_6}dy\,\Psi^\dagger(r,y,t)\Psi(r,y,t)
\]

一般測定では、

\[
P(a)=\langle\Psi|E_a|\Psi\rangle
\]

### 公理6: 低エネルギーではゼロモードのみ

\[
E\ll \frac{\hbar c}{\ell_P}
\quad\Rightarrow\quad
\Psi(r,y,t)\approx\psi_0(r,t)\eta_0(y)
\]

---

## 11. 参考情報

- NIST CODATA, Planck length: \(\ell_P\approx 1.616255\times10^{-35}\,\mathrm{m}\).  
  <https://physics.nist.gov/cgi-bin/cuu/Value?plkl=>
- Particle Data Group, reviews/listings on extra dimensions and Kaluza-Klein excitations.  
  <https://pdg.lbl.gov/>
- Kaluza-Klein compactification: compact dimensions produce discrete momentum modes, often interpreted as towers of heavier modes in the lower-dimensional effective theory.
- Gaussian wavepackets and coherent states: standard constructions in quantum mechanics and quantum optics; Gaussian states are central examples of minimum-uncertainty states.

---

## 12. 最終整理

この会話で到達した位置は以下である。

> **世界そのものが Gaussian splat である**と断定するのではなく、  
> **観測世界が Gaussian splat 的に現れる**という素朴主義から出発し、  
> **高次元の複素量子状態を Gaussian splat cloud として表現する**。

隠れ次元は、見えている現実にそぐうようにプランク長スケールにコンパクト化する。

\[
\mathrm{size}(K_6)\sim\ell_P
\]

観測可能な世界は、

\[
\boxed{
\text{高次元 complex Gaussian splat cloud}
\rightarrow
\text{隠れ次元の周辺化}
\rightarrow
\text{3D観測分布}
}
\]

として得られる。

このモデルは、完成した物理理論ではなく、**見える現実・量子振幅・余剰次元を統一的な表現形式に乗せるための仮説的な記述フレーム**である。
