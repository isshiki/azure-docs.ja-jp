# [概要](search-what-is-azure-search.md)
## [Azure Search とは](search-what-is-azure-search.md)

# 作業の開始

## [サービスを作成する](search-create-service-portal.md)
## [インデックスを作成する](search-what-is-an-index.md)
### [Azure Portal](search-create-index-portal.md)
### [.NET](search-create-index-dotnet.md)
### [REST](search-create-index-rest-api.md)
## [データの追加](search-what-is-data-import.md)
### [Azure Portal](search-import-data-portal.md)
### [.NET](search-import-data-dotnet.md)
### [REST](search-import-data-rest-api.md)
## [インデックスの検索](search-query-overview.md)
### [Azure Portal](search-explorer.md)
### [.NET](search-query-dotnet.md)
### [REST](search-query-rest-api.md)

# チュートリアル

## [.NET での開発](search-howto-dotnet-sdk.md)
## [.NET のシノニムのプレビュー](search-synonyms-tutorial-sdk.md)
## [.NET の SQL データ インデクサー](search-indexer-tutorial.md)
## [ポータルのチュートリアル](search-get-started-portal.md)
## [半構造化データの検索](search-semi-structured-data.md)
## [REST API の確認](search-fiddler.md)

# 方法

## 計画と設計
### [SKU を選択する](search-sku-tier.md)
### [サービスの制限](search-limits-quotas-capacity.md)
### [サービスの拡張性](search-capacity-planning.md)
### [マルチテナント方式の設計パターン](search-modeling-multitenant-saas-applications.md)
## セキュリティ
### [データおよび運用面のセキュリティ](search-security-overview.md)
### [ID フィルターを使用してセキュリティ保護する](search-security-trimming-for-azure-search.md)
### [Active Directory を使用してセキュリティ保護する](search-security-trimming-for-azure-search-with-aad.md)
## 開発
### [API のバージョン](search-api-versions.md)
### [Node.js での開発](search-get-started-nodejs.md)
### [Java での開発](search-get-started-java.md)
### [SDK をアップグレードする](search-dotnet-sdk-migration.md)
### [REST API をアップグレードする](search-api-migration.md)
### [複合データ型をモデル化する](search-howto-complex-data-types.md)
### [同時更新を処理する](search-howto-concurrency.md)
### [コード サンプル](https://azure.microsoft.com/resources/samples/?service=search)
## データを読み込む
### [インデクサーの概要](search-indexer-overview.md)
### [Azure Blob Storage インデクサー](search-howto-indexing-azure-blob-storage.md)
### [Azure Table Storage インデクサー](search-howto-indexing-azure-tables.md)
### [Azure SQL インデクサー](search-howto-connecting-azure-sql-database-to-azure-search-using-indexers.md)
### [Azure Cosmos DB インデクサー](search-howto-index-cosmosdb.md)
### [CSV BLOB のインデックスを作成する](search-howto-index-csv-blobs.md)
### [JSON BLOB のインデックスを作成する](search-howto-index-json-blobs.md)
### [Azure VM で SQL Server へのインデクサーの接続を構成する](search-howto-connecting-azure-sql-iaas-to-azure-search-using-indexers.md)
### [インデクサーのフィールド マッピング](search-indexer-field-mappings.md)
##  検索
### [フルテキスト検索のしくみ](search-lucene-query-architecture.md)
### クエリの構築
#### [単純なクエリ構文](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search)
#### [Lucene クエリ構文](https://docs.microsoft.com/rest/api/searchservice/lucene-query-syntax-in-azure-search)
#### [Lucene クエリ例](search-query-lucene-examples.md)
### Azure Search のアナライザー
#### [概要](search-analyzers.md)
#### [言語アナライザー](https://docs.microsoft.com/rest/api/searchservice/language-support)
#### [カスタム アナライザー](https://docs.microsoft.com/rest/api/searchservice/custom-analyzers-in-azure-search)
### Azure Search のフィルター
#### [概要](search-filters.md)
#### [ファセット フィルター](search-filters-facets.md)
#### [言語フィルター](search-filters-language.md)
#### [式の構文リファレンス](https://docs.microsoft.com/rest/api/searchservice/odata-expression-syntax-for-azure-search)
### [ページングの結果](search-pagination-page-layout.md)
### [スコア付け](https://docs.microsoft.com/rest/api/searchservice/add-scoring-profiles-to-a-search-index)
### [検索候補](https://docs.microsoft.com/rest/api/searchservice/suggesters)
### [ファセット ナビゲーション](search-faceted-navigation.md)
### [シノニムのプレビュー](search-synonyms.md)
### [moreLikeThis のプレビュー](search-more-like-this.md)
## 管理と分析
### [Azure Portal を使用した管理](search-manage.md)
### [PowerShell を使用した管理](search-manage-powershell.md)
### [使用状況と統計情報を監視する](search-monitor-usage.md)
### [検索トラフィックの分析](search-traffic-analytics.md)
### [パフォーマンスと最適化](search-performance-optimization.md)

# 参照

## [.NET](/dotnet/api/?term=microsoft.azure.search)
## [.NET (管理)](/dotnet/api/?term=microsoft.azure.management.search)
## [Python (管理)](http://azure-sdk-for-python.readthedocs.io/en/latest/ref/azure.mgmt.search.html)
## [REST](/rest/api/searchservice)
## [REST (管理)](/rest/api/searchmanagement)
## [サービス REST (プレビュー)](search-api-2016-09-01-preview.md)

# リソース

## [FAQ - よく寄せられる質問](search-faq-frequently-asked-questions.md)
## [料金](https://azure.microsoft.com/pricing/details/search/)
## [料金計算ツール](https://azure.microsoft.com/pricing/calculator/)
## [サービスの更新情報](https://azure.microsoft.com/updates/?product=search)
## コースウェアとチュートリアル
### [ビデオとチュートリアル](search-video-demo-tutorial-list.md)
### [バーチャル アカデミー](https://mva.microsoft.com/training-courses/using-windows-azure-search-10540?l=ADkxnd97_9304984382)
## デモ サイト
### [アナライザーのデモを検索する](http://alice.unearth.ai/)
### [ライブ デモ アプリ](https://searchsamples.azurewebsites.net/)
### [求人情報アプリ](http://aka.ms/azjobsdemo)
## パートナーとコミュニティ
### [Azure Search GitHub](https://github.com/Azure-Samples/?utf8=%E2%9C%93&query=search)
### [MSDN フォーラム](https://social.msdn.microsoft.com/forums/azure/home?forum=AzureSearch)
### [Stack Overflow](http://stackoverflow.com/questions/tagged/azure-search)
### [ブログ: リレーショナル データのモデル化](http://blogs.technet.com/b/onsearch/archive/2015/09/08/modeling-the-adventureworks-inventory-database-for-azure-search.aspx)
### [ブログ: 多層構造ファセット](http://blogs.technet.com/b/onsearch/archive/2015/09/09/multi-level-taxonomy-facets-in-azure-search.aspx)



