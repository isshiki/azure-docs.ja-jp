---
title: "エンドユーザー認証: Azure Active Directory を使用した Python と Data Lake Store | Microsoft Docs"
description: "Python と Azure Active Directory を使用した Data Lake Store でエンドユーザー認証を行う方法について説明します"
services: data-lake-store
documentationcenter: 
author: nitinme
manager: jhubbard
editor: cgronlun
ms.service: data-lake-store
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: big-data
ms.date: 10/11/2017
ms.author: nitinme
ms.openlocfilehash: 48990c57fb10127733623000a105507b5a48d900
ms.sourcegitcommit: b5c6197f997aa6858f420302d375896360dd7ceb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="end-user-authentication-with-data-lake-store-using-python"></a>Data Lake Store での Python を使用したエンドユーザー認証
> [!div class="op_single_selector"]
> * [Java の使用](data-lake-store-end-user-authenticate-java-sdk.md)
> * [.NET SDK の使用](data-lake-store-end-user-authenticate-net-sdk.md)
> * [Python の使用](data-lake-store-end-user-authenticate-python.md)
> * [REST API の使用](data-lake-store-end-user-authenticate-rest-api.md)
> 
> 

この記事では、Python SDK を使用して、Azure Data Lake Store に対するエンドユーザー認証を行う方法について説明します。 エンドユーザー認証は、2 つのカテゴリに分割できます。

* 多要素認証なしのエンドユーザー認証
* 多要素認証によるエンドユーザー認証

この記事では、両方のオプションについて説明します。 Python を使用した Data Lake Store に対するサービス間認証については、「[Service-to-service authentication with Data Lake Store using Python (Data Lake Store での Python を使用したサービス間認証)](data-lake-store-service-to-service-authenticate-python.md)」を参照してください。

## <a name="prerequisites"></a>前提条件

* **Python**。 Python は、[ここ](https://www.python.org/downloads/)からダウンロードできます。 この記事では、Python 3.6.2 を使用します。

* **Azure サブスクリプション**。 [Azure 無料試用版の取得](https://azure.microsoft.com/pricing/free-trial/)に関するページを参照してください。

* **Azure Active Directory "ネイティブ" アプリケーションを作成します**。 [Azure Active Directory を使用した Data Lake Store に対するエンドユーザー認証](data-lake-store-end-user-authenticate-using-active-directory.md)のステップを完了している必要があります。

## <a name="install-the-modules"></a>モジュールをインストールする

Python を使用して Data Lake Store を操作するには、3 つのモジュールをインストールする必要があります。

* `azure-mgmt-resource` モジュール。これには、Active Directory 用の Azure モジュールなどが含まれています。
* `azure-mgmt-datalake-store` モジュール。これには、Azure Data Lake Store アカウント管理操作が含まれています。 このモジュールの詳細については、[Azure Data Lake Store 管理モジュール リファレンス](http://azure-sdk-for-python.readthedocs.io/en/latest/sample_azure-mgmt-datalake-store.html)を参照してください。
* `azure-datalake-store` モジュール。これには、Azure Data Lake Store ファイルシステム操作が含まれています。 このモジュールの詳細については、[Azure Data Lake Store ファイルシステム モジュール リファレンス](http://azure-datalake-store.readthedocs.io/en/latest/)を参照してください。

モジュールをインストールするには、次のコマンドを使用します。

```
pip install azure-mgmt-resource
pip install azure-mgmt-datalake-store
pip install azure-datalake-store
```

## <a name="create-a-new-python-application"></a>新しい Python アプリケーションを作成する

1. 任意の IDE で、**mysample.py** などの新しい Python アプリケーションを作成します。

2. 必要なモジュールをインポートするには、次のスニペットを追加します

    ```
    ## Use this for Azure AD authentication
    from msrestazure.azure_active_directory import AADTokenCredentials

    ## Required for Azure Data Lake Store account management
    from azure.mgmt.datalake.store import DataLakeStoreAccountManagementClient
    from azure.mgmt.datalake.store.models import DataLakeStoreAccount

    ## Required for Azure Data Lake Store filesystem management
    from azure.datalake.store import core, lib, multithread

    # Common Azure imports
    import adal
    from azure.mgmt.resource.resources import ResourceManagementClient
    from azure.mgmt.resource.resources.models import ResourceGroup

    ## Use these as needed for your application
    import logging, pprint, uuid, time
    ```

3. mysample.py に対する変更を保存します。

## <a name="end-user-authentication-with-multi-factor-authentication"></a>多要素認証によるエンドユーザー認証

### <a name="for-account-management"></a>アカウント管理を行う場合

Data Lake Store アカウントに対するアカウント管理操作のために Azure AD で認証する場合、次のスニペットを使用します。 次のスニペットは、多要素認証を使用してアプリケーションを認証するために使用できます。 既存の Azure AD **ネイティブ** アプリケーションに対して以下の値を指定します。

    authority_host_url = "https://login.microsoftonline.com"
    tenant = "FILL-IN-HERE"
    authority_url = authority_host_url + '/' + tenant
    client_id = 'FILL-IN-HERE'
    redirect = 'urn:ietf:wg:oauth:2.0:oob'
    RESOURCE = 'https://management.core.windows.net/'
    
    context = adal.AuthenticationContext(authority_url)
    code = context.acquire_user_code(RESOURCE, client_id)
    print(code['message'])
    mgmt_token = context.acquire_token_with_device_code(RESOURCE, code, client_id)
    armCreds = AADTokenCredentials(mgmt_token, client_id, resource = RESOURCE)

### <a name="for-filesystem-operations"></a>ファイルシステム操作を行う場合

Data Lake Store アカウントに対するファイルシステム操作のために Azure AD で認証する場合、これを使用します。 次のスニペットは、多要素認証を使用してアプリケーションを認証するために使用できます。 既存の Azure AD **ネイティブ** アプリケーションに対して以下の値を指定します。

    adlCreds = lib.auth(tenant_id='FILL-IN-HERE', resource = 'https://datalake.azure.net/')

## <a name="end-user-authentication-without-multi-factor-authentication"></a>多要素認証なしのエンドユーザー認証

これは推奨されていません。 詳細については、[Python SDK を使用した Azure 認証](https://docs.microsoft.com/python/azure/python-sdk-azure-authenticate?view=azure-python#mgmt-auth-token)に関するページを参照してください。
   
## <a name="next-steps"></a>次のステップ
この記事では、エンドユーザー認証を使って、Python を使用して Azure Data Lake Store で認証する方法を説明しました。 これで、Python を使用して Azure Data Lake Store を使用する方法について説明した次の記事に進めるようになりました。

* [Python を使用した Data Lake Store に対するアカウント管理操作](data-lake-store-get-started-python.md)
* [Python を使用した Data Lake Store に対するデータ操作](data-lake-store-data-operations-python.md)

