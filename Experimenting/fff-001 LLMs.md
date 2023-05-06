---
aliases: []
tags: []
publish: true
date: 2023-05-04T17:18:16+09:00
updated: 2023-05-05T13:14:08+09:00
---

# LLM-powered software, ChagGPT Integration

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

## Integration with Obsidian 
[different\-ai/embedbase: Hook LLMs to your data](https://github.com/different-ai/embedbase)


# ChatGPTに多くの情報をinputする方法を知りたい
- Embedbaseのように batch add した上で、chat gptとのcontextを作っていくと思われる
	- [BenさんはTwitterを使っています: 「No more homework\. Some of our users are using Embedbase for their homework 😂 Here's how they do it: a\) They upload their courses to Embedbase b\) they then askt their question on our ChatGPT playground c\) Embedbase automatically fetches the right answer from their courses and… https://t\.co/SxCutrHyjv」 / Twitter](https://twitter.com/hotkartoffel1/status/1653359527159267328)
