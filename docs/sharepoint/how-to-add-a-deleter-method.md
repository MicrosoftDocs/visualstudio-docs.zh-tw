---
title: HOW TO：新增刪除者方法 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b1ddbd45771637ffcdd2ad1b6d553b8c497982b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924172"
---
# <a name="how-to-add-a-deleter-method"></a>HOW TO：新增刪除者方法
  您可以讓使用者從 SharePoint 網站上的外部清單刪除資料錄，藉由加入模型中的刪除者方法。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-deleter-method"></a>若要建立刪除者方法  
  
1. 在  **BDC 設計工具**，選擇實體。  
  
2. 在功能表列上選擇 **檢視** > **其他 Windows** > **BDC 方法詳細資料**。  
  
    **BDC 方法詳細資料**視窗隨即開啟。 如需有關此視窗的詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3. 在 **將方法加入**清單中，選擇**建立刪除者方法**。  
  
    Visual Studio 會將下列項目加入至模型。 這些項目會出現在**BDC 方法詳細資料**視窗。  
  
   - 名為的方法**刪除**。  
  
   - 方法的輸入的參數。  
  
   - 參數型別描述項。  
  
   - 方法執行個體方法。  
  
     如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4. 在 **方案總管**，開啟實體時，所產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。  
  
    實體服務程式碼檔會開啟在程式碼編輯器。 如需有關實體服務程式碼檔的詳細資訊，請參閱[建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5. 若要刪除記錄的刪除者方法中加入程式碼。 下列範例會刪除從銷售訂單中行項目，使用 AdventureWorks 範例資料庫的 SQL Server。  
  
   > [!NOTE]  
   >  此範例中的方法會使用兩個輸入的參數。  
  
   > [!NOTE]  
   >  值取代`ServerName`欄位與您伺服器的名稱。  
  
    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>另請參閱
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：新增更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：新增參數至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
