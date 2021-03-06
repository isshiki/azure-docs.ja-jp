---
title: "VM から Azure DevTest Labs カスタム イメージを作成する | Microsoft Docs"
description: "Azure ポータルを使用して、プロビジョニングされた VM から Azure DevTest Labs にカスタム イメージを作成する方法について説明します"
services: devtest-lab,virtual-machines
documentationcenter: na
author: craigcaseyMSFT
manager: douge
editor: 
ms.assetid: 
ms.service: devtest-lab
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/10/2017
ms.author: v-craic
ms.openlocfilehash: ce854024df5c6974873cf3574bf2de282946f6d0
ms.sourcegitcommit: 85012dbead7879f1f6c2965daa61302eb78bd366
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="create-a-custom-image-from-a-vm"></a>VM からカスタム イメージを作成する

[!INCLUDE [devtest-lab-custom-image-definition](../../includes/devtest-lab-custom-image-definition.md)]

## <a name="step-by-step-instructions"></a>詳細な手順

プロビジョニングされた VM からカスタム イメージを作成し、その後、そのカスタム イメージを使用して同一の VM を作成できます。 次の手順では、VM からカスタム イメージを作成する方法を説明します。

1. [Azure ポータル](http://go.microsoft.com/fwlink/p/?LinkID=525040)にサインインします。

1. **[その他のサービス]** を選択し、一覧の **[DevTest Labs]** を選択します。

1. ラボの一覧で目的のラボを選択します。  

1. ラボのブレードで、 **[仮想マシン]**を選択します。
 
1. **[仮想マシン]** ブレードで、カスタム イメージを作成する VM を選択します。

1. VM のブレードで、 **[Create custom image (VHD) (カスタム イメージ を作成する (VHD))]**を選択します。

    ![カスタム イメージのメニュー項目の作成](./media/devtest-lab-create-template/create-custom-image.png)

1. **[Create image (イメージの作成)]** ブレードで、カスタム イメージの名前と説明を入力します。 この情報は、VM を作成する際にベースの一覧に表示されます。

    ![カスタム イメージの作成ブレード](./media/devtest-lab-create-template/create-custom-image-blade.png)

1. sysprep を VM で実行したかどうかを選択します。 sysprep を VM で実行していない場合は、カスタム イメージから VM を作成するときに sysprep を実行するかどうかを指定します。

1. 完了したら **[OK]** を選択して、カスタム イメージを作成します。

[!INCLUDE [devtest-lab-try-it-out](../../includes/devtest-lab-try-it-out.md)]

## <a name="related-blog-posts"></a>関連するブログ記事

- [Custom images or formulas? (カスタム イメージか数式か?)](https://blogs.msdn.microsoft.com/devtestlab/2016/04/06/custom-images-or-formulas/)
- [Copying Custom Images between Azure DevTest Labs (Azure DevTest Labs 間でのカスタム イメージのコピー)](http://www.visualstudiogeeks.com/blog/DevOps/How-To-Move-CustomImages-VHD-Between-AzureDevTestLabs#copying-custom-images-between-azure-devtest-labs)

##<a name="next-steps"></a>次の手順

- [VM をラボに追加する](devtest-lab-add-vm.md)
