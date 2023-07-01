---
aliases: []
tags: []
publish: true
date: 2023-07-01T10:24:26+09:00
updated: 2023-07-01T10:25:17+09:00
---

# SI　テスト
## 良いテストケースの条件
* テスト要件とのトレースがとりやすい ⇒ テスト要件のカバレッジがわかる
* どこに何が書いてあるかわかりやすくする ⇒ テストケースの漏れや重複を起こしにくくする
* 適切な細かさで記載しやすくする ⇒ 誰がやっても同じテスト結果になる
* 修正しやすい ⇒ 追加・変更しやすいテスト仕様
* テスト実施結果(ログ)を残しやすい ⇒ 最新の情報に更新される頻度が早くなる
* テスト消化率のとりやすいしくみがある ⇒ テスト実施の進捗を把握できる

[NOTE]
出典：ソフトウェア・テスト PRESS Vol.1 

Test Management Tool
- <https://en.wikipedia.org/wiki/Test_management_tool#List_of_test_management_tools[Test> management tool - Wikipedia]

# ソフトウェアテスト　（一般論として）
## 良さそうな文献
* The Art of Software Testing
* ソフトウェアテスト293の鉄則
* システムテスト自動化 標準ガイド
* IEEE829


## 定義
テストとは
- ”実際どうなっているか”と”本来はどうあるべきか”を比較するプロセスのこと
- IEEE Standard Glossary of Software Engineering Terminologyによる定義
```
ある特定の条件下でシステムまたはコンポーネントを操作するプロセスであり、その結果を観察または記録して、システムまたはコンポーネントのある側面を評価すること
```
ここでいう”ある特定の条件”を具体化したものがテストケースである

- Systematic Software Testingによる定義
```
テストとは、テストされるソフトウェアの品質を測定して改善するために、テストウェアをエンジニアリングし、利用し、保守しながら、同時並行的に進めるライフサイクルプロセスである
```
テストには、実行だけでなく、計画・分析・テストケース設計の観点も必要である

=== ブラックボックステスト
==== 同値クラステスト
* 十分なテストカバレッジを保ちつつ、ケース数を削減する技法のこと
* 同値クラス：有るコードパスを通る値のグルーピング
** ある同値クラス内のテストケースで欠陥が検出された場合、同じ同値クラス内の他のテストケースでも同じく欠陥が発生する。(欠陥が発生しない場合は、すべてで発生しない)
* 方法

1. 同値クラスが何かを識別する
2. 各同値クラスにつき、テストケースを1つ作成する
3. (オプション)リソースに余裕があれば、同じ同値クラスに複数のテストケースを設定する。但し、適切に同値クラスが識別されていれば、1つ目のケースで発見できなかった欠陥を見つけることは無い。
テストケースは、アプローチによって有効値/無効値の入力をテストする

* 同値クラステストは、単体テスト、統合テスト、システムテスト、受け入れテストのそれぞれに同じ様に適用できる

* 無効な入力値に対してテストケースを作成する必要があるか？？
** 事前条件がtaken/untakenの時のテストに対する、事後条件のテスト有無によって、契約と防御的設計の2つに分けられる
** アプローチ1：契約による設計(事前条件がtakenの場合のみを想定)
*** 事前条件が満足された状況でのテストケースしか作成しないというアプローチ(e.g. ファイルが存在しなければ(事前条件)、file open(事後条件)のテストは行わない)
** アプローチ2：防御的設計
*** モジュールはどんな入力でも受け付けるように設計される
*** 正常な事前条件が満たされない場合に、モジュールはエラーコードを返したり例外を発生させる
* 複数入力での無効値のテストでは、1回のテストで1つの無効値をテストすること
** 1つの入力値が無効値で、別の項目のエラーを覆い隠すことがあるため。というか、科学的なアプローチとして、同時に変えて良い変数は1つだけ！
* 発生し得る入力値を要件定義・設計の段階で減らす事は、テスト削減につながる
** e.g. 入力値をラジオボタンにする
* 1つのテストケースで複数の入力項目をテストできるようにすると効率的である

==== 境界値テスト
* 境界にはたくさんの欠陥が潜んでいる
* 方法

1. 同値クラスを見つける
2. 同値クラスの境界を見つける
3. 各境界について、境界上の値、境界上のすぐ下、すぐ上の値を選んでテストケースを作る

* ある同値クラスに対する、境界値テストが、別の同値クラスのテストになることもあるが、その場合は不要(重複実施する必要は無い)

==== ディシジョンテーブルテスト
* デシジョンテーブル：システムが実装する、ビジネスルールを記録するためのもの。
** 入力の条件組合せと、紐づくアクションを定義する
* デシジョンテーブルは、テストケースを作成するための指針としても役立つ
* 各ルールに対して、少なくとも1つのテストケースを作成する必要がある。ルールの条件が2値の場合、各組み合わせに対して1つのテストケースを用意すれば十分。条件が値の範囲の場合は、境界値テストの考え方を統合する
* デシジョンテーブルの論理圧縮
** アクションがある条件に依存する場合、他の条件はDon't Careにできるため、テーブル論理を圧縮でき、開発は楽ができる
** しかし、テストにおいては、誤ったデシジョンテーブルの論理圧縮をしていないかをテストするために、圧縮をしないデシジョンテーブルをもとにしてテストケースを作るべきである

