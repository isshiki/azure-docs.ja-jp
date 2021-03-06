---
title: "Azure Active Directory の条件付きアクセスのベスト プラクティス | Microsoft Docs"
description: "条件付きアクセス ポリシーを構成するときに知っておくべきことと避けるべきことについてご確認ください。"
services: active-directory
keywords: "アプリへの条件付きアクセス, Azure AD での条件付きアクセス, 企業リソースへの安全なアクセス, 条件付きアクセス ポリシー"
documentationcenter: 
author: MarkusVi
manager: mtillman
editor: 
ms.assetid: 8c1d978f-e80b-420e-853a-8bbddc4bcdad
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 12/12/2017
ms.author: markvi
ms.reviewer: calebb
ms.openlocfilehash: 8c6707505a6331b53e06b1de60575dd3637ea477
ms.sourcegitcommit: aaba209b9cea87cb983e6f498e7a820616a77471
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="best-practices-for-conditional-access-in-azure-active-directory"></a>Azure Active Directory の条件付きアクセスのベスト プラクティス

このトピックでは、条件付きアクセス ポリシーを構成するときに知っておくべきことと避けるべきことについて説明します。 このトピックを読む前に、概念と用語について理解しておいてください。「[Azure Active Directory の条件付きアクセス](active-directory-conditional-access-azure-portal.md)」に説明があります。

## <a name="what-you-should-know"></a>知っておくべきこと

### <a name="whats-required-to-make-a-policy-work"></a>ポリシーを機能させるために必要なこと

新しいポリシーを作成するとき、ユーザー、グループ、アプリケーション、アクセスの制御は選択されていません。

![クラウド アプリ](./media/active-directory-conditional-access-best-practices/02.png)


ポリシーを機能させるには、以下を構成する必要があります。


|対象           | 方法                                  | 理由|
|:--            | :--                                  | :-- |
|**クラウド アプリ** |1 つまたは複数のアプリを選択する必要があります。  | 条件付きアクセス ポリシーの目的は、許可されているユーザーがどのようにアプリケーションにアクセスできるかを微調整できるようにすることです。|
| **ユーザーとグループ** | 選択したクラウド アプリにアクセスする権限を与えられたユーザーまたはグループを、少なくとも 1 人は選択する必要があります。 | ユーザーとグループが割り当てられていない条件付きアクセス ポリシーは、トリガーされることはありません。 |
| **アクセスの制御** | アクセスの制御を少なくとも 1 つ選択する必要があります。 | 条件が満たされた場合のポリシー プロセッサの対応を決める必要があります。|


これらの基本的な要件に加えて、多くの場合、条件も構成する必要があります。 ポリシーは構成された条件なしでも機能しますが、条件はアプリケーションへのアクセスの微調整の推進要因となります。


![クラウド アプリ](./media/active-directory-conditional-access-best-practices/04.png)



### <a name="how-are-assignments-evaluated"></a>割り当てはどのように評価されますか。

すべての割り当ては、論理的に **AND** 処理されます。 複数の割り当てを構成した場合、ポリシーをトリガーするには、すべての割り当てを満たす必要があります。  

組織のネットワークの外部から行われたすべての接続に適用される場所の条件を構成する必要がある場合は、次の割り当てを行うことでこれを実現できます。

- **すべての場所**を含める
- **すべての信頼できる IP** を除外する

### <a name="what-happens-if-you-have-policies-in-the-azure-classic-portal-and-azure-portal-configured"></a>Azure クラシック ポータルと Azure Portal の両方にポリシーが構成されている場合はどうなりますか。  
Azure Active Directory によって両方のポリシーが適用されます。ユーザーは、すべての要件が満たされた場合のみ、アクセスできます。

### <a name="what-happens-if-you-have-policies-in-the-intune-silverlight-portal-and-the-azure-portal"></a>Intune Silverlight ポータルと Azure Portal の両方にポリシーが構成されている場合はどうなりますか。
Azure Active Directory によって両方のポリシーが適用されます。ユーザーは、すべての要件が満たされた場合のみ、アクセスできます。

### <a name="what-happens-if-i-have-multiple-policies-for-the-same-user-configured"></a>同じユーザーに対して複数のポリシーが構成されている場合はどうなりますか。  
毎回のサインインで、すべてのポリシーが Azure Active Directory によって評価され、すべての要件が満たされていることを確認したうえで、ユーザーのアクセスが許可されます。


### <a name="does-conditional-access-work-with-exchange-activesync"></a>条件付きアクセスは、Exchange ActiveSync と連携しますか。

はい。条件付きアクセス ポリシーで Exchange ActiveSync を使用できます。


## <a name="what-you-should-avoid-doing"></a>避けるべきこと

条件付きアクセス フレームワークは、優れた構成柔軟性を提供します。 ただし、柔軟性が高いということは、リリースの前に各構成ポリシーを慎重に見直して、望ましくない結果を避ける必要があることも意味します。 この状況では、**すべてのユーザー/グループ/クラウド アプリ**などの完全なセットに影響する割り当てには特に注意を払う必要があります。

お客様の環境では、次の構成を避ける必要があります。


**すべてのユーザー、すべてのクラウド アプリに対して:**

- **アクセスのブロック** - この構成では組織全体がブロックされるため、明らかによい方法ではありません。

- **準拠しているデバイスが必要です** - 登録されたデバイスをまだ持っていないユーザーに対して、このポリシーは Intune ポータルへのアクセスを含むすべてのアクセスをブロックします。 このポリシーにより、登録済みのデバイスを持たない管理者は、Azure Portal に戻ってポリシーを変更することができなくなります。

- **ドメインへの参加が必要** - このポリシーでは、ドメイン参加済みデバイスをまだ持っていない場合に、組織内のすべてのユーザーのアクセスがブロックされる可能性もあります。


**すべてのユーザー、すべてのクラウド アプリ、すべてのデバイス プラットフォームに対して:**

- **アクセスのブロック** - この構成では組織全体がブロックされるため、明らかによい方法ではありません。



## <a name="policy-migration"></a>ポリシーの移行

次の理由から、Azure Portal で作成していないポリシーの移行を検討する必要があります。

- 以前は処理できなかったシナリオに対処できるようになった可能性があります。

- ポリシーを統合することで、管理する必要のあるポリシーの数を減らすことができます。   

- 一元的な場所ですべての条件付きアクセス ポリシーを管理することができます。

- Azure クラシック ポータルは廃止されます。   


詳しくは、「[Azure Portal でクラシック ポリシーを移行する](active-directory-conditional-access-migration.md)」をご覧ください。


## <a name="next-steps"></a>次のステップ

条件付きアクセスポリシーの構成方法については、[Azure Active Directory での条件付きアクセスの使用](active-directory-conditional-access-azure-portal-get-started.md)に関する記事を参照してください。
