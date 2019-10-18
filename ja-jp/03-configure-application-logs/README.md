# 03 - アプリケーション・ログの設定

__このガイドは  [Azure Spring Cloud training](../README.md) トレーニング のコンテンツの一部です__

一般的な課題を理解するために、Spring Boot アプリケーションのログへのアクセス

---

## ログの集約に関する設定

アプリケーションのログにアクセスするには、下記の 3 種類があります。  

* [Azure Storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction/?WT.mc_id=azurespringcloud-github-yoterada)  
* [Azure Events Hub](https://docs.microsoft.com/en-us/azure/event-hubs/?WT.mc_id=azurespringcloud-github-yoterada)  
* [Log Analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/get-started-portal/?WT.mc_id=azurespringcloud-github-yoterada) 

ここでは、最も一般的であり、Azure Spring Cloud に統合されている　Log Analytics を利用します。

[Log Analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/get-started-portal/?WT.mc_id=azurespringcloud-github-yoterada) は Azure Monitor の一部で、Azure Spring Cloud にうまく統合されており、メトリックの監視にも役立ちます。

- [Azure Portal](https://portal.azure.com/?WT.mc_id=azurespringcloud-github-judubois) にアクセスしてください
- 検索ボックスより "Log Analytics workspaces" を検索してください
- Azure Spring Cloud が含まれるリソース・グループ内に新規ワーク・スペースを作成してください

![Create Log analytics workspace](media/01-create-logs-analytics-workspace.png)

- Log Analytics のワークスペースを作成したので、Azure Spring Cloud クラスターインスタンスからワークスペースにデータを送信するように構成します。
- Azure Spring Cloud クラスターの "Overview" ページに移動し、メニューで "Diagnostic Settings" を選択します
- Click on "Add diagnostic setting" and configure your cluster to send all its logs to the Log analytics workspace that we just created.
- 作成した Log Analytics のワークスペースに対してログを送信するため、"Add diagnostic setting" をクリックし設定してください。

![Send logs to the log analytics workspace](media/02-send-logs-to-log-analytics-workspace.png)

## アプリケーション・ログのクエリ

以上の設定で、ログをAzure Spring Cloud クラスターの "Logs" メニューから参照できるようになりました。

これは、事前に作成した Log Analytics のワークスペースのショートカットで、メニューからアクセスできます。

このワークスペースでは集約されたログからクエリを実行することができます。一番分かりやすい処理として、特定のアプリケーションからログの最終行を取得するなどが可能です。


__重要:__  Spring Boot のアプリケーションに対して専用の型 (`AppPlatformLogsforSpring`) が用意されています。

ここでは [前章](../02-build-a-simple-spring-boot-microservice/README.md) で実装した "simple-microservice" を利用し、アプリケーション・ログの最後から 50 行目までを取得する方法を記載しています。


```
AppPlatformLogsforSpring
| where AppName == "simple-microservice"
| limit 50
```

![Query logs](media/03-logs-query.png)

---

⬅️ 前章: [02 - かんたんな Spring Boot マイクロサービスの構築
](../02-build-a-simple-spring-boot-microservice/README.md)

➡️ 次章: [04 - Spring Cloud Config Server の設定](../04-configure-a-spring-cloud-config-server/README.md)