==== ペア構成テスト
* 複数の入力値と、各入力値のテストする値の数について、全パターンをテストしようとすると、テストケース数が爆発する
* 品質をできるだけ落とさずに、テストを圧縮したいというのがモチベーション
** 感覚的には、1〜20％のテストケースの作成・実行で、全欠陥の70〜85％を検出できるといった感じ
* 単体・統合・システム・受け入れテストそれぞれに適用可能
* シングルモード欠陥とダブルモード欠陥をすべてテスト可能なテストケースの最小セットを定義する
** ほとんどの欠陥はこの2つの欠陥タイプであると仮定できるため、実際に欠陥を高い確率で検出出来ている

* 直交表を使う方法と、アルゴリズムで組合せを生成する、2つの方法がある
** 直交表
*** どの任意の2列を選んでも、すべての値ペアの組合せが現れる表のこと
*** 対象のモジュールに合う直交表を探し、テストケースを割り付ける(ルールあり)
** 全ペアアルゴリズム(オールペア法、Allpairs)
*** アルゴリズムで生成。均衡である直交表と違うため、ケース数は直交表よりも減る
*** 状況によっては組合せに制約条件があり、特定の変数の組み合わせは選択できないことが有る(e.g. IEとMacOS)。その場合は、制約条件を定義すれば、ツールがそれを考慮してペアを選択するものも有る
**** rdExpert, AETG
** 直交表では、結果としてダブルモード欠陥よりも複雑な欠陥を一定量カバーしており、全ペアアルゴリズムよりもカバレッジは高くなる
** 当然、特定の非常に重要な組合せがあれば、自分の判断でテストケースを追加してもよい

===== ツール
* All Pairs test case Generation Tool
** <http://satisfice.com/tools.shtml[Test> Tools - James Bach - Satisfice, Inc.]


==== 状態遷移図テスト
* 状態遷移図の構成要素：状態、イベント、アクション
** 1つのエンティティについて、1つの状態遷移図
*** 複数の異なるエンティティを混在させないこと
** 対象のエンティティにおけるすべての可能性がある状態、イベント、遷移を表す
* 状態遷移図から状態遷移表を作れる
** ある行が持つ列は、現在の状態、イベント/アクション、次の状態 
* 状態遷移表からテストケースを作る
** 最も望ましいのは、すべてのパスが少なくとも1回は実行されるようなケースを作成すること
*** 状態遷移図がループを持っている場合は無限になってしまう・・・
** 他には、全ての遷移を少なくとも1回はテストするケースを作成するというアプローチ
*** 一般的にはこのレベルが推奨される
*** 状態遷移表がそのままテストケースになる


==== ドメイン分析テスト
* 同時に複数の変数をテストする方法
** すべての変数のために個別のテストケースを作成するには、あまりに多すぎて、時間が足りない
** 同値クラステストや境界値テストを一般化したもの
** 不等式条件や等値条件で、on/offポイントを検査するようにテストケースを設定する。対象外の変数は、条件を満たす代表値を使用する。

==== ユースケーステスト
* 個別のトランザクションを1つ1つテストすることで、システムの機能を最初から最後まで通しで実行するようなテストケース設計方法
* ユースケースはUMLなどで定義される
* システムテストと受け入れテストのテストケースを開発するための基盤として役立つ

=== ホワイトボックステスト
* 適用対象は単体・統合・システムテスト
* 対象ソフトウェアの内部パス・構造・実装に関する知識を拠り所にしたテスト戦略
* 本質は、コードのテストというよりもパスのテスト
** モジュール内のパスのテスト(単体)、サブシステム内のモジュール間、システム内のサブシステム間のパス、システム間のパスのテスト、というように拡張できる

==== 制御フローテスト
* モジュール内の実行パスを識別して、パスを網羅するようにテストケースを作成して実行する
* パスの数がとてつもなく大きくなる可能性あり
** e.g. 条件分岐1つにつき、2倍になっていく・・
** 要件を満たさずに誤って実装された場合、それは当然検知できない(誤った実装からテストを生成するため)
* モジュールを制御フローグラフで表現する
* カバレッジレベル
** ステートメントカバレッジ
*** 全てのステートメントが少なくとも1回実行される
** ディシジョンカバレッジ(ブランチカバレッジ)
*** 全ての条件判定に対してTrue, Falseを少なくとも1回ずつ
** コンデションカバレッジ
*** 全ての条件がTrue/Falseの判定結果に少なくとも1回ずつなるように
** 複合コンディションカバレッジ
** パスカバレッジ
*** 全てのパスを1回通るようにケースを生成する

