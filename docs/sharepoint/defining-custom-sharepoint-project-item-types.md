---
title: 定義自訂 SharePoint 專案項目類型 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d9b752aa8162f52746b4487b863557af6dd37fd9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765576"
---
# <a name="define-custom-sharepoint-project-item-types"></a>定義自訂 SharePoint 專案項目類型
  當您想要建立一種新的 SharePoint 專案項目，定義新的 SharePoint 專案項目類型。 例如，Visual Studio 不包含 SharePoint 專案項目加入欄位或 SharePoint 網站的自訂動作。 您可以定義自己的欄位、 自訂動作或其他類型的 SharePoint 元件建立 SharePoint 專案項目類型。  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>定義 SharePoint 專案項目類型的工作
 若要定義自訂專案項目類型，建立 Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面。 如需詳細資訊，請參閱[如何： 定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
 當您定義的自訂專案項目類型時，您也可以加入下列功能的專案項目：  
  
-   將捷徑功能表項目加入至專案項目。 當您開啟專案項目中的捷徑功能表，出現的功能表項目**方案總管 中**以滑鼠右鍵按一下專案項目，或選擇它，然後選擇**Shift** + **F10**索引鍵。 如需詳細資訊，請參閱[How to： 將捷徑功能表項目加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)。  
  
-   將自訂屬性加入至專案項目。 屬性會出現在**屬性**視窗時選擇的專案項目**方案總管 中**。 如需詳細資訊，請參閱[How to： 將屬性加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 若要啟用其他開發人員在 Visual Studio 中使用您的專案項目，建立.spdata 檔案並建立項目範本或專案項目相關聯的專案範本。 如需詳細資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>了解專案項目類型和專案項目執行個體之間的關聯性
 當您定義 SharePoint 專案項目類型時，Visual Studio 的專案項目相關聯的類型加入至 SharePoint 專案時，就會載入您的擴充功能。 例如，如果您定義新**自訂動作**專案項目類型時，Visual Studio 會載入您的擴充功能，當使用者新增**自訂動作**專案項目加入專案。 Visual Studio 會使用您的擴充功能的相同執行個體相關聯的專案項目類型的所有執行個體。 在上述範例中，如果使用者加入第二個**自訂動作**專案項目加入專案中，您的擴充功能的相同執行個體用於自訂的第二個專案項目。  
  
 若要存取您的專案項目類型的特定執行個體，處理其中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>事件*projectItemTypeDefinition*的實作中的參數<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。 例如，若要判斷您的自訂類型的專案項目加入至專案時，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>事件。 如需詳細資訊，請參閱[如何： 定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
## <a name="see-also"></a>另請參閱
 [如何： 定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [如何： 將屬性加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [如何： 將捷徑功能表項目加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [建立項目範本和專案範本的 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [逐步解說： 建立網站欄專案項目以專案範本，第 1 部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [逐步解說： 建立自訂動作專案項目包含項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [逐步解說： 使用專案範本，第 2 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [部署 Visual Studio 中 SharePoint 工具的延伸模組](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
