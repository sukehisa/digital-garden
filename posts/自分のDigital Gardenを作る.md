---
aliases: []
tags: []
publish: true
date: 2023-05-01T14:11:05+09:00
updated: 2023-05-02T20:59:42+09:00
---

---
date: "2023-04-01"
updated: "2023-05-01"
draft: false
---

## Digital Gardenの構築
- 良いプラットフォームの候補たち
	- [10 Obsidian Publish Alternatives to Publish Your Notes Online for Free \| Medium](https://beingpax.medium.com/7-obsidian-publish-alternatives-to-publish-your-notes-online-for-free-33db4fb06f5)
- 要件
	- Netlifyでホストできること（SSGなFW）
- 結果
	- Zola
- 他にも良かった候補
	- [TuanManhCao/digital\-garden: Free Obisidian Publish alternative, for publishing your digital garden\.](https://github.com/TuanManhCao/digital-garden)
		- 最初にこれを試したが、ToCとか検索ができず、別のを探すことに
	- [theowenyoung/gatsby\-theme\-primer\-wiki: A Gatsby Theme for Wiki/Docs/Knowledge Base, which using Primer style as the UI theme, can work well with Foam or Obsibian or just markdown files\.](https://github.com/theowenyoung/gatsby-theme-primer-wiki)
	- 全文検索ができなさそうなので、却下した
- 日本のDigital Gardenな人と思われる人たち
	- [Home \- nNodes](https://notes.naney.org/Home)
	- [Home \- Minerva](https://minerva.mamansoft.net/Home)

## 構成
### コンテンツ側
- [sukehisa/digital\-garden](https://github.com/sukehisa/digital-garden)
	- ここにコンテンツを溜めていく。
	- Obsidianで書いていく場所

### Platform側
- [sukehisa/obsidian\-zola: A no\-brainer solution to turning your Obsidian PKM into a Zola site\.](https://github.com/sukehisa/obsidian-zola)
	- ZolaというSSGツールのプラットフォーム側
- Zola側にコンテンツを持っていくときにObsidian特有の仕様を吸収するために変換を行う
	- [zoni/obsidian\-export: Rust library and CLI to export an Obsidian vault to regular Markdown](https://github.com/zoni/obsidian-export)
	- 例えば
		- Note embedding  e.g. ```![[xxx]]```
	- Pre-built binariesをbin配下に置いている
