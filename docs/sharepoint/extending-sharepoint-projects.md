---
title: 擴充 SharePoint 專案 |Microsoft Docs
description: 瞭解如何在您想要自訂 SharePoint 專案的專案層級功能時，建立專案延伸模組。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8efeb704bb247e653af0ee062efcc71ad390c5ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948657"
---
# <a name="extend-sharepoint-projects"></a>擴充 SharePoint 專案
  當您想要自訂 SharePoint 專案的專案層級功能時，請建立專案延伸模組。 例如，您可以加入自訂專案屬性，或回應使用者在 Visual Studio 中開發 SharePoint 方案時引發的專案層級事件。

## <a name="create-project-extensions"></a>建立專案延伸模組
 若要擴充專案專案，請建立一個 Visual Studio 擴充元件來執行 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面。 如需詳細資訊，請參閱 [如何：建立 SharePoint 專案延伸](../sharepoint/how-to-create-a-sharepoint-project-extension.md)模組。

 當您建立專案延伸模組時，您也可以將下列功能加入至 SharePoint 專案：

- 新增快捷方式功能表項目。 當您在 [**方案總管**] 中開啟 SharePoint 專案節點的快捷方式功能表，以滑鼠右鍵按一下該節點或選擇該節點，然後選擇 **Shift** + **F10** 鍵時，就會出現功能表項目。 如需詳細資訊，請參閱 [如何：將快捷方式功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)。

- 新增自訂屬性。 當您在 **方案總管** 中選擇 SharePoint 專案時，屬性會出現在 [**屬性**] 視窗中。 如需詳細資訊，請參閱 [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。

  如需示範如何建立、部署和測試專案延伸的逐步解說，請參閱 [逐步解說：建立 SharePoint 專案延伸](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)。

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>瞭解專案延伸和專案實例之間的關聯性
 當您建立專案擴充功能時，會在中開啟任何種類的 SharePoint 專案時載入擴充功能 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含數個 SharePoint 專案範本，例如清單定義、內容類型和事件接收器。 不過，只有一個 SharePoint 專案類型。 出現在 [ **新增專案** ] 對話方塊中的專案類型，只是組合一或多個 SharePoint 專案專案的範本。 由於只有一個 SharePoint 專案類型，因此針對某個專案所建立的延伸模組會套用至所有 SharePoint 專案。 例如，您無法建立只套用至 **內容類型** 專案的延伸模組。

 若要存取特定的專案實例，請 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 在方法的執行中處理 *projectService* 參數的其中一個事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 。 例如，若要判斷何時將 SharePoint 專案加入至方案，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 事件。 如需詳細資訊，請參閱 [如何：建立 SharePoint 專案延伸](../sharepoint/how-to-create-a-sharepoint-project-extension.md)模組。

## <a name="see-also"></a>另請參閱
- [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [如何：將快捷方式功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [逐步解說：建立 SharePoint 專案延伸模組](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)
- [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
