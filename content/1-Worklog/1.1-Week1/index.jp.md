---
title: "Worklog 第1週"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### 第1週の目標:
* AWS Viet Namインターnシップにおけるテクニカルコーディネーターとの連携、およびFirst Cloud AI Journeyプログラムのロードマップ把握。
* プラットフォームへのアクセス権を有効化し、AWS Management ConsoleおよびAWS CLIを含む主要なAWSサービスとクラウド管理ツールの学習。

### 今週実施したこと:
| 曜日 | 業務内容 | 開始日 | 完了日 | 参照資料 |
| --- | --- | --- | --- | --- |
| 月 | - Workforce Bootcamp - FCAJのオリエンテーションセッションに出席。<br>- AWS Viet Namの社内セキュリティ規定および機密保持コンプライアンスポリシーの確認。 | 2026/06/01 | 2026/06/01 | AWS社内トレーニング資料 |
| 火 | - 主要なAWSクラウドインフラサービスの基本概要を学習:<br>&emsp; + Compute (EC2)<br>&emsp; + Storage (S3)<br>&emsp; + Networking (VPC)<br>&emsp; + Identity & Access Management (IAM) | 2026/06/02 | 2026/06/02 | <https://cloudjourney.awsstudygroup.com/> |
| 水 | - プログラムから提供されたAWSエンタープライズアカウントをアクティベート。<br>- AWS Management Consoleのインターフェースを確認し、ローカル環境にAWS CLI v2をインストール。 | 2026/06/03 | 2026/06/03 | <https://cloudjourney.awsstudygroup.com/> |
| 木 | - 仮想サーバーサービスであるAmazon EC2の基本概念を調査:<br>&emsp; + インスタンスタイプ、AMI (Amazon Machine Image) の分類。<br>&emsp; + Elastic Block Store (EBS) ボリューム容量およびElastic IPの役割。 | 2026/06/04 | 2026/06/04 | <https://cloudjourney.awsstudygroup.com/> |
| 金 | - **技術ハンズオンの実施:**<br>&emsp; + `aws configure` コマンドによるAccess KeyおよびSecret Keyのローカル認証設定。<br>&emsp; + テスト用EC2インスタンスの起動、EBSボリュームの追加マウント、およびSSHプロトコルによるリモート接続の確立。 | 2026/06/05 | 2026/06/05 | <https://cloudjourney.awsstudygroup.com/> |

### 成果・実績:
* 最小特権の原則に基づくAWSクラウド運用のベストプラクティスおよびアイデンティティセキュリティモデルを深く理解。
* 提供されたAWSエンタープライズ環境の初期化と、多要素認証（MFA）によるルートアカウントの保護設定を正常に完了。
* ローカル開発環境におけるAWS CLI v2の疎通確認を完了し、デフォルトリージョン `ap-southeast-1`（シンガポール）への接続を確立。
* CLIを用いた基本的なクエリコマンドを実行し、アカウント情報の確認、アクティブリージョンの一覧取得、およびEC2メトリクスの抽出に成功。
* 起動したEC2インスタンスへのSSH経由のリモート接続に成功し、EBSボリュームによる動的なストレージ拡張プロセスを習得。