* 構造化テスト/基礎パステスト
** サイクロマチック数：直列の組合せでモジュールを通過するすべての可能な、独立でループを含まないパス(基礎パス)を生成できる
** サイクロマチック数分のテストケースを生成する
** 制御フローグラフ上の全てのノード、リンクをカバーするため、ステートメントカバレッジとディシジョンカバレッジを満たす

==== データフローテスト
* データのライフサイクル(定義:d、使用:u、消滅:k)で、時系列にチェックする
** 定義・使用・消滅のパターンが正しいかを確認する
*** e.g. ku(消滅した後に使用)は、欠陥
* データフロータイアグラムで、モジュールの全ての変数に対して、定義・使用・消滅の状態を記述する


=== テストパラダイム
* テストのパラダイムは、スクリプトテストと探索的テストの2つ。(全く異なるパラダイム)
** 現場ではこの2つのミックスとなることが多い

=== テストに対するアプローチ
==== 非特定不具合モデル
* 欠陥の分類を使わない方法。要件及び仕様から全てのテストケースを作成する

==== 特定不具合モデル
* 欠陥の分類にもとづいてテストケースを作成する。以前に経験したことの有る欠陥に似た不具合を発見できるようにテストケースを作成。

=== 欠陥の分類
* ソフトウェアにおける欠陥の分類
** Beizerによる分類
** Kaner, Falk, Nguyenによる分類

==== スクリプトテスト
* テストを設計し、テストケースを文書化し、テストケースを実行する
* 再現性、客観性、監査性が求められる場合に利用する
* 再現性：誰が実行しても同じ方法で実行できる状態でテストが定義されていること
* 客観性：テストケースを作成した人に依存しなこと
* 監査性：要件・設計・コード→テストケースに対して、トレーサビリティが存在すること
* IEEE829「Standard for Software Test Documentation」

==== 探索的テスト
* 製品について学習し、テストを設計し、テストを実行する
* James Bach「テスト設計とテスト実行の同時並行的な学習行為」
* 次に実行すべきテストケースを事前に計画しきらずに、むしろ1つ前に実行したテストとその結果から、次のテストを設計していく
* 要件が曖昧・存在しない時、システムが不安定など、短い時間内にテストしてフィードバックをする場合に役立つ
* スクリプトテストがエラーを検出できなくなった場合に、補完するものとして役立つ

# Unit Testing
## Reading Unit Testing
単体テストの定義とはなんでしょうか？下記のような性質を持つものと定義されます。
- 単体（Unit）　となる少量のコードを検証すること
- 実行時間が短いこと
- 隔離された状態で実行されること

良い単体テスト　はどのような性質を持つでしょうか？
- １単位の振る舞い（a unit of behavior) が検証されていること
	- アプリケーションの振る舞いについてより高いレベルで描写するべきである（≠プロダクションコードが何をするのかを単に列挙する）

「単体テスト」自体はどのような性質を持つでしょうか？
- プロダクションコードの欠点を見つけ出すことが得意であること
	- 例えば、あなたのテストコードの準備（Arrange)フェーズがあまりにも大きい場合、それは何らかの設計問題がある可能性が高い　（複雑な依存関係が必要になる）


”単体”をテストするために、テスト対象の単体（SUT）と”依存”を区別する必要があります。この依存はどのように種類分けできるでしょうか？
まず、”依存”は必ず、下記２種類のどちらかに所属します
- 共有依存
	- 複数のテストケースで使われている依存
- プライベート依存

また、各依存の性質　として下記軸が存在します。
- 依存のmutability
	- 不変 or 可変　依存
- 依存の所在
	- プロセス内 or 外　依存
	- プロセス外の例: データベース、ファイルシステム、外部API

| 例                             | 依存の種類   | 依存のmutability | プロセス内外 |
| ------------------------------ | ------------ | ---------------- | ------------ |
| Singleton, staticフィールド    | 共有依存     | Immutable        | プロセス内   |
| Database                       | 共有依存     | Mutable          | プロセス外   |
| ※単体テストとしてはあまりない。ほとんどはMutable | 共有依存     | Immutable        | プロセス外   |
| ※実際のPRJではほぼ無いはず     | 共有依存     | Mutable          | プロセス内   |
|                                | プライベート | Immutable        | プロセス内   |
|                                | プライベート | Mutable          | プロセス外   |
| 読み取り専用API                | プライベート | Immutable        | プロセス外   |
|                                | プライベート | Mutable          | プロセス内   |

## 古典学派 vs ロンドン学派
違いを理解するための考え方の軸
- 単体テストはプロダクションコードをどのくらい把握してないといけないのか？
| ああ                          | 古典学派 | ロンドン学派                                                          |
| ----------------------------- | -------- | --------------------------------------------------------------------- |
| "単体"の定義→隔離の範囲の定義 | 1単位の"振る舞い"。テストケースそれぞれを隔離する。他のテストケースの実行に影響する共有依存のみをテストダブルに置き換える         | 1単位の"コード" ≒クラス。不変依存以外の依存をテストダブルに置き換える |
- 



## 実践
- TDD

# Integration Testing （統合テスト）
# E2E Testing