---
aliases: []
tags: []
publish: true
date: 2023-05-04T17:17:46+09:00
updated: 2025-06-29T12:46:47+09:00
---
# GenAI Utilization

[[fff-001 LLM-powered software, ChagGPT Integration]]

## 本質っぽいこと
- LLMモデルの性能（回答精度、スピード、in/outの制約、コストなど）の良し悪しがあれど、現時点では100点の精度を保証することはできない
	- 10個質問して正しく回答されていても、11個目の質問でトンチンカンな回答があり得る。そうなると、元々の10個はどうなの？　となって、結局人が介入する必要がある。今時点では、汎用的に、horizontalに、完全なるLLMベースの自動化は難しい
	- 結局、品質基準(e.g. 99.9999%)とのバトルが続く
	- プロンプトを書かせることになったら、まず精度・品質を保証することはできないだろう
- LLM利用にも自動運転で言うところの段階・レベルが存在する
	- 軸：
		- あるワークフローの中で活用するスコープ：　一部〜結合〜全体
		- vertical/horizontal: 特定ワークフローに限定〜任意のワークフロー
		- プロンプトの固定化 / 変動化
			- 変動： 
				- RAGのようにシステムで変動させる
				- 人に自由に書かせる
			- 固定：
				- 事前にプロンプトとモデルの組み合わせを評価をして固定化する
		- LLM活用対象の性質、結果に求められる精度
			- 絶対に誤ってはいけない〜ある程度誤りは許容される
			- ワークフローとして、結果に対する確認が必要かどうかを決定する
				- 人のレビュー
				- その他手段によるチェック
					- システム、ロジック、ルールベース
					- 別のプロンプトでチェックする
			- ただし、人がやれば精度が100%というわけではないことは重要
				- LLMで100%じゃなくても、人よりは正確だと評価できれば、そっちの方が良い
			- 自動運転Lv5は、100%精度が求められる？
		- モーダル: text, image, sound..
	- Lv1: 既存ワークフロータスクのドラフティング
		- プロンプトを書く
		- 人間がチェックする
	- Lv2: 
- 人間のやるべきこと
	- なぜ・なにをすべきか？を考えるweightが増す
		- LLMの登場で、Howのコストが下がっていく
		- コミュニケーションや人間の意思決定　の重要性が増す
			- そもそもなぜ何をしたいのかを、定義・明文化していく
			- [AI時代のITエンジニアの付加価値について \- NRIネットコムBlog](https://tech.nri-net.com/entry/value_of_it_engineers_in_the_age_of_ai)


## Utilization Patterns
- RAG
	- Agentic RAG
- ![[Pasted image 20250629124644.png]] 
- [https://substack\-post\-media\.s3\.amazonaws\.com/public/images/f784d500\-c708\-457c\-a152\-fee43058cf97\_2360x2770\.jpeg \(2360×2770\)](https://substackcdn.com/image/fetch/$s_!dP3e!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff784d500-c708-457c-a152-fee43058cf97_2360x2770.jpeg?utm_source=substack&utm_medium=email)