---
title: FAQ - Azure Active Directory Domain Services | Microsoft Docs
description: "Azure Active Directory Domain Services についてよく寄せられる質問"
services: active-directory-ds
documentationcenter: 
author: mahesh-unnikrishnan
manager: mtillman
editor: curtand
ms.assetid: 48731820-9e8c-4ec2-95e8-83dba1e58775
ms.service: active-directory-ds
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 12/07/2017
ms.author: maheshu
ms.openlocfilehash: cfab51f985dd0b9db109f1ca8e4030bc9d0de1cc
ms.sourcegitcommit: e266df9f97d04acfc4a843770fadfd8edf4fa2b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2017
---
# <a name="azure-active-directory-domain-services-frequently-asked-questions-faqs"></a>Azure Active Directory Domain Services: よく寄せられる質問 (FAQ)
このページでは、Azure Active Directory Domain Services に関してよく寄せられる質問への回答が記載されています。 常に最新情報をチェックしてください。

### <a name="troubleshooting-guide"></a>トラブルシューティング ガイド
Azure AD Domain Services を構成または管理する際に生じる一般的な問題の解決策については、「[トラブルシューティング ガイド](active-directory-ds-troubleshooting.md)」を参照してください。

### <a name="configuration"></a>構成
#### <a name="can-i-create-multiple-managed-domains-for-a-single-azure-ad-directory"></a>1 つの Azure AD ディレクトリに対して複数の管理対象ドメインを作成することはできますか。

いいえ。 1 つの Azure AD ディレクトリに対して Azure AD Domain Services によって対応される管理対象ドメインは 1 つだけ作成できます。  

#### <a name="can-i-enable-azure-ad-domain-services-in-an-azure-resource-manager-virtual-network"></a>Azure Resource Manager 仮想ネットワークで Azure AD Domain Services を有効にすることはできますか。
はい。 Azure AD Domain Services は Azure Resource Manager 仮想ネットワークで有効にすることができます。 現在この機能はプレビュー版です。

#### <a name="can-i-migrate-my-existing-managed-domain-from-a-classic-virtual-network-to-a-resource-manager-virtual-network"></a>既存の管理対象ドメインをクラシック仮想ネットワークから Resource Manager 仮想ネットワークに移行することはできますか。
現時点では連携しません。 将来的には、既存の管理対象ドメインをクラシック仮想ネットワークから Resource Manager 仮想ネットワークに移行するメカニズムを提供します。

#### <a name="can-i-enable-azure-ad-domain-services-in-an-azure-csp-cloud-solution-provider-subscription"></a>Azure AD Domain Services を Azure CSP (Cloud Solution Provider) サブスクリプション内で有効にできますか。

いいえ。 現在、製品チームは CSP サブスクリプションに対するサポートを追加するように作業しています。

#### <a name="can-i-enable-azure-ad-domain-services-in-a-federated-azure-ad-directory-i-use-adfs-to-authenticate-users-for-access-to-office-365-and-do-not-synchronize-password-hashes-to-azure-ad-can-i-enable-azure-ad-domain-services-for-this-directory"></a>フェデレーション Azure AD ディレクトリの Azure AD Domain Services を有効にすることはできますか。 Office 365 にアクセスするユーザーの認証に ADFS を使い、パスワード ハッシュを Azure AD と同期しません。 このディレクトリの Azure AD Domain Services を有効にすることはできますか。
いいえ。 Azure AD Domain Services では、NTLM または Kerberos を通じたユーザーの認証で、ユーザー アカウントのパスワード ハッシュへのアクセスが必要になります。 フェデレーション ディレクトリでは、パスワード ハッシュは Azure AD ディレクトリに格納されません。 そのため、Azure AD Domain Services では、このような Azure AD ディレクトリは使用されません。

#### <a name="can-i-make-azure-ad-domain-services-available-in-multiple-virtual-networks-within-my-subscription"></a>Azure AD Domain Services をサブスクリプション内の複数の仮想ネットワークで利用できますか。
このサービスそのものが、そのようなシナリオを直接サポートすることはありません。 管理対象ドメインは一度に 1 つの仮想ネットワークでのみ利用できます。 ただし、Azure AD Domain Services を他の仮想ネットワークに公開するために複数の仮想ネットワーク間の接続を構成できます。 [Azure で仮想ネットワークに接続する](../vpn-gateway/virtual-networks-configure-vnet-to-vnet-connection.md)方法をご覧ください。

