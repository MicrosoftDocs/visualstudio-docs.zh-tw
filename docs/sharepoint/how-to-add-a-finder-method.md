---
title: 如何： 新增搜尋方法 |Microsoft Docs
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
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 597d1e706ad75ba6ec16b958c94b5ba9d8e97760
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836225"
---
# <a name="how-to-add-a-finder-method"></a>如何： 新增搜尋方法
  若要啟用網頁組件或清單中顯示的實體清單的商務資料連接 (BDC) 服務，您必須建立*Finder*方法。 搜尋方法是特殊的方法可傳回實體執行個體的集合。 如需詳細資訊，請參閱 <<c0> [ 設計 Business Data Connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-finder-method"></a>若要建立搜尋方法  
  
1. 在  **BDC 設計工具**，選擇實體。  
  
    如需詳細資訊，請參閱 <<c0> [ 如何： 將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2. 在功能表列上選擇 **檢視** > **其他 Windows** > **BDC 方法詳細資料**。  
  
    **BDC 方法詳細資料**視窗隨即開啟。 如需詳細資訊**BDC 方法詳細資料** 視窗中，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3. 在 **將方法加入**清單中，選擇**建立搜尋方法**。  
  
    Visual Studio 會新增方法，是傳回參數和型別描述項。  
  
4. 設定為實體集合類型描述元的型別描述項。 如需如何建立實體集合類型描述元的詳細資訊，請參閱[如何： 定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
   > [!NOTE]  
   >  您沒有執行此步驟中，如果您已加入實體中的特定搜尋工具方法。 Visual Studio 會使用您在特定搜尋工具方法中定義的類型描述元。  
  
5. 在 **方案總管**，開啟實體時，所產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。 如需有關服務的程式碼檔的詳細資訊，請參閱[建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
6. 加入搜尋方法的程式碼。 這個程式碼會執行下列工作：  
  
   - 從資料來源擷取資料。  
  
   - BDC 服務傳回實體的清單。  
  
     下列範例會傳回的集合`Contact`適用於 SQL Server 使用 AdventureWorks 範例資料庫中的資料的實體。  
  
   > [!NOTE]  
   >  值取代`ServerName`欄位與您伺服器的名稱。  
  
    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>另請參閱
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何： 定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  
