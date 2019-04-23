---
title: HOW TO：編輯 SharePoint 部署組態 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cfaa260b32deb2cb91b27dfcaa910e950ee00752
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093705"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>HOW TO：編輯 SharePoint 部署組態
  您可以建立部署組態，或修改現有的部署組態。 比方說，您無法執行單一的步驟，或變更的部署程序中的步驟順序。 您可能想要建立或修改部署組態，因為無法變更內建和以程式設計方式加入組態。

## <a name="create-a-sharepoint-deployment-configuration"></a>建立 SharePoint 部署組態

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>若要建立 SharePoint 部署組態

1. 在 **方案總管**，選擇 SharePoint 專案，然後在功能表列上選擇 **專案**， _ProjectName_**屬性**。

2. 在 [ **SharePoint**索引標籤上，選擇**新增**] 按鈕。

     **加入新的部署組態** 對話方塊隨即出現。

3. 在 **名稱**文字中，輸入部署組態的名稱。

4. 在 [**可用的部署步驟**窗格中，選擇您想要加入部署組態，請選擇的步驟 (**>**) 按鈕，然後再選擇 **[確定]** ] 按鈕。

    > [!NOTE]
    >  如果您已設定預先部署命令或部署後命令，只有在您加入自訂的部署設定，也會執行這些步驟。

## <a name="change-the-active-deployment-configuration"></a>變更現用部署組態

#### <a name="to-change-the-active-deployment-configuration"></a>若要變更現用部署組態

1. 在 **方案總管**，選擇 SharePoint 專案，然後在功能表列上選擇 **專案** > **\<*ProjectName*> 屬性**。

2. 選擇**SharePoint**  索引標籤。

3. 在 **現用部署組態**清單方塊中，選擇您想要使用的部署組態的名稱。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
