---
aliases: []
tags: []
publish: true
date: 2023-07-05T14:06:59+09:00
updated: 2023-12-17T18:13:24+09:00
---

# 開発への要求
- 開発生産性、ビジネスの変化に追従できる開発ができること
- 複数の開発チームが体制上存在する
- 新規参画者はすぐにキャッチアップできるようにしたい
	- アプリケーションの構造を理解し、何を修正すればよいか分かる
- アプリケーションのCI/CDを実践する
	- 常にアプリケーションが動く状態を維持すること
- 要求されるサービスレベル・処理量に応じて、アプリケーションにスケーラビリティとアベイラビリティを確保したい
- 新規技術を取り入れやすくすることで、システムの進化を妨げない

# Monolithic
- 状況、コンテキスト
	- 複数の開発チームが、同じソースコードレポジトリを育てる
- 欠点
	- 開発スピードが遅くなる
		- 新規参画者のキャッチアップは大変・・
			- 構造がわからない、何を修正すればよいかわからない
		- アプリ内のモジュール/コンポーネント　境界線が曖昧になり、修正の分担が不明確
			- 開発チームは自律的に動きづらくなる
				- チーム間の調整が絶えず必要
		- 開発ツール（IDEなど）の動きが、ソースコードのサイズ肥大に応じて遅くなる
		- デプロイの頻度が下がる
			- 一部分だけの修正でもアプリ全体のデプロイが必要なので、、
			- テスト：ある箇所を修正したときの影響範囲が自明ではない
				- アプリ全体のリグレッションテスト・・
			- デプロイするということは一部コンポーネントが動かなくなるリスクと隣り合わせである
				- 修正と全く関係ないコンポーネントが使用不可になる可能性が高まり、デプロイに対するモチベーションが下がる
			- デプロイスケジュールが出来上がってしまう
				- デプロイスケジュール≠ビジネス変更のスピード
			- UI部分は、頻繁に修正とデプロイをしたいため、critical…
	- アプリケーションのスケールが困難、コスト対効果が下がる
		- アプリケーションまるごと　スケールさせるのは簡単だが・・・データのスケールは本質的に難しい　（データの整合性問題）
			- アプリケーションが複数インスタンスで動いても、同一のデータソースにアクセスして、データがボトルネックになり得る
		- 実際のアプリケーションは、コンポーネント単位で必要なリソースの特性が異なる
			- CPU intensive, memory intensive..
			- Read Intensive, Write Intensive
			- アクセス頻度の高い一部コンポーネントのみスケールさせたくても、アプリ全体でスケールしなくてはならず、リソースの利用効率が下がる
	- 同一の技術スタックを使い続けざるを得ない
		- アプリケーションの一部だけ、新規技術を使うというのは困難
			- e.g. JVMベースのアプリだと、JVM以外の技術が入り込む余地はない
- 利点
	- ※前提：　複雑度・サイズが小さければ（small monolith)
	- 開発はシンプル
		- 1つのアプリケーションとしてIDEなどの開発ツールがフルサポート
		- デプロイが楽　（1アプリだけでプロイすればいい）
		- スケールアウトも楽　（1アプリだけインスタンスを増やせば良い）
# Microservice アーキテクチャ
- サービスは
	- 小規模な開発チームが独立して（理想的には、別のチームとの調整なしに）開発、デプロイが可能
	- サービス間が疎結合
- 利点
	- 複雑で、サイズが大きくなった、アプリケーション/システムに対応できる
		- Maintainable: 構成するサービスは比較的小さく、理解ができるため修正ができる。小さめのチームが自律的に動ける
			- Testable: テストもしやすい