---
title: 如何：加入更新程式方法 |Microsoft Docs
description: 瞭解如何藉由新增更新程式方法，讓使用者更新 SharePoint 外部清單中的商務資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fff7083305d4e19495b81525c8a67a42c5ff6c70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967497"
---
# <a name="how-to-add-an-updater-method"></a>如何：加入更新程式方法
  您可以藉由 *建立更新程式方法，* 讓使用者更新 SharePoint 外部清單中的商務資料。 如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-create-an-updater-method"></a>建立更新程式方法

1. 在 BDC 設計工具上，選擇實體。

2. 在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **BDC 方法詳細資料**]。

    [BDC 方法詳細資料] 視窗隨即開啟。 如需此視窗的詳細資訊，請參閱 [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)。

3. 在 [ **加入方法** ] 清單中，選擇 [ **建立更新程式方法**]。

    Visual Studio 將下列元素加入至模型。 這些專案會出現在 [BDC 方法詳細資料] 視窗中。

   - 名為 **Update** 的方法。

   - 方法的輸入參數。

   - 參數的類型描述元。 根據預設，Visual Studio 會使用您為搜尋工具方法定義的實體類型描述元 (例如： Contact) 。

   - 方法的方法實例。

     如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

   > [!NOTE]
   > 如果實體類型的識別碼代表資料庫資料表中未自動產生的欄位，請將 [ **更新前欄位** ] 屬性設定為 [ **True**]。

4. 在 **方案總管** 中，開啟針對實體所產生之服務程式代碼檔案的快捷方式功能表，然後選擇 [ **View code**]。

    Entity service 程式碼檔案會在程式 **代碼編輯器** 中開啟。 如需有關該檔案的詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

5. 將程式碼新增至 Update 方法以更新資料。 下列範例會更新 AdventureWorks 範例資料庫中的連絡人資訊，以進行 SQL Server。

   > [!NOTE]
   > 將欄位的值取代為 `ServerName` 您伺服器的名稱。

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>另請參閱
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
