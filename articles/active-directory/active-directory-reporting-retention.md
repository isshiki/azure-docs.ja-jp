---
title: "Azure Active Directory レポートの保持ポリシー | Microsoft Docs"
description: "Azure Active Directory でのレポート データの保持ポリシー"
services: active-directory
documentationcenter: 
author: MarkusVi
manager: femila
editor: 
ms.assetid: 183e53b0-0647-42e7-8abe-3e9ff424de12
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 10/17/2017
ms.author: markvi
ms.reviewer: dhanyahk
ms.openlocfilehash: 933d251903f4ca74902e984e7a1581a75345ee7f
ms.sourcegitcommit: 9c3150e91cc3075141dc2955a01f47040d76048a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2017
---
# <a name="azure-active-directory-report-retention-policies"></a>Azure Active Directory レポートの保持ポリシー


このトピックでは、最も一般的な質問に対する回答を、Azure Active Directory のさまざまなアクティビティ レポートのデータ保持と一緒に説明します。 

**Q: アクティビティ データの収集を開始するにはどうすればよいか**

**A:**

| Azure AD のエディション | コレクションの開始 |
| :--              | :--   |
| Azure AD Premium P1 <br /> Azure AD Premium P2 | サブスクリプションにサインアップしたとき |
| Azure AD Free | [Azure Active Directory ブレード](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)を初めて開いたとき、または [Reporting API](https://aka.ms/aadreports) を初めて使用したとき  |

---
**Q: Azure Portal でアクティビティ データを使用できるようになるのはいつか**

**A:**

- **すぐに** - Azure クラシック ポータルで既にレポートを操作している場合
- **2 時間以内** - Azure クラシック ポータルでレポートを有効にしていない場合

---
**Q: セキュリティ シグナルの収集を開始するにはどうすればよいか**  

**A:** セキュリティ シグナルの場合、収集プロセスは Identity Protection センターを使用することを選択した時点から開始されます。 


---
**Q: 収集されたデータのどのくらい保存されるのか**

**A:**

**アクティビティ レポート**    

| レポート                 | Azure AD Free | Azure AD Premium P1 | Azure AD Premium P2 |
| :--                    | :--           | :--                 | :--                 |
| ディレクトリ監査        | 7 日        | 30 日             | 30 日             |
| サインイン アクティビティ       | 該当なし           | 30 日             | 30 日             |
| Azure MFA の使用状況        | 90 日間       | 90 日間             | 90 日間             |

**セキュリティ シグナル**

| レポート         | Azure AD Free | Azure AD Premium P1 | Azure AD Premium P2 |
| :--            | :--           | :--                 | :--                 |
| リスクのあるユーザー  | 7 日        | 30 日             | 90 日間             |
| リスクの高いサインイン | 7 日        | 30 日             | 90 日間             |

---
