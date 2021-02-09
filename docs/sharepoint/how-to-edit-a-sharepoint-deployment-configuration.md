---
title: 如何：編輯 SharePoint 部署設定 |Microsoft Docs
description: 瞭解如何建立 SharePoint 部署設定或修改現有的部署設定。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 59354537f0c1f22534395da1e0ed3db3929a14a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913654"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>如何：編輯 SharePoint 部署設定
  您可以建立部署設定，或修改現有的部署設定。 例如，您可以執行單一步驟或變更部署程式中的步驟順序。 您可能會想要建立或修改部署設定，因為無法變更內建和以程式設計方式新增的設定。

## <a name="create-a-sharepoint-deployment-configuration"></a>建立 SharePoint 部署設定

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>若要建立 SharePoint 部署設定

1. 在 **方案總管** 中，選擇 SharePoint 專案，然後在功能表列上選擇 [專案]、[**專案**_名稱_]**屬性**。

2. 在 [ **SharePoint** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

     [ **加入新的部署** 設定] 對話方塊隨即出現。

3. 在 [ **名稱** ] 文字方塊中，輸入部署設定的名稱。

4. 在 [ **可用的部署步驟** ] 窗格中，選擇您要新增至部署設定的步驟，選擇 [ (**>** ]) 按鈕，然後選擇 [ **確定]** 按鈕。

    > [!NOTE]
    > 如果您已設定預先部署命令或部署後命令，則只有在將這些步驟新增至自訂部署設定時，才會執行這些步驟。

## <a name="change-the-active-deployment-configuration"></a>變更主動部署設定

#### <a name="to-change-the-active-deployment-configuration"></a>變更主動部署設定

1. 在 **方案總管** 中，選擇 SharePoint 專案，然後在功能表列上選擇 [**專案**  >  **\<*ProjectName*> 屬性**]。

2. 選擇 [ **SharePoint** ] 索引標籤。

3. 在 [使用中的 **部署** 設定] 清單方塊中，選擇您想要使用的部署設定名稱。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
