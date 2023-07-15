---
aliases: []
tags: []
publish: true
date: 2023-03-12T11:11:23+09:00
updated: 2023-07-01T10:30:03+09:00
---

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