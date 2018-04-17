---
title: 如何： 建立實體之間的關聯 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c341586fbd2a22f38385a6c613058318f5c2d6a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-association-between-entities"></a>如何：建立實體之間的關聯
  您可以定義您藉由建立關聯的商務資料連線 (BDC) 模型中實體之間的關聯性。 Visual Studio 會產生模型的取用者提供每個關聯的相關資訊的方法。 這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 (UI) 中顯示資料關聯性。  
  
 您可以在 BDC 設計工具中建立兩種類型的關聯： 外部索引鍵為基礎的關聯和外部無索引鍵的關聯。 如需詳細資訊，請參閱[建立實體之間關聯](../sharepoint/creating-an-association-between-entities.md)。  
  
### <a name="to-create-an-association-between-entities"></a>若要建立實體之間的關聯  
  
1.  在**BusinessDataConnectivity**  索引標籤**工具箱**，選擇**關聯**項目。  
  
2.  在 [BDC 設計工具] 中選擇來源實體，然後選擇目的實體。  
  
     **關聯編輯器**隨即出現。  
  
3.  如果您想要建立外部索引鍵為基礎的關聯，請選取**是外部索引鍵關聯**核取方塊。  
  
    1.  在**來源識別碼**資料行**識別項對應**資料表中，選擇旁邊會出現在每個相符類型描述元識別碼**欄位**資料行。  
  
         例如，在**來源識別碼**欄中，選取`ContactID`旁`ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID`類型描述元和`ReadItem.salesOrder.SalesOrder.ContactID`類型描述元。  
  
4.  如果您想要建立外部索引無索引鍵關聯中，清除**是外部索引鍵關聯**核取方塊。  
  
5.  選擇 [確定]  按鈕。  
  
6.  在 BDC 設計工具中，來源實體和目的地之間會出現一條線代表關聯。  
  
     Visual Studio 關聯巡覽器將方法加入至目的地實體的服務類別與來源實體的服務類別。 如需有關關聯的巡覽方法的詳細資訊，請參閱[支援的作業](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
7.  在來源實體關聯的導覽方法中，加入程式碼會傳回目的地實體的集合。  
  
8.  在目的地實體關聯的導覽方法中，加入程式碼會傳回相關的來源實體。  
  
     關聯的導覽器方法的範例，請參閱[建立實體之間關聯](../sharepoint/creating-an-association-between-entities.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)   
 [如何： 定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  