#### <a name="can-i-enable-azure-ad-domain-services-using-powershell"></a>PowerShell を使用して Azure AD ドメイン サービスを有効にできますか。
はい。 [PowerShell を使って Azure AD Domain Services を有効にする方法](active-directory-ds-enable-using-powershell.md)に関する記事をご覧ください。

#### <a name="is-azure-ad-domain-services-available-in-the-new-azure-portal"></a>Azure AD Domain Services は新しい Azure Portal で利用できますか。
はい。 Azure AD Domain Services は、[Azure Portal](https://portal.azure.com) を使って構成できます。 [Azure クラシック ポータル](https://manage.windowsazure.com)は現在サポートされていません。

#### <a name="can-i-enable-azure-ad-domain-services-using-a-resource-manager-template"></a>Resource Manager テンプレートを使用して Azure AD Domain Services を有効にできますか。
はい。 [PowerShell を使って Azure AD Domain Services を有効にする方法](active-directory-ds-enable-using-powershell.md)に関する記事をご覧ください。

#### <a name="can-i-add-domain-controllers-to-an-azure-ad-domain-services-managed-domain"></a>Azure AD ドメイン サービスの管理対象ドメインにドメイン コント ローラーを追加することはできますか。
いいえ。 管理対象ドメインは Azure AD Domain Services によって提供されるドメインです。 このドメインに対してドメイン コントローラーをプロビジョニング、構成、または管理する必要はありません。これらの管理作業は Microsoft によるサービスとして提供されます。 そのため、管理対象ドメインに追加のドメイン コント ローラー (読み取り/書き込みも読み取り専用も) を追加することはできません。

### <a name="administration-and-operations"></a>管理と操作
#### <a name="can-i-connect-to-the-domain-controller-for-my-managed-domain-using-remote-desktop"></a>リモート デスクトップを使用して管理対象ドメインのドメイン コントローラーに接続できますか。
いいえ。 管理対象ドメインのドメイン コントローラーにリモート デスクトップで接続する権限はありません。 "AAD DC 管理者" グループのメンバーは、Active Directory 管理センター (ADAC) や AD PowerShell などの AD 管理ツールで管理対象ドメインを管理できます。 これらのツールは、"リモート サーバー管理ツール" 機能を使用して、管理対象ドメインに参加している Windows サーバーにインストールされます。

#### <a name="ive-enabled-azure-ad-domain-services-what-user-account-do-i-use-to-domain-join-machines-to-this-domain"></a>Azure AD Domain Services を有効にしています。 このドメインに参加しているドメイン コンピューターでは、どのユーザー アカウントを使用できますか。
管理グループのメンバー ("AAD DC 管理者" など) は、ドメインに参加しているコンピューターで使用できます。 さらに、このグループのメンバーには、ドメインに参加しているコンピューターへのリモート デスクトップ アクセス権が付与されます。

#### <a name="do-i-have-domain-administrator-privileges-for-the-managed-domain-provided-by-azure-ad-domain-services"></a>Azure AD Domain Services によって提供される管理対象ドメインにドメイン管理者特権はありますか。
いいえ。 管理対象ドメイン上に管理者特権は付与されません。 "ドメイン管理者" 特権と "エンタープライズ管理者" 特権はどちらも、ドメインでは利用できません。 Azure AD ディレクトリ内の既存のドメイン管理者グループまたはエンタープライズ管理者グループにも、ドメインに関するドメイン/エンタープライズ管理者特権は付与されません。

#### <a name="can-i-modify-group-memberships-using-ldap-or-other-ad-administrative-tools-on-managed-domains"></a>管理対象ドメインで LDAP または他の AD 管理ツールを使用してグループ メンバーシップを変更できますか。
いいえ。 Azure AD Domain Services によってサービスされるドメインのグループ メンバーシップは変更できません。 ユーザー属性に対しても同様です。 ただし、Azure AD またはオンプレミスのドメインのいずれかで、グループ メンバーシップまたはユーザー属性を変更できます。 このような変更は、Azure AD Domain Services に自動的に同期されます。

#### <a name="how-long-does-it-take-for-changes-i-make-to-my-azure-ad-directory-to-be-visible-in-my-managed-domain"></a>Azure AD ディレクトリに対して行った変更が管理対象ドメインに反映されるまで、どのくらいの時間がかかりますか。
Azure AD UI または PowerShell を使用して Azure AD ディレクトリに対して行った変更は、管理対象ドメインに同期されます。 この同期プロセスはバック グラウンドで実行されます。 1 回のみ実行されるディレクトリの初期同期が完了した後は、Azure AD で行われた変更が管理対象ドメインに反映されるまで、通常は約 20 分かかります。

#### <a name="can-i-extend-the-schema-of-the-managed-domain-provided-by-azure-ad-domain-services"></a>Azure AD Domain Services によって提供される管理対象ドメインのスキーマは拡張できますか。
いいえ。 スキーマは、Microsoft が管理対象ドメインを管理することで管理されます。 Azure AD ドメイン サービスでは、スキーマの拡張機能はサポートされていません。

#### <a name="can-i-modify-or-add-dns-records-in-my-managed-domain"></a>管理対象ドメインの DNS レコードを変更または追加できますか。
はい。 "AAD DC 管理者" グループのメンバーには、管理対象ドメインの DNS レコードを変更できるよう "DNS 管理者" 特権が付与されます。 これらのメンバーは、管理対象ドメインに参加している Windows Server を実行しているコンピューター上で DNS マネージャー コンソールを使用して、DNS を管理できます。 DNS マネージャー コンソールを使用するには、"リモート サーバー管理ツール" オプション機能の一部である "DNS サーバー ツール" をサーバーにインストールします。 [DNS の管理、監視、およびトラブルシューティングを行うためのユーティリティ](https://technet.microsoft.com/library/cc753579.aspx) の詳細については、TechNet をご覧ください。

### <a name="billing-and-availability"></a>課金と可用性
#### <a name="is-azure-ad-domain-services-a-paid-service"></a>Azure AD Domain Services は有料のサービスですか。
はい。 詳細については、 [価格に関するページ](https://azure.microsoft.com/pricing/details/active-directory-ds/)を参照してください。

#### <a name="is-there-a-free-trial-for-the-service"></a>サービスの無料試用版はありますか。
このサービスは、Azure の無料試用版に含まれています。 [1 か月間の無料試用版](https://azure.microsoft.com/pricing/free-trial/)にサインアップできます。

#### <a name="can-i-pause-an-azure-ad-domain-services-managed-domain"></a>Azure AD Domain Services 管理対象ドメインを一時停止することはできますか。 

いいえ。 Azure AD Domain Services 管理対象ドメインを有効にすると、管理対象ドメインを無効化/削除するまで、選択した仮想ネットワーク内でサービスを使用できます。 サービスを一時停止する方法はありません。 課金は、管理対象ドメインを削除するまで、1 時間ごとに続行されます。

#### <a name="can-i-get-azure-ad-domain-services-as-part-of-enterprise-mobility-suite-ems-do-i-need-azure-ad-premium-to-use-azure-ad-domain-services"></a>Enterprise Mobility Suite (EMS) の一部として Azure AD Domain Services を取得できますか。 Azure AD Domain Services を使用するのに Azure AD Premium が必要ですか。
いいえ。 Azure AD Domain Services は従量課金の Azure サービスであり、EMS には含まれていません。 Azure AD Domain Services は、Azure AD のすべてのエディション (Free、Basic、および Premium) で使用できます 。 使用状況に応じて、時間単位で課金されます。

#### <a name="what-azure-regions-is-the-service-available-in"></a>このサービスは、どの Azure のリージョンで利用できますか。
Azure AD Domain Services を使用できる Azure リージョンの一覧については、[リージョン別の Azure サービス](https://azure.microsoft.com/regions/#services/)に関するページを参照してください。
