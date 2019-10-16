|English|
|:--:|
|[![English](./Flag-usa_32.png) ](../README.md)|


# Azure Spring Cloud トレーニング

ここに Azure Spring Cloud の完全なワークショプがあります。このワークショップには説明やデモも含まれています。

このドキュメントは [Julien Dubois](https://twitter.com/juliendubois) が作成していますが、[MIT license](LICENSE.txt) ライセンスに従ってどなたでもご利用いただけます。

## 本トレーニングの期待値

このドキュメントは正式ドキュメントではございませんが、よく考えられたトレーニングです。

かんたんなデモから、とても複雑な例まで、コーディングを迅速に行い、プラットフォームを容易に操作できることから、このハンズオン・トレーニングでは、広範囲にわたってコマンドラインが使用されます。

すべてのガイドを完了することで、Azure Spring Cloud が提供するすべての機能を、より深く理解できるでしょう。

## 前提条件

- Java 8 以上
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli/?WT.mc_id=azurespringcloud-github-yoterada)
- [GitHub アカウント](https://github.com)
- Azure アカウント [Get one for free](https://azure.microsoft.com/free/).
- Azure Spring Cloud サービスの有効化 - [申請はこちらから](http://aka.ms/spring-cloud).
  - 現在、このサービスはプレビュー版として提供されています。そのため申請はケースバイケースで承認されます。

## [01 - クラスタの作成](01-create-a-cluster/README.md)

クラスタ作成と、効率的に作業を行うためのコマンドラインによる設定の基本操作


## [02 - かんたんな Spring Boot マイクロサービスの構築](02-build-a-simple-spring-boot-microservice/README.md)


[https://start.spring.io/](https://start.spring.io/) を利用した、できる限りかんたんな Spring Boot マイクロサービスの構築


## [03 - アプリケーション・ログの設定](03-configure-application-logs/README.md)

共通の課題を理解するために、Spring Boot アプリケーションのログへのアクセス

## [04 - Spring Cloud Config Server の設定](04-configure-a-spring-cloud-config-server/README.md)

[Spring Cloud Config Server](https://cloud.spring.io/spring-cloud-config) は Azure Spring Cloud で完全に管理およびサポートされ、Spring Boot のマイクロサービスで利用されます。

## [05 - Spring Cloud の機能を利用した Spring Boot マイクロサービスの構築](05-build-a-spring-boot-microservice-using-spring-cloud-features/README.md)

Build a Spring Boot microservice that is cloud-enabled: it uses a Spring Cloud Service Registry and a [Spring Cloud Config Server](https://cloud.spring.io/spring-cloud-config) which are both managed and supported by Azure Spring Cloud.

## [06 - Cosmos DB を使用したリアクティブ Spring Boot マイクロサービスの構築](06-build-a-reactive-spring-boot-microservice-using-cosmosdb/README.md)

[Spring Reactive Stack](https://docs.spring.io/spring/docs/current/spring-framework-reference/web-reactive.html) を利用したリアクティブな Spring Boot マイクロサービスを構築し、最高のパフォーマンスを持つグローバルの分散データベースである [Cosmos DB database](https://docs.microsoft.com/en-us/azure/cosmos-db/?WT.mc_id=azurespringcloud-github-yoshio) に接続するためのバインド設定を実施

## [07 - MySQL を利用した Spring Boot マイクロサービスの構築](07-build-a-spring-boot-microservice-using-mysql/README.md)

[MySQL database managed by Azure](https://docs.microsoft.com/en-us/azure/mysql/?WT.mc_id=azurespringcloud-github-yoterada) に接続するため JPA で実装した、典型的な Spring Boot アプリケーションの構築

## [08 - Spring Cloud Gatewayの構築](08-build-a-spring-cloud-gateway/README.md)

適切な Spring Boot マイクロサービスへ HTTP リクエストをルーティングするために [Spring Cloud Gateway](https://spring.io/projects/spring-cloud-gateway) を構築

## [09 - すべてを統合した完全なマイクロサービス・スタックの構築](09-putting-it-all-together-a-complete-microservice-stack/README.md)

フロントエンドの GUI から、マイクロサービスの全スタックに対しアクセスします。 Azure Spring Cloud の分散トレースメカニズムを使用してサービスを監視し、ニーズに応じてサービスをスケールします。

## [10 - Blue/Green デプロイメント](10-blue-green-deployment/README.md)

Deploy new versions of applications in a staging environment, and switch between staging and production with Azure Spring Cloud.

ステージング環境に、新しいバージョンのアプリケーションのをデプロイし Azure Spring Cloud でステージングと本番環境を切り替えます。

## [11 - CI/CD の設定](11-configure-ci-cd/README.md)

Configure a Continuous Integration / Continuous Deployement platform using GitHub Actions, so our Spring Boot microservices are automatically deployed.

GitHub のアクションを使用して継続的インテグレーション/継続的デプロイのプラットフォームを構成し、Spring Boot のマイクロサービスを自動配備します。

---

## Legal Notices

Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.

Privacy information can be found at https://privacy.microsoft.com/en-us/

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
