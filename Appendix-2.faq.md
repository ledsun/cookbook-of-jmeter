# よくある質問と回答

## ログに関する質問
### Q.-LオプションでログレベルをWARNに設定してもINFOログが出力されます。
起動オプション-LでログレベルをWARNに設定してもINFOログが出力されます。

```
jmeter -LWARN
```

以下の順序で、指定したログレベル以上のログしか出ないのではないですか？

```
DEBUG　＜　INFO　＜　WARN　＜　ERROR　＜　FATAL
```

INFOログの出力を抑制するにはどうしたらいいでしょうか？

#### A.ログレベルを上げるにはjmeter.propertiesを変更してください。
-Lオプションではログレベルを下げることしかできません。
binディレクトリにあるjmeter.propertiesのlog_level.jmeterをWARNに設定してください。

```
log_level.jmeter=WARN
```

ログレベルをDEBUGに下げる場合は-Lオプションが有効です。

```
jmeter -LDEBUG
```

### Q.jmeter.log以外に独自のログを出す方法はありませんか？
テスト実行時に独自のログを出力して残したいです。
log関数でjmeter.logに出力すると他のログと混じってしまいます。
ログファイルを分けることは出来ないでしょうか？

#### A.this.interpreter.setOut関数でprint関数の出力先を変更してください。
print関数の出力先を変える方法が簡単です。

```
f = new FileOutputStream("my_log.txt", true);
p = new PrintStream(f, true, &quot;UTF-8&quot;);
this.interpreter.setOut(p);
```
以上のBeanShellコードでprint関数の出力先を、標準出力から「my_log.txt」に変更することができます。

## リスナーに関する質問

### Q. Throughputの計算式を教えてください。

「統計レポート」リスナーに表示される、"Throughput"(スループット)の数値はどのように算出されていますか？

#### A. Samples を テスト所要時間  で割ったものです。

計算式は以下の通りです

```
スループット　　＝　サンプル数　÷　( MAX(リクエスト開始時間　＋　Elapsed Time) - MIN(リクエスト開始時間) )
```

このためRamp-Up 期間やタイマーによる待ち時間の影響を受けます。
スループットの値では、アプリケーションの性能を表すことが出来ないので注意して下さい。

アプリケーションの性能を評価するには、次の手順を踏む必要があります。

1. シナリオを作成する
1. 負荷を変更しながらスループットを取得する
1. 負荷を上げてもスループットが上昇しなくなる負荷を探す
1. その時に処理したリクエスト数でアプリケーションの性能を評価する

## Processorに関する質問

### Q. Post-Processorsでアサーション結果が参照できません。

BeanShell PostProcessorで次のコードを実行してもアサーション結果が0件しか取得できません。
```
assertionResults = prev.getAssertionResults();
print(assertionResults.length);
```

#### A. アサーション結果の確認はアサーションで行ってください。
PostProcessorはアサーションより先に実行されるため、アサーション結果を取得できません。

コンポーネントは次の順序で実行されます。

1. 設定エレメント
1. PreProcessor
1. タイマー
1. サンプラー
1. PostProcessor
1. アサーション
1. リスナー

アサーション結果を確認するためのアサーションを追加してください。

