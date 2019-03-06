---
title: 定義自訂 SharePoint 專案項目類型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5f32abba4c4cbdeab59ed66e38019d913e704e6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604818"
---
# <a name="define-custom-sharepoint-project-item-types"></a>定義自訂 SharePoint 專案項目類型
  當您想要建立新類型的 SharePoint 專案項目，請定義新的 SharePoint 專案項目類型。 例如，Visual Studio 不會包含新增的欄位或自訂動作至 SharePoint 網站的 SharePoint 專案項目。 您可以定義自己的 SharePoint 專案項目建立欄位、 自訂動作或其他類型的 SharePoint 元件的型別。

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>工作定義 SharePoint 專案項目類型
 若要定義自訂專案項目類型，建立 Visual Studio 延伸模組組件可實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面。 如需詳細資訊，請參閱[如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

 當您定義的自訂專案項目類型時，您也可以在專案項目，新增下列功能：

- 快顯功能表項目加入專案項目。 當您開啟快顯功能表中的專案項目時，會出現的功能表項目**方案總管**以滑鼠右鍵按一下專案項目，或選擇它，然後選擇**Shift** + **F10**索引鍵。 如需詳細資訊，請參閱[如何：將捷徑功能表項目新增至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)。

- 將自訂屬性加入專案項目。 屬性會出現在**屬性**視窗中，當您選擇的專案項目時**方案總管 中**。 如需詳細資訊，請參閱[如何：將屬性加入至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。

  若要啟用其他開發人員在 Visual Studio 中使用您的專案項目，請建立.spdata 檔案，並建立項目範本或專案項目相關聯的專案範本。 如需詳細資訊，請參閱 <<c0> [ 建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>了解專案項目類型和專案項目執行個體之間的關聯性
 當您定義 SharePoint 專案項目類型時，Visual Studio 相關聯的類型的專案項目新增至 SharePoint 專案時，就會載入您的延伸模組。 例如，如果您定義新**自訂動作**專案項目類型、 Visual Studio 會載入您的延伸模組，當使用者將**自訂動作**至專案的專案項目。 Visual Studio 會使用您的擴充功能的相同執行個體相關聯的專案項目類型的所有執行個體。 在上述範例中，如果使用者加入第二個**自訂動作**專案項目至專案，您的擴充功能的相同執行個體用來自訂的第二個專案項目。

 若要存取您的專案項目類型的特定執行個體，處理的其中一個<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>的事件*projectItemTypeDefinition*實作中的參數<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。 例如，若要判斷您的自訂類型的專案項目新增至專案時，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>事件。 如需詳細資訊，請參閱[如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

## <a name="see-also"></a>另請參閱
- [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [如何：將屬性加入至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [如何：將捷徑功能表項目新增至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [逐步解說：使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [逐步解說：建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [逐步解說：使用專案範本，第 2 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
