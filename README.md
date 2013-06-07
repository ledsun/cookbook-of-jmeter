# JMeter クックブック

## はじめに

### 本文書の目的

本文章は未経験者が Apache JMeter の使い方がわかることを目的としています。本書のゴールは以下の通りです。

- JMeterの使い方を理解する
- JMeterの用語を覚える

対象とするJMeterはバージョン2.9以上です。

次の項目は本書の対象外です。

- 負荷試験の設計方法
- Javaの環境設定方法
- 試験のリモート実行
- 次のリクエストを扱う試験。FTP、LDAP、JMS、JUnit。

### JMeterとは
（主に）HTTPリクエストを送信する負荷試験ツールです。以下の点が好まれています。

+ Javaで作られているためWindows、Linux、Mac、いずれのOSでも動く
+ リクエスト生成機能がプラグインになっていて、対応しているリクエストが豊富
（JDBC、FTP、JMS、LDAP、SOAP)

### 参考情報
[JMeter | TECHSCORE(テックスコア)](http://www.techscore.com/tech/Java/ApacheJakarta/JMeter/index/)がJMeterについて日本語でまとまっていて参考になります。


## 目次

1. [起動する](1.start.md "起動する")
1. [テストを実行する](2.run.md "テストを実行する")
1. [多すぎる機能（サンプラー）を減らす](3.shrink.md "多すぎる機能（サンプラー）を減らす")
1. [見た目を見慣れたものにする](4.view.md "見た目を見慣れたものにする")
1. [変数を定義する](5.variable.md "変数を定義する")
1. [一定間隔でテストを実行する](6.beat.md "一定間隔でテストを実行する")
1. [付録1:用語集](Appendix-1.term.md "付録1:用語集")
1. [付録2:よくある質問と回答](Appendix-2.faq.md "付録2:よくある質問と回答")

## ライセンス
<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/deed.ja"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/3.0/88x31.png" /></a>

この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/deed.ja">クリエイティブ・コモンズ 表示 - 継承 3.0 非移植 ライセンスの下に提供されています。</a>
