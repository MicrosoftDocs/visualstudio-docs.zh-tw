---
title: 如何： 新增 Specific Finder 方法 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8005728d29c38e32d55f01e42d2666c69112b3f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886483"
---
# <a name="how-to-add-a-specific-finder-method"></a>如何： 加入特定搜尋方法
  您可以藉由建立傳回單一實體執行個體*特定的 Finder*方法。 當使用者選擇商務資料 web 組件或外部的清單中的實體時，商務資料連接 (BDC) 服務會執行特定搜尋工具方法。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-specific-finder-method"></a>若要建立特定搜尋方法
  
1. 在  **BDC 設計工具**，選擇實體。  
  
    如需如何將實體新增至**BDC 設計工具**在 Visual Studio 中，請參閱[如何： 將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2. 在功能表列上選擇 **檢視** > **其他 Windows**， **BDC 方法詳細資料**。  
  
    **BDC 方法詳細資料**視窗隨即開啟。 如需該視窗的詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3. 在 **將方法加入**清單中，選擇**建立特定搜尋方法**。  
  
    Visual Studio 會將下列項目加入至模型。 這些項目會出現在**BDC 方法詳細資料**視窗。  
  
   - 方法。  
  
   - 方法的輸入的參數。  
  
   - 方法的傳回參數。  
  
   - 每個參數的型別描述項。  
  
   - 方法執行個體方法。  
  
     如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4. 開啟 Visual Studio**屬性**視窗。  
  
5. 設定傳回參數的類型描述元做為實體型別描述元。 如需有關如何建立實體型別描述元的資訊，請參閱 <<c0> [ 如何： 定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
   > [!NOTE]  
   >  您不需要執行此步驟中，如果您已加入實體中的搜尋工具方法。 Visual Studio 會使用您在搜尋工具方法中定義的類型描述元。  
  
   > [!NOTE]  
   >  如果實體類型的識別項欄位代表自動產生的資料庫資料表中的欄位，設定**唯讀**屬性的識別項欄位 **，則為 True**。  
  
6. 在 [**方法詳細資料**] 視窗中，選擇此方法的方法執行個體。  
  
7. 在 [**屬性] 視窗**，將**傳回參數名稱**屬性方法的傳回參數的名稱。 如需有關方法的執行個體屬性的詳細資訊，請參閱[MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
8. 在 **方案總管**，開啟實體時，所產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。  
  
    實體服務程式碼檔會開啟在程式碼編輯器。 如需有關實體服務程式碼檔的詳細資訊，請參閱[建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
9. 您可以將程式碼加入特定搜尋工具方法。 這個程式碼會執行下列工作：  
  
   - 從資料來源中擷取一筆記錄。  
  
   - BDC 服務傳回的實體。  
  
     下列範例會傳回 SQL Server 的 AdventureWorks 範例資料庫中的連絡人。  
  
     > [!NOTE]  
     >  值取代`ServerName`欄位與您伺服器的名稱。  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>另請參閱
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
