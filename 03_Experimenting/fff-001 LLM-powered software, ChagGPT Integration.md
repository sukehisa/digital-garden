---
aliases: []
tags: []
publish: true
date: 2023-05-04T17:18:16+09:00
updated: 2025-03-29T11:47:53+09:00
---

# LLM-powered software, ChagGPT Integration

- [ClineとAIコーディングツールの現状 \- laiso](https://laiso.hatenablog.com/entry/2025/01/07/045009)
	- 良いまとめ
	- > その経験からの感想なんですが、精度に関しては既存のコードベースで日常的な業務プログラミングのタスクを実行するレベルには達していません。コンテキストに入る情報とその処理能力に限界を感じます。
		- enterpriseでは、適切・明確に開発の単位を区切ってcontext量を制限することが重要になるはず
- MCP：　LLM applicationを接続する
	- [Model Context Protocol · GitHub](https://github.com/modelcontextprotocol)
	- [\(759\) Building Agents with Model Context Protocol \- Full Workshop with Mahesh Murag of Anthropic \- YouTube](https://www.youtube.com/watch?v=kQmXtrmQ5Zg)
	- ![[Pasted image 20250329114744.png]]

- Local LLM 
	- API利用のコストと、responseまでの時間のunstabilityで　利用が拡大していくはず
## Usecase
- プログラミング系、Engineering
	- コード補完
	- Chat Assistance

	- Code generation
	- Coding Agent

- tools
	- [Copilot Edits](https://code.visualstudio.com/docs/copilot/copilot-edits)
		- chat assistance, (preview) agent
	- Cline : 
	- Cursor : 専用IDE (vscode fork)

- ObsidianとのIntegration
	- Copilotというプラグインが良かった

## Chat GPT 4 Interface
- Input
	- text, image (non GA)
- API Keyの発行 [こちらから](https://platform.openai.com/signup/)
- 
## 環境
- Azure OpenAI Serviceを調べる
	- [\[比較表\] Azure OpenAIと本家OpenAI APIの比較表](https://zenn.dev/microsoft/articles/e0419765f7079a)
	- ```お客様から提供されたトレーニングデータは、お客様のモデルのfine-tuning (微調整)にのみ使用される。```
	- Enterpriseではこれが使えそう・・
- hosted by OpenAI (GA)

## [[Baby AGI]], Chat GPT Orchastration
- Implementation
	- [hwchase17/langchain: ⚡ Building applications with LLMs through composability ⚡](https://github.com/hwchase17/langchain)
	- [Significant\-Gravitas/Auto\-GPT: An experimental open\-source attempt to make GPT\-4 fully autonomous\.](https://github.com/Significant-Gravitas/Auto-GPT)

おそらく、下記要素が重要になる。
- 情報のInput
	- LLMの外から Liveな情報を収集する →Pluginになる
		- e.g. Google Search, Voice with Whisper, Images…. 
	- 収集した情報を Storeする, 管理する
		- short/long term memory
	- 意思決定する with Chat GPT 4
		- Thoughts
		- Reasoning
		- Plan
		- Critisism
		- Next Action
	- Actionを実行する
		- (Optional) 人間の許可を介在させる
	- 実行結果をStore/管理する

## Data Store for AGI
- Embedbase
- 

## Integration with Obsidian 
[different\-ai/embedbase: Hook LLMs to your data](https://github.com/different-ai/embedbase)


# ChatGPTに多くの情報をinputする方法を知りたい
- Embedbaseのように batch add した上で、chat gptとのcontextを作っていくと思われる
	- [BenさんはTwitterを使っています: 「No more homework\. Some of our users are using Embedbase for their homework 😂 Here's how they do it: a\) They upload their courses to Embedbase b\) they then askt their question on our ChatGPT playground c\) Embedbase automatically fetches the right answer from their courses and… https://t\.co/SxCutrHyjv」 / Twitter](https://twitter.com/hotkartoffel1/status/1653359527159267328)


# GenAI + Engineering
[実例で紹介するRAG導入時の知見と精度向上の勘所 \- Speaker Deck](https://speakerdeck.com/yamahiro/shi-li-deshao-jie-sururagdao-ru-shi-nozhi-jian-tojing-du-xiang-shang-nokan-suo?slide=75)