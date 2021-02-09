---
title: 如何：建立實體之間的關聯 |Microsoft Docs
description: 在 Visual Studio 中建立關聯，以定義商務資料連線中實體之間的關聯性 (BDC) 模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e726e8b5702a656b340401c9a2db26e40be1a37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925575"
---
# <a name="how-to-create-an-association-between-entities"></a>如何：建立實體之間的關聯
  您可以藉由建立關聯來定義商務資料連線中實體之間的關聯性 (BDC) 模型。 Visual Studio 會產生可提供模型取用者的方法，以及每個關聯的相關資訊。 這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 (UI) 中顯示資料關聯性。

 您可以在 BDC 設計工具中建立兩種類型的關聯：外鍵型關聯和外部無索引鍵關聯。 如需詳細資訊，請參閱 [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)。

### <a name="to-create-an-association-between-entities"></a>若要建立實體之間的關聯

1. 在 [**工具箱**] 的 [ **BusinessDataConnectivity** ] 索引標籤上，選擇 [**關聯**] 專案。

2. 在 [BDC 設計工具] 中選擇來源實體，然後選擇目的實體。

     [ **關聯編輯器** ] 隨即出現。

3. 如果您想要建立外鍵關聯，請選取 [ **為外鍵關聯** ] 核取方塊。

    1. 在 [**識別碼對應**] 資料表的 [**來源** 識別碼] 資料行中，選擇出現在 **欄位** 資料行中之每個相符類型描述元旁的識別碼。

         例如，在 [ **來源識別碼** ] 資料行中，選取 `ContactID` 類型描述元旁的 `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 和 `ReadItem.salesOrder.SalesOrder.ContactID` 類型描述元。

4. 如果您想要建立外部無索引鍵關聯，請清除 [ **為外鍵關聯** ] 核取方塊。

5. 選擇 [確定]  按鈕。

6. 在 BDC 設計工具上，來源實體與目的地實體之間會出現代表關聯的線條。

     Visual Studio 將關聯導覽器方法加入至目的地實體的服務類別和來源實體的服務類別。 如需關聯導覽方法的詳細資訊，請參閱 [支援的作業](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))。

7. 在來源實體的 [關聯導覽器] 方法中，加入可傳回目的實體集合的程式碼。

8. 在目的地實體的 [關聯導覽器] 方法中，加入可傳回相關來源實體的程式碼。

     如需關聯導覽器方法的範例，請參閱 [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)。

## <a name="see-also"></a>另請參閱
- [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
- [如何：定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
