---
title: 如何：建立實體之間的關聯 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cba9d712e2bcfa90ae37d47e3c518697f10b6add
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981838"
---
# <a name="how-to-create-an-association-between-entities"></a>如何：建立實體之間的關聯
  您可以藉由建立關聯，在商務資料連線（BDC）模型中定義實體之間的關係。 Visual Studio 會產生方法，以提供模型的取用者與每個關聯的相關資訊。 這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 (UI) 中顯示資料關聯性。

 您可以在 BDC 設計工具中建立兩種類型的關聯： [外鍵關聯] 和 [外部無索引鍵關聯]。 如需詳細資訊，請參閱[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)。

### <a name="to-create-an-association-between-entities"></a>若要建立實體之間的關聯

1. 在 [**工具箱**] 的 [ **BusinessDataConnectivity** ] 索引標籤上，選擇 [**關聯**] 專案。

2. 在 [BDC 設計工具] 中選擇來源實體，然後選擇目的實體。

     [**關聯編輯器**] 隨即出現。

3. 如果您想要建立外鍵型關聯，請選取 [**是外鍵關聯**] 核取方塊。

    1. 在 [**識別碼對應**] 資料表的 [**來源**識別碼] 資料行中，選擇 [**欄位**] 資料行中所顯示之每個相符類型描述元旁的識別碼。

         例如，在 [**來源識別碼**] 資料行中，選取 [`ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 型別描述項] 和 [`ReadItem.salesOrder.SalesOrder.ContactID` 型別描述元] 旁邊的 [`ContactID`]。

4. 如果您想要建立外部無索引鍵關聯，請清除 [**是外鍵關聯**] 核取方塊。

5. 選擇 [ **確定** ] 按鈕。

6. 在 BDC 設計工具上，代表關聯的線條會出現在來源實體與目的地實體之間。

     Visual Studio 會將關聯導覽器方法新增至目的地實體的服務類別，以及來源實體的服務類別。 如需關聯流覽方法的詳細資訊，請參閱[支援的作業](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))。

7. 在來源實體的 [關聯導覽器] 方法中，加入可傳回目的地實體集合的程式碼。

8. 在目的地實體的 [關聯導覽器] 方法中，加入會傳回相關來源實體的程式碼。

     如需關聯導覽器方法的範例，請參閱[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)。

## <a name="see-also"></a>請參閱
- [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：加入 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：加入特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：新增更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
- [如何：定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
