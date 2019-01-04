---
title: 擴充 SharePoint 專案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cc42ed418de78ee5f75ab51b63c7e1ccdf29911
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863978"
---
# <a name="extend-sharepoint-projects"></a>擴充 SharePoint 專案
  當您想要自訂的 SharePoint 專案的專案層級功能，請建立專案擴充功能。 比方說，您可以新增自訂的專案屬性，或使用者開發的 Visual Studio 中的 SharePoint 方案時所引發的專案層級事件回應。  
  
## <a name="create-project-extensions"></a>建立專案的擴充功能
 若要擴充的專案項目，建置 Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>介面。 如需詳細資訊，請參閱[＜How to：建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
 當您建立的專案擴充功能時，您也可以加入至 SharePoint 專案的下列功能：  
  
- 加入快顯功能表項目。 當您開啟中的 SharePoint 專案節點的捷徑功能表的功能表項目會出現**方案總管**滑鼠右鍵按一下節點或選擇它，然後選擇**Shift** + **F10**索引鍵。 如需詳細資訊，請參閱[＜How to：加入 SharePoint 專案的捷徑功能表項目](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)。  
  
- 新增自訂屬性。 屬性會出現在**屬性**當您選擇 SharePoint 專案中的視窗**方案總管 中**。 如需詳細資訊，請參閱[＜How to：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
  如需示範如何建立、 部署和測試專案擴充功能的逐步解說，請參閱[逐步解說：建立 SharePoint 專案擴充功能](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)。  
  
## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>了解專案延伸模組與專案執行個體之間的關聯性
 當您建立的專案延伸模組時，擴充功能載入任何種類的 SharePoint 專案中開啟時[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含數個 SharePoint 專案範本，例如清單定義、 內容類型和事件接收器。 不過，還有一個 SharePoint 專案類型。 會出現在專案類型**新的專案**對話方塊會連結在一起的一或多個 SharePoint 專案項目時，相同的範本。 因為只有一個 SharePoint 專案類型，建立一個專案的延伸模組套用至所有 SharePoint 專案。 比方說，不能建立的擴充功能，僅適用於**內容類型**專案。  
  
 若要存取特定專案執行個體，處理的其中一個<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>的事件*projectService*實作中的參數<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法。 例如，若要判斷 SharePoint 專案新增至方案時，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>事件。 如需詳細資訊，請參閱[＜How to：建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## <a name="see-also"></a>另請參閱
 [如何：建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [如何：加入 SharePoint 專案的捷徑功能表項目](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [逐步解說：建立 SharePoint 專案擴充功能](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)  
