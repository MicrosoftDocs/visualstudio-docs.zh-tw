---
title: "擴充 SharePoint 專案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 403ff3793dfd5ae4211444868af8c37dbd908672
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-projects"></a>擴充 SharePoint 專案
  當您想要自訂 SharePoint 專案的專案層級功能，請建立專案擴充功能。 例如，您可以新增自訂的專案屬性中，或回應使用者開發的 Visual Studio 中的 SharePoint 方案時所引發的專案層級事件。  
  
## <a name="creating-project-extensions"></a>建立專案擴充功能  
 若要擴充的專案項目，建置 Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>介面。 如需詳細資訊，請參閱[How to： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
 當您建立專案擴充功能時，您也可以加入下列功能的 SharePoint 專案：  
  
-   加入快顯功能表項目。 當您開啟中的 SharePoint 專案節點的捷徑功能表，出現的功能表項目**方案總管] 中**滑鼠右鍵按一下節點或選擇它，然後選擇 [Shift + F10 鍵。 如需詳細資訊，請參閱[How to： 將捷徑功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)。  
  
-   加入自訂屬性。 屬性會出現在**屬性**當您選擇 SharePoint 專案中的視窗**方案總管 中**。 如需詳細資訊，請參閱[How to： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 如需示範如何建立、 部署和測試專案擴充功能的逐步解說，請參閱[逐步解說： 建立 SharePoint 專案擴充功能](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)。  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>了解專案擴充功能和專案的執行個體之間的關聯性  
 當您建立專案擴充功能時，延伸模組會載入任何一種 SharePoint 專案中開啟時[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]包含數個 SharePoint 專案範本，例如清單定義、 內容類型和事件接收器。 不過，沒有一個 SharePoint 專案類型。 會出現在專案類型**新專案**對話方塊會連結在一起的一或多個 SharePoint 專案項目時，相同的範本。 因為只有一個 SharePoint 專案類型，建立一個專案的延伸模組會套用至所有 SharePoint 專案。 例如，無法建立擴充功能，僅適用於**內容類型**專案。  
  
 若要存取的特定專案的執行個體，處理其中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>事件*projectService*的實作中的參數<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法。 例如，若要判斷 SharePoint 專案加入至方案時，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>事件。 如需詳細資訊，請參閱[How to： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [如何： 將捷徑功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [如何： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [逐步解說： 建立 SharePoint 專案擴充功能](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  