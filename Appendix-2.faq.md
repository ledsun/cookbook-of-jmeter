# よくある質問と回答

### Post-Processorsでアサーション結果が参照できません。

BeanShell PostProcessorで次のコードを実行してもアサーション結果が0件しか取得できません。
```
assertionResults = prev.getAssertionResults();
print(assertionResults.length);
```

#### アサーション結果の確認はアサーションで行ってください。
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
