---
aliases: []
tags: []
publish: true
date: 2023-03-12T11:11:23+09:00
updated: 2023-12-24T15:01:33+09:00
---

# 2023/12/24
## deduction, induction, abduction

- きっかけ
	- <https://x.com/asknbid/status/1738557398816530632?s=20>
- それぞれなんだっけ？
	- [Deduction, Induction, Abduction：演繹、帰納、仮説形成 \| りんだろぐ rindalog](https://rindalog.blogspot.com/2017/04/deduction-induction-abduction.html)
	- deduction (演繹法)
	- induction (帰納法)
	- abduction (仮説形成)
	- analogy (類推)　もある
- [ロジカルシンキング \- Wikipedia](https://ja.wikipedia.org/wiki/%E3%83%AD%E3%82%B8%E3%82%AB%E3%83%AB%E3%82%B7%E3%83%B3%E3%82%AD%E3%83%B3%E3%82%B0#cite_note-11)
	- 和製英語, 
	- > 「論理的思考力」とか「ロジカル・シンキング」といった言葉がよく聞かれるように、論理とは思考に関わる力だと思われがちである。だが、そこには誤解がある。(中略) 論理力は思考力そのものではない。思考は、けっきょくのところ最後は「閃き」(飛躍)に行き着く。(中略) 思考の本質はむしろ飛躍と自由にあり、そしてそれは論理の役目ではない。
	- > (中略) 論理力とは思考力のような新しいものを生み出す力ではなく、考えをきちんと伝える力であり、伝えられたものをきちんと受け取る力にほかならない。
	- " 三角ロジックとトゥールミンモデル"　という名前は初めて知った

# 2023/12/23
## JVM based language & serverless
- 起動を早くするためには、苦労が必要である。手段として、Graal VM Native imageやCRaCが挙げられる。
	- 読んだページ
		- [Scalaはもうだめなのか？…というかJVM言語がもうだめじゃん？｜sugitani](https://sizu.me/sugitani/posts/i2xm9z9u5xk3)
		- [Java × サーバーレスは SaaS バックエンドとして通用するのか ? ~スタートアップの実戦記録~ \- builders\.flash☆ \- 変化を求めるデベロッパーを応援するウェブマガジン \| AWS](https://aws.amazon.com/jp/builders-flash/202310/java-serverless-saas-backend/?awsf.filter-name=*all)
	- CRaC: Coordinated Restore at Checkpoint
		- - [CRaC/docs](https://github.com/CRaC/docs#crac)
	- 既存資産・体制・ナレッジを脇に置くと、そもそも、JVMベースの言語　を初めから使わない　方が　たしかに良さそう
		- golangなど
	- Graal VM compatibleなfwで最近出てきているのが　Quarkus

- JVM はクラウドネイティブ時代に合わない？serverless系でJVM baseのアプリが動くまでの流れは？起動に時間がかかる？
	- 
- java -jar のようにアプリを起動して終了したら JVM process　はexitし、loadされたclassやJITコンパイルの結果は再利用/キャッシュされない？
	- javaアプリのプロセスモデルは？


- CRaCはserverless以外の環境（EC2など）でも使える技術？

	- 参考
		- [CRaCによるJavaの高速化 \| 豆蔵デベロッパーサイト](https://developer.mamezou-tech.com/blogs/2022/12/02/jdk-crac/)
			- すごい詳しい
		- [Lambda SnapStartを完全に理解してみた \- FLINTERS Engineer's Blog](https://blog.flinters.co.jp/entry/2023/02/21/122311)
	- できるが、実行環境として商用サポートが有るものは無さそう
		- AWS Lambda Snap Startくらい
			- > AWSはLambdaで使われているJavaランタイム(Corretto11)に対し、AWSが独自にCRaCの成果をアドオンしてLambda SnapStartを実現しているものと思われます。ですので、このLambda SnapStartはCRaCをプロダクトレベルで使った初めての例になると思います。
			- [firecracker/docs/snapshotting/snapshot\-support\.md at main · firecracker\-microvm/firecracker](https://github.com/firecracker-microvm/firecracker/blob/main/docs/snapshotting/snapshot-support.md)
- Spring Bootは対応している？
	- v3.2以降でサポートしているらしい
		- [CRaC/docs](https://github.com/CRaC/docs?tab=readme-ov-file#spring-boot)

## should we leave JVM base application?
- [Why we moved from Kotlin & Spring Boot to Go](https://blog.astradot.com/why-we-moved-from-kotlin-spring-boot-to-go/)
	- 起動も早い、使用するメモリ量やレイテンシが改善
	- Java/Spring のアノテーションを使用した作りは、black boxになっていて、動きを追うことができなくなっている
	- gradleの複雑さから開放された
- [The era of the JVM is coming to an end](https://movingfulcrum.com/the-era-of-the-jvm-is-coming-to-an-end/?ref=blog.astradot.com)


## other
- [sun\.misc\.Unsafe の魔力 \- A Memorandum](https://blog1.mammb.com/entry/2015/06/26/005020)
	- 知らなかった

- [Java 21新機能まとめ \#Java \- Qiita](https://qiita.com/nowokay/items/174f75b9e48cc7a80838)
# 2023/12/17
- [競技Excel 〜Excelの腕自慢集まれ！〜](https://fukusen.org/excel-for-e-sports/)
	- こんな世界があるのか、ちょっと面白そう
- [ChatGPTはなぜ計算が苦手なのか](https://www.nii.ac.jp/event/upload/20230707-03_Minato.pdf)

# 2023/11/05
[Towards Modern Development of Cloud Applications](https://sigops.org/s/conferences/hotos/2023/papers/ghemawat.pdf)
- 実感としても納得感がある。modular monolith から、下回りでサポートするecosystemがでてくるんだろうなー
# 2023/10/07
- [社会公共サービス \| BIPROGY技報 \| BIPROGY株式会社](https://www.biprogy.com/tec_info/backnumber/157abs.html#thesis6)　IT人材需給ギャップから見るSIビジネスのあるべき姿

# 2023/10/05
[10 Abstract Class and Interface Interview Questions Answers in Java](https://javarevisited.blogspot.com/2013/04/10-abstract-class-and-interface-interview-question-java-answers.html)
[Javaインターフェースメモ\(Hishidama's Java Interface Memo\)](https://www.ne.jp/asahi/hishidama/home/tech/java/interface.html)
# 2023/09/10
- [open\-interpreter/interpreter at main · KillianLucas/open\-interpreter · GitHub](https://github.com/KillianLucas/open-interpreter/tree/main/interpreter)
	- おもしろい。仕組みが簡単
- [A Simple Framework for Architectural Decisions](https://www.infoq.com/articles/framework-architectural-decisions/?itm_source=infoq&itm_medium=popular_widget&itm_campaign=popular_content_list&itm_content=)
	- Technology Radar for your company/team, Technology Standards, ADR
# 2023/08/30
## [Introducing ChatGPT Enterprise](https://openai.com/blog/introducing-chatgpt-enterprise)
- `enterprise-grade security and privacy,`  と言った時、何を指しているか？
	- データのcontrolがあるということ
	- OpenAI社が、そのdeployに関連するデータを使って、trainingなどしないこと
	- encryption at rest(AES 256) and in transit(TLS1.2+)
	- SOC 2 compliant
- [ChatGPT API を基礎から理解する \- Qiita](https://qiita.com/PND/items/c9e9d449539a460515a4)
	- 良いまとめだった
- [Fine\-tuning \- OpenAI API](https://platform.openai.com/docs/guides/fine-tuning/use-a-fine-tuned-model)
	- 知識自体の個別化は、難しそう。
	- [LLMのファインチューニング で 何ができて 何ができないのか｜npaka](https://note.com/npaka/n/nec63c01f7ee8)
- [Chat with Open Large Language Models](https://chat.lmsys.org/)
	- いろんなLLMを試せる
- [ChatGPTを使う前に知っておくべき「何を学習しているか」（Wedge（ウェッジ）） \- Yahoo\!ニュース](https://news.yahoo.co.jp/articles/62240832ffa3b00d18a196a1ab7e2a0c74e8f47f?page=2)


embeddingsとは？
- [［速報］Google、PostgreSQLにAI対応を組み込んだ「AlloyDB AI」発表、オンプレミスでも他社クラウドでも利用可能に。Google Cloud Next '23 － Publickey](https://www.publickey1.jp/blog/23/googlepostgresqlaialloydb_aigoogle_cloud_next_23.html)

# 2023/08/27
- [文章生成AI利活用に関するガイドライン](https://www.digitalservice.metro.tokyo.lg.jp/ict/pdf/ai_guideline.pdf)
	- 東京都。いいね、どんどんみんな使おう
- LLM Software Architecture, Design Patternが出てきている件
	- [98\. LLMを活用したソフトウェアアーキテクチャと代表的なユースケース w/ ryohtaka \| fukabori\.fm](https://fukabori.fm/episode/98)
	- MS用語だと　Copilot Stack:  AI infra - Model - Orchestrator - Copilot Frontend
	- でも概念的にはこうなるなー。　e.g. gpt3.5 - langchain - Chat GPT
	- [Microsoft の Copilot stack とは何か](https://zenn.dev/microsoft/articles/8974330fb534ef)
	- そもそもチャットである必要はあるのか？　検索の下地にあるデータが結局重要。　その通りだな・・
- 
- 

- [\(1\) Xユーザーのmizchiさん: 「今日ずっと考えてたフロントエンドの main\(\) が 合成関数だという記事を書きました。 https://t\.co/DvYmyP4ZBD」 / X](https://twitter.com/mizchi/status/1662123939781570560?s=12&t=0silruUD6NuwMo3wAwXjQA)

# 2023/08/16
[サーブレットを「JavaでのWebアプリケーションの基礎」として最初に勉強させるのをやめてあげてほしい \- きしだのHatena](https://nowokay.hatenablog.com/entry/2023/07/15/213831)
- 確かに。
- むしろ、Spring Boot以外に、　Quarkus・MicronautというFWが出てきていることを初めて知った。
- あと、Jakarta EE 

[無駄な議論を減らすために使ってる言葉 \- Konifar's ZATSU](https://konifar-zatsu.hatenadiary.jp/entry/2016/06/29/193911)
- こういう状況になった時に、俯瞰して　抽象化してまとめられるの　尊敬する。
- その状況になっていることに気づいて、アクションとしてのvocabularyを持っておきたい。

[自分の勉強や開発をできなくなった \- Konifar's ZATSU](https://konifar-zatsu.hatenadiary.jp/entry/2021/08/16/155833)
- わかる。以前は当たり前にやってたことができなくなって、自分を責める。

[SpringBoot/Quarkus/Micronautの性能を検証してみた ～その1 起動編～ \- Taste of Tech Topics](https://acro-engineer.hatenablog.com/entry/2022/12/21/161101)
- nice.  Spring Frameworkのエコシステムとか他の依存なければ、良いのでは。　要watch
- [Native Image](https://www.graalvm.org/latest/reference-manual/native-image/)
	- DIはReflectionを使っているから起動に時間がかかる。 この２つはReflectionを使わないDIを実現しているから、native image化もできる

# 2023/07/15
## Andrew Ng CS229 revisit
- 2011年に大学生の頃, courseraで受けたな〜
	- [2011\_Stanford\_MachineLearning\_Statement\_Of\_Accomplishment\.pdf \- Google ドライブ](https://drive.google.com/file/d/1S7J9gn86OMaoGe53HnqiABuVFnkCpKJk/view?pli=1)
- [\(37\) Stanford CS229: Machine Learning Course, Lecture 1 \- Andrew Ng \(Autumn 2018\) \- YouTube](https://www.youtube.com/watch?v=jGwO_UgTS7I&ab_channel=StanfordOnline)
- MLの変化に応じて、毎年授業がupdateされている
	- 当時はOctave(MATLABみたいなもの)から、Pythonベースになったり
- 学生にチーム制(助け合いや共同プロジェクト）を推奨している
- Prerequisiteは毎週　サポートのセッションがoptionalである
- そもそも先生がGoogleやBaiduのAIチームの経験があるというすごさ
- 冒頭で、MLがすでに一部の人たちのものではなく、pervasiveであると言って、Stanfordの卒業生は、あらゆる分野で実際に適応できる　と当たり前のようにいっていて、　これはやる気出るよな〜

# 2023/07/02

インドについて調べたい
- [アーダール \- Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%A2%E3%83%BC%E3%83%80%E3%83%BC%E3%83%AB)
	- インドのマイナンバー。指紋や虹彩といった生体情報まで使える。

[国民識別番号 \- Wikipedia](https://ja.wikipedia.org/wiki/%E5%9B%BD%E6%B0%91%E8%AD%98%E5%88%A5%E7%95%AA%E5%8F%B7)を見ると、個人番号はそりゃ必要だよね



[\(9\) 第130回　金融業界の話に要注意！実は簡単な為替の話 \- YouTube](https://www.youtube.com/watch?v=qTyx_eSyuW0&ab_channel=%E9%AB%99%E6%A9%8B%E6%B4%8B%E4%B8%80%E3%83%81%E3%83%A3%E3%83%B3%E3%83%8D%E3%83%AB)
- 2国間の通貨の交換比率　≒　通貨の総量(マネタリーベース）の比率　に近くなってくる（国際金融　の理論）
- 金融政策: お金をたくさん刷るか、刷らないか
- 
# 2023/07/01
- [[Software Testing]]を "単体テストの考え方　使い方"を読みながらupdate
- 推薦されていたreference
	- [Entity vs Value Object: the ultimate list of differences · Enterprise Craftsmanship](https://enterprisecraftsmanship.com/posts/entity-vs-value-object-the-ultimate-list-of-differences/)
	- [Amazon \| Dependency Injection Principles, Practices, and Patterns \| Seemann, Mark, Deursen, Steven van \| Software Development](https://www.amazon.co.jp/-/en/Mark-Seemann/dp/161729473X)

# 2023/06/23
## Docker internal
- [The internals and the latest trends of container runtimes \(2023\) \| by Akihiro Suda \| nttlabs \| Jun, 2023 \| Medium](https://medium.com/nttlabs/the-internals-and-the-latest-trends-of-container-runtimes-2023-22aa111d7a93)を読みながら
- 

# 2023/06/21
- [グローバルインタプリタロック \- Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%B0%E3%83%AD%E3%83%BC%E3%83%90%E3%83%AB%E3%82%A4%E3%83%B3%E3%82%BF%E3%83%97%E3%83%AA%E3%82%BF%E3%83%AD%E3%83%83%E3%82%AF)
	- Pythonはこれを採用している。
	- interpreter holds global lock, only 1 thread can run at time. 
	- 本当に並列処理する場合は、インタプリタプロセス自体を複数にする必要あり
	- 並列処理にくせがあるというのはこういうことかな？
- pythonの None aware dereferencingは PEPな状態
	- [PEP 505 – None\-aware operators \| peps\.python\.org](https://peps.python.org/pep-0505/)
	- 
# 2023/05/05
- Baby AGI系について試す
	- [[fff-001 LLMs]]
- Auto GPT venturing
	- git cloneで無限ループしたけど、これができたら良いな・・
		- [\(238\) AutoGPT just OBLITERATED all Traders \- YouTube](https://www.youtube.com/watch?v=JWELpf_5JvU&t=1s&ab_channel=MoonDev)
	- [Auto\-GPTでCakePHP4の簡単なWebアプリケーションを作ってみた \- Qiita](https://qiita.com/daishiro_jp/items/18077e429ed9b2626f7c)

小さなタスクを具体的なゴールで支持する　範囲でのみ効果的だと思われる。

# 2023/05/01
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
	- 

# 2023/04/29
## VS codeで AI codingを試す
- まずは、Github Copilot
	- すごい
- Chat GPT
	- [VSCodeにChatGPTの拡張機能を入れてコードレビューやバグを発見してもらう \- Qiita](https://qiita.com/tak001/items/c3000b3ce9b6e72b2ae5)

- Azure OpenAI Serviceを調べる
	- [\[比較表\] Azure OpenAIと本家OpenAI APIの比較表](https://zenn.dev/microsoft/articles/e0419765f7079a)
	- ```お客様から提供されたトレーニングデータは、お客様のモデルのfine-tuning (微調整)にのみ使用される。```
	- Enterpriseではこれが使えそう・・

Chrome Extension with Chat GPT
- なんでも要約する拡張がすごい・・

# 2023/04/23
- [x] obsedian follow toc ✅ 2023-04-23
	- [Outliner: highlight location of cursor \- Feature requests \- Obsidian Forum](https://forum.obsidian.md/t/outliner-highlight-location-of-cursor/3916/8)
		- 違うか。カーソルの色の話だ・・
	- [guopenghui/obsidian\-quiet\-outline: Improving experience of outline in Obsidian](https://github.com/guopenghui/obsidian-quiet-outline)
		- 解決！
- [x] obsedian plugin どういう仕組？ ✅ 2023-04-23

- chat gptで多くのインプットを入れる場合のやり方
	- [openai/openai\-cookbook: Examples and guides for using the OpenAI API](https://github.com/openai/openai-cookbook)
	- 

- kindleの指定箇所をchat gptで調べる

- 強力なlight weightな同時編集ツール
	- obsedian を共有ファイルとして使いたい

# 2023/03/21
- [\(125\) 「全米最優秀女子高生」の母が語る”非認知能力”と教育について【TBSラジオ】 \- YouTube](https://www.youtube.com/watch?v=ZSgGQb5dOVM&t=1245s&ab_channel=TBS%E3%83%A9%E3%82%B8%E3%82%AA%E5%85%AC%E5%BC%8F)

- Social Emotion (非認知能力)
- 主体性が鍵
	- 人間は自分が自分をcontrolしたい
		- あれしろこれしろというと反発したい理由はこれ

# 2023/03/18
## Miyadai
- <https://youtube.com/watch?v=aIhf1T2ayQc&si=EnSIkaIECMiOmarE&t=880>
- トクヴィル主義
	- 民主主義の国家が健全である条件は、個人が自立していること（≒依存することによる思考停止に陥っていないこと）
- 自立した個人は、自立した共同体（国家に依存しない共同体）が育てる。自立した共同体が国家を支える
- 個人が腐っているのは、共同体が腐っているからではないか？
- 国家のなすべきことは健全な個人を作り出す自立した共同体を支えることだ　（第三の道の本質）
- 全集団（≒全個人）を支えるプラットフォームをパブリック、Commonsと呼ぶ
- エートス：かんたんには変えられない行為・態度、行為を支える構え
- アンソニー・ギデンズと第三の道


# 2023-03-12
## LinuxのGithubに対する不満点
- [uedder's blog – Linus Torvalds 氏の理想の git 運用と GitHub](https://blog.uedder.com/linus_torvalds_complains_about_github_merges.html)
- なるほど、commitがtrace可能であること、その目的背景がわかること。その通りだ。

## 学びの構造　読んでみたい
- [『学びの構造』を読んで、自分の学び方や、他人の学び方を見直そう \- Magnolia Tech](https://blog.magnolia.tech/entry/2023/03/04/180528)
> **「わかる」とは「わからないところがわかる」こと**だと定義し、そこから「わからない部分」に行き当たると「疑問がわき」、それが全体を統合する働きをする

## ChatGPTとSiriのインテグレーション
[旅人さんはTwitterを使っています: 「【iPhoneの音声AIチャット\(ChatGPT\)】の設定方法を、以下ツリーで公開します❗️ Siriより便利❗️\(以下の動画参照\) iPhoneに「しつもん」と話しかけると自動でAIが立ち上がって「どうした？」と音声で聞いてくるので、質問を話すと、それに音声で答えます。AIの回答はテキストでメモ帳に自動保存❗️ https://t\.co/oZrF82lMUT」 / Twitter](https://twitter.com/Tomoto1234567/status/1631148219336982534)



# 2023-02-26
[だれが何をやっても日本円は紙くずになってしまう…日銀総裁が｢東大の経済学者｣となった本当の理由 本命の候補者たちは､みんな逃げていった \| PRESIDENT Online（プレジデントオンライン）](https://president.jp/articles/-/66766)


- 黒田前日銀総裁は、市場にお金を大量に流し込んだ　≒市場まれな強烈な金融緩和
	- 手段
		- 国債の爆買
		- 株価の買い支え（アベノミクスの維持）
	- 結果
		- 日銀の財務は悪化
		- 量的緩和→物価上昇


# 2023-01-09
- [\(5\) 若新雄純リターンズ！迫り来る老いと死、ボクたちはどう向き合う？\(後編\)【COTEN RADIO 番外編 \#82】 \- YouTube](https://www.youtube.com/watch?v=7jd06n0Hk04&ab_channel=%E6%AD%B4%E5%8F%B2%E3%82%92%E9%9D%A2%E7%99%BD%E3%81%8F%E5%AD%A6%E3%81%B6%E3%82%B3%E3%83%86%E3%83%B3%E3%83%A9%E3%82%B8%E3%82%AA_COTENRADIO)
- ストック型社会　
	- 絶対ではない
	- ストックが積み上がってる最中は安定する
		- 頑張ればなんとなるという感覚を持てる
	- ストックが固定化されて時間が立つと、不安定・不安因子が高まってくる
- フロー型社会
	- 例えば
		- お金が無くなる
		- 会社で階層を登っていく　が無くなる
- 農耕社会になってからストック型になってきた　（which is 結構最近）
- これからの社会の変動っぷりは半端ない　と思う
	- コミュニケーション技術が新しくなると、変動の回転のスピードが早くなる
		- スマホ、活版印刷、・・・
		- スマホが出てからの社会変遷のスピードがすごい
	- そのスピードの中で、自分が100歳の時に向けて何をストックすべきかなんて当たらない
	- 何に向けるかのポートフォリオ
		- 趣味、体験
		- 遊び心
		- ☓　ストックしないともったいない
			- その瞬間が消費されてOKである
		- フローが、思い出としてストックされる
		- 自分の人生が良かったと保証してくれるものは、思い出だけである。思い出は否定されない
			- 瞬間瞬間はフローだが
			- 死ぬ前に思い出すのって思い出だけ
			- 自分にだけ意味があるストック
		- 自己認知に影響がある
			- e.g. 海外旅行に行こうと思って実際に行く人と、行かない人　は自己認知に違いがであるはず　（自己効力感？）
			- 思い出をストックしよう
			- 同じ思い出（同じ事実）でも、どう認識するかで捉え方が変わる
- 
- 自分が決めることと、社外で規定されること。後者に引っ張られる。　引っ張られちゃだめだ。　自分側でやったほうが良い。　　どうせ社会は変わる。
- 社会の実態は追いつかない。が、実態としてはインターネットのコミュニケーションの回転速度が早くなり、認識はすごいスピードで進む。　
	- 民主主義は遅い
	- 社会は　意識と感覚に対して絶対　Behindする
- 社会の規定　と　自分の基準　とのギャップを感じながら、どっちの基準を大事にするのか。　自分の基準を大事にすべき
- 個人レベルで、自由にやります　ということ
- ハックできるのは、社会では無く、自己・認識・感覚・心の中である
	- 「老い」というのは認識である
- 認識を自由に捉えて良いというのが希望である
- 自分の人生は自作自演もOK。自己満足で死ねれば良い
	- 社会的な評価、安心は必要条件ではない
	- 自己満足に向けた活動資金としてのストック　はある


# 2022-11-12
## 散歩しながら
- 網羅性　を担保できるものと、できないもの　はどう区別する？
	- セキュリティがOKかの保証に近い
- お仕事でのちょっとしたこだわり集
	- 一覧を書くときは列の定義をすること
	- 分からないことは蓄積して調べる癖をつける
		- 日々仕事しながら、新しい情報に触れたときに感じる、自分の中の感覚（違和感、疑問、好奇心）に気づく。
		- specificな話と、一般化できる話を区別する。後者について調べる。
		- 後者は、また同じことに遭遇する可能性が高い。他の人も困ってたりする
	- 具体と一般化の話　(Specialization)
		- TAのマインドの一つ
	- 処理フローを正しく書く。書きながら、頭の中で　システムを動かす癖
		- 処理を構成する要素
		- トリガー、処理・制御の流れ、データの流れ、登場人物たち（処理の機構）
	- 曖昧性を無くす
		- 正しく文章を書く　
		- システムは再現性のある機械です　（巨大なピタゴラスイッチ）
		- 曖昧性があると、システムは予期しない動きをします。
		- 人の設計に曖昧性があると・・・
		- 設計（ドキュメント）は曖昧性が混入し得る
		- 実装は曖昧性0
		- 具体例
- サンジュにぺろの　エンディングテーマ　を歌ってみたい


## Elon Musk: 
- Elon Musk
	- Blockchain twitter isn't possible, as the bandwidth and latency requirements cannot be supported by peer to peer network, unless those "peers" are absolutely gigantic, thus defeating the purpose of a decentralized network. 
		- こういうところに技術に対する深い理解を感じる
	- ![[Pasted image 20221112094236.png]]
	- [Letter in Support of Responsible Fintech Policy](https://concerned.tech/)
	- 扱うデータ　の特性を踏まえないといけないはず