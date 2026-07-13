---
title: "第1週 業務日誌"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### 第1週の目標 (Week 1 Objectives):
* First Cloud AI Journey (FCAJ) プログラムのコーディネーターおよび同期メンバーとのネットワーク構築とワークフローの同期。
* セキュリティが確保された企業用AWS環境の初期化、AWSマネジメントコンソールインターフェースの習熟、およびAWS CLIエンドポイントの設定。
* 技術的なクラウドMLOps移行マッピングの準備として、AI Pulmonary Diagnostic Suite（AI肺診断スイート）プロジェクトの既存コードベースと事前学習済みモデル `pneumonia_model_finetuned.keras` の構造を分析。

### 今週実施したこと (Tasks Implemented):
| 曜日 | 業務内容 | 開始日 | 完了日 | 参照資料 |
| --- | --- | --- | --- | --- |
| 月 | - オンボーディングオリエンテーションに参加。AWS Viet Namにおけるインターンシップの規則とワークフローを確認 <br> - FCAJプログラム用のAWSクラウドインフラストラクチャのアカウント識別子を受領 | 2026/06/01 | 2026/06/01 | AWS社内トレーニング資料 |
| 火 | - 業界標準のAWSコアサービス（Compute、Storage、Networking、IAM）のドキュメントを学習<br> - プロジェクトの `pneumonia_model_finetuned.keras` ファイルに含まれる肺疾患認識用CNN深層学習モデルの構造を調査 | 2026/06/02 | 2026/06/02 | <https://cloudjourney.awsstudygroup.com/> |
| 水 | - AWSマネジメントコンソールのアカウントをアクティベート <br> - ルートアカウントに対する多要素認証（MFA）セキュリティポリシーの強制適用 <br> - 最小特権の原則（PoLP）に基づき、管理用のIdentity and Access Management（IAM）ユーザーユーザーを初期化 | 2026/06/03 | 2026/06/03 | AWS IAM Best Practices Guide |
| 木 | - ローカル開発環境の標準化：AWS CLI v2、Python MLOps SDK、Docker Engineのインストール <br> - `aws configure` コマンドを使用した暗号化認証情報の構成（Access Key、Secret Key、デフォルトリージョン `ap-southeast-1`） | 2026/06/04 | 2026/06/04 | <https://docs.aws.amazon.com/cli/> |
| 金 | - テスト用のCLIクエリコマンドを実行し、クラウドとのプログラム接続の整合性を検証 <br> - 将来的な技術文書作成のため、`fcj-workshop-template-main` アーキテクチャをローカルリポジトリにマッピング | 2026/06/05 | 2026/06/05 | 個人リポジトリ＆FCAJテンプレート |

### 成果・実績 (Results Achieved):
* **安全なクラウドインフラの構築:** プロジェクト専用のAWSクラウド環境の初期化に成功。セキュリティリスクを隔離するため、ルートアカウントへのMFA適用を完了。
* **IAM デンティティアクセスの管理:** ルートの資格情報を公開することなく、MLOpsエンジニアのロールに特化した独立した管理用IAMユーザーの権限を策定。
* **AWS CLI v2 の疎通確認:** ローカルワークステーションとシンガポールリージョン（`ap-southeast-1`）のAWS APIエンドポイント間の認証通信チャネルを確立。
* **ワークスペース環境の標準化:** `fcj-workshop-template-main` テンプレートを用いたドキュメントフレームワークの構成を完了。次週以降に予定されている、肺X線画像ディープラーニングモデルのAWS SageMakerへのパイプライン移行に向けた準備を整えた。
