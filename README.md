# PCGS / Complex Gaussian Splat Cloud — Codex Handoff

このリポジトリ/作業パッケージは、会話で構築した **「3D Gaussian Splatting の語彙で量子・観測・隠れ自由度を読む翻訳フレーム」** を、Codex に移送して実装・整理してもらうためのものです。

重要: これは「新しい物理法則の主張」ではなく、既存の量子論・観測・余剰次元/内部自由度を、3DGS の母語に **位相=矢印** を足して読み替える表現モデルです。

## 現在の中心命題

> 3DGS は観測後・デコヒーレンス後の古典世界を描く母語として強い。そこに「位相=矢印」を足すと、干渉・重ね合わせ・event sampling・隠れ自由度を一貫した可視化語彙で説明できる。

## コア対応表

| 3DGS 語彙 | 量子/観測側の読み替え |
|---|---|
| Gaussian splat | Gaussian wavepacket / coherent-state primitive |
| anisotropic covariance | 広がり・向き・不確定性楕円体 |
| opacity / density | 確率密度に近いが、そのままでは不足 |
| phase arrow | 複素位相 |
| splat 合成 | 複素振幅の重ね合わせ |
| rendered density image | 確率場 \(P=|\Psi|^2\) |
| stochastic sample | 一回の観測 event |
| accumulation | 多数回観測で分布が安定化 |
| hidden projection | 隠れ自由度の周辺化 / trace out |
| classical render | デコヒーレンス後の古典的見え |

## 正準式

状態:

```math
\Psi(x,t)=\sum_j c_j(t)g_j(x,t)\chi_j
```

単一 complex Gaussian splat:

```math
g_j(x,t)=N_j\exp\left[-\frac12(x-q_j)^TA_j(x-q_j)+\frac{i}{\hbar}p_j^T(x-q_j)+i\phi_j\right]
```

観測確率場:

```math
P(x,t)=|\Psi(x,t)|^2
```

一回の event render:

```math
x_{obs}\sim P(x,t)
```

隠れ自由度の周辺化:

```math
P_{vis}(r,t)=\sum_{\alpha,s}\int dy\,|\Psi(r,y,\alpha,s,t)|^2
```

密度行列で書く場合:

```math
\rho_{vis}=\mathrm{Tr}_{hidden/env}\,\rho
```

## 隠れ空間の分解

「隠れ空間」は単一のものではありません。以下を混ぜないこと。

| 種類 | 役割 | プランク長コンパクト化の対象か |
|---|---|---|
| physical hidden dimensions | 余剰空間方向 \(K_n\) | 基本的には yes |
| internal gauge fiber | 電荷・色荷・弱荷など | no |
| spin / local-frame fiber | スピン、局所フレーム、スピノル構造 | no |
| configuration / Hilbert space | 多粒子状態・もつれ・波動関数の置き場所 | no |
| renderer latent / cognitive space | 説明・可視化上の潜在変数 | no |

## 推奨プロジェクト化

最小実装は、静的 HTML/JS で以下を見せることです。

1. 2つの complex Gaussian splat の干渉
2. phase / momentum / width / separation の操作
3. density render \(P=|\Psi|^2\)
4. event sample \(x\sim P\)
5. accumulation による安定化
6. decoherence knob \(\lambda\) による干渉項の消失
7. optional: hidden coordinate \(y\) の周辺化

既存の `pcgs_toy_simulator.html` が最小プロトタイプです。

## ファイル構成

- `complex_gaussian_splat_note_v4_hidden_spaces.md` — 現時点の本体ノート。隠れ空間の分解まで反映。
- `pcgs_toy_simulator.html` — 1D toy simulator。phase/interference/event sampling/decoherence knob。
- `pcgs_compact_standalone_note.md` — 単体で読めるコンパクト版。
- `gaussian_splat_quantum_sampling_note.md` — sampling / accumulation / decoherence の独立ノート。
- `pcgs_concept_note.md` — 初期の話の経緯を含む広めの概念ノート。
- `CODEX_PROMPT.md` — Codex に貼る開始プロンプト。
- `TASKS.md` — Codex に投げる作業分解。
- `AGENTS.md` — Codex/agent 用の作業指針。

## 重要な制約

- 「物理的導出」と「翻訳フレーム」を混同しない。
- `hidden physical dimensions`, `internal gauge fiber`, `spin fiber`, `configuration/Hilbert space` を混ぜない。
- 3DGS renderer は一回の結果を直接産むものではなく、基本は density render。量子測定の event は後段の sampling として分ける。
- Born rule と一回性は、現時点では標準量子論から借りている外部ルールとして扱う。
- internal fiber の図解は比喩・翻訳であって、標準模型の導出ではない。

## ゴール

このパッケージの目的は、次のどちらかです。

1. **読み物化**: PCGS/Complex Gaussian Splat Cloud の説明サイトを作る。
2. **可視化プロトタイプ化**: 量子干渉・sampling・decoherence・hidden projection を動かせる toy simulator を作る。

