---
title: 如何：新增特定搜尋工具方法 |Microsoft Docs
description: 藉由新增 Finder 方法來取得實體實例。 當使用者挑選商務資料網頁元件或外部清單中的實體時，BDC 服務會呼叫方法。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 237cd28bffece4517e80b979602ac8d2ed357aa2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882683"
---
# <a name="how-to-add-a-specific-finder-method"></a>如何：新增特定搜尋工具方法
  您可以藉由建立特定的搜尋 *工具* 方法來傳回單一實體實例。 當使用者選擇商務資料網頁元件或外部清單中的實體時， (BDC) 服務的商務資料連線會執行特定的搜尋工具方法。 如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-create-a-specific-finder-method"></a>若要建立特定的搜尋工具方法

1. 在 **BDC 設計** 工具上，選擇實體。

    如需如何在 Visual Studio 中將實體新增至 **BDC 設計** 工具的詳細資訊，請參閱 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。

2. 在功能表列上，選擇 [**視圖**  >  **其他視窗**]、[ **BDC 方法詳細資料**]。

    [ **BDC 方法詳細資料** ] 視窗隨即開啟。 如需該視窗的詳細資訊，請參閱 [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)。

3. 在 [ **加入方法** ] 清單中，選擇 [ **建立特定的搜尋工具方法**]。

    Visual Studio 將下列元素加入至模型。 這些專案會出現在 [ **BDC 方法詳細資料** ] 視窗中。

   - 方法。

   - 方法的輸入參數。

   - 方法的傳回參數。

   - 每個參數的類型描述元。

   - 方法的方法實例。

     如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

4. 開啟 [Visual Studio **屬性** ] 視窗。

5. 將 return 參數的類型描述元設定為實體類型描述元。 如需如何建立實體類型描述元的詳細資訊，請參閱 [如何：定義參數的類型描述](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)元。

   > [!NOTE]
   > 如果您已將 Finder 方法加入至實體，就不需要執行此步驟。 Visual Studio 會使用您在搜尋工具方法中定義的型別描述項。

   > [!NOTE]
   > 如果實體類型的 [識別碼] 欄位代表自動產生之資料庫資料表中的欄位，請將 [識別碼] 欄位的 [ **唯讀** ] 屬性設定為 [ **True**]。

6. 在 [ **方法詳細資料** ] 視窗中，選擇方法的方法實例。

7. 在 [ **屬性] 視窗** 中，將 [傳回 **參數名稱** ] 屬性設定為方法的傳回參數名稱。 如需方法實例屬性的詳細資訊，請參閱 [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))。

8. 在 **方案總管** 中，開啟針對實體所產生之服務程式代碼檔案的快捷方式功能表，然後選擇 [ **View code**]。

    Entity service 程式碼檔案會在程式碼編輯器中開啟。 如需實體服務程式代碼檔案的詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

9. 將程式碼新增至特定的搜尋工具方法。 此程式碼會執行下列工作：

   - 從資料來源抓取記錄。

   - 將實體傳回到 BDC 服務。

     下列範例會從 AdventureWorks 範例資料庫傳回 SQL Server 的連絡人。

     > [!NOTE]
     > 將欄位的值取代為 `ServerName` 您伺服器的名稱。

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>另請參閱
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
