# AWS CodeCommit

## なにそれ

完全マネージド型のソース管理サービス。
GitHubとかBitBucketのようなやつ。

### メリット

- AWSのアカウントでログイン・利用できる。
- プルリクエスト機能あり
- AWS CodePipelineでCD（継続的デプロイ）のソースとして使用できる。（GitHubでもできる）
　（プッシュしたら→ビルド→デプロイなど）
 
### デメリット
- 有料（5人まで無料、それ以降1人当たり1USD/Month）

## 兄弟

- CodeCommit
- CodeDeploy
- CodePipeline
- CodeStar

Code三兄弟を知る – シリーズ –
https://dev.classmethod.jp/series/code-trio/
