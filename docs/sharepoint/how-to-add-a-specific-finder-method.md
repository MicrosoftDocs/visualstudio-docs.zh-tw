---
title: "如何： 加入特定搜尋方法 |Microsoft 文件"
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
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6a5dbff1d4a4c739ce8ecab0807e2d74c62f999e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-specific-finder-method"></a>如何：加入特定搜尋方法
  您可以藉由建立傳回單一實體執行個體*特定搜尋工具*方法。 在使用者選擇商務資料 web 組件或外部的清單中的實體時，商務資料連線 (BDC) 服務會執行特定搜尋工具方法。 如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-specific-finder-method"></a>若要建立特定搜尋工具方法  
  
1.  在 BDC 設計工具中，選擇 [實體]。  
  
     如需如何將實體加入至 BDC 設計工具，Visual Studio 中的資訊，請參閱[How to： 將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2.  在功能表列上選擇 **檢視**，**其他視窗**， **BDC 方法詳細資料**。  
  
     **BDC 方法詳細資料**視窗隨即開啟。 如需該視窗的詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在**將方法加入**清單中，選擇**建立特定搜尋方法**。  
  
     Visual Studio 會將下列項目加入至模型。 這些項目會出現在**BDC 方法詳細資料**視窗。  
  
    -   方法。  
  
    -   方法的輸入的參數。  
  
    -   方法的傳回參數。  
  
    -   針對每個參數類型描述元。  
  
    -   方法執行個體方法。  
  
     如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  開啟 Visual Studio**屬性**視窗。  
  
5.  將傳回參數的類型描述元設定為實體類型描述元。 如需如何建立實體型別描述項資訊，請參閱[如何： 定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
    > [!NOTE]  
    >  您沒有執行此步驟，如果您已經加入搜尋方法的實體。 Visual Studio 會使用您在搜尋工具方法中定義的類型描述元。  
  
    > [!NOTE]  
    >  如果實體類型的識別項欄位代表自動產生的資料庫資料表中的欄位，設定**唯讀**屬性的識別項欄位**True**。  
  
6.  在**方法詳細資料**視窗中，選擇方法的方法執行個體。  
  
7.  在**屬性 視窗**，將**傳回參數名稱**屬性設為方法的傳回參數的名稱。 如需方法執行個體屬性的詳細資訊，請參閱[MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
8.  在**方案總管 中**，開啟實體的已產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。  
  
     實體服務程式碼檔隨即開啟 程式碼編輯器。 如需有關實體服務程式碼檔的詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
9. 程式碼加入特定搜尋工具方法。 這個程式碼會執行下列工作：  
  
    -   從資料來源擷取記錄。  
  
    -   傳回實體，BDC 服務。  
  
     下列範例會傳回連絡人從 AdventureWorks 範例資料庫的 SQL Server。  
  
    > [!NOTE]  
    >  取代的值`ServerName`欄位與您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  