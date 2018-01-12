---
title: "如何： 加入建立者方法 |Microsoft 文件"
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
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 423992400abfb3f18c3f3d530be1d837c50948d6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-creator-method"></a>如何：加入建立者方法
  建立者方法會將新資料加入至資料來源的實體。 商務資料連線 (BDC) 服務會呼叫這個方法，當使用者選擇**新項目**清單中的模型為基礎的功能區上的按鈕。 如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-add-a-creator-method"></a>若要加入建立者方法  
  
1.  在 BDC 設計工具中，選擇 [實體]。  
  
2.  在功能表列上選擇 **檢視**，**其他視窗**， **BDC 方法詳細資料**。  
  
     **BDC 方法詳細資料**視窗隨即開啟。 如需該視窗的詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在**將方法加入**清單中，選擇**建立 Creator 方法**。  
  
     Visual Studio 會將下列項目加入至模型，而且這些項目出現在**BDC 方法詳細資料**視窗。  
  
    -   方法，名為**建立**。  
  
    -   方法的輸入的參數。  
  
    -   方法的傳回參數。  
  
    -   輸入參數的描述元。  
  
    -   方法執行個體方法。  
  
     如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  在**方案總管 中**，開啟實體的已產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。  
  
     實體服務程式碼檔隨即開啟 程式碼編輯器。 如需有關實體服務程式碼檔的詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5.  將資料加入至資料來源的建立者方法中加入程式碼。 下列範例會將 SQL Server 的 AdventureWorks 範例資料庫的連絡人。  
  
    > [!NOTE]  
    >  取代的值`ServerName`欄位與您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  