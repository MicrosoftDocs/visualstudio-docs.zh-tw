---
title: 如何：加入刪除者方法 |Microsoft Docs
description: 瞭解如何在 Visual Studio 的 BDC 設計工具中加入刪除者方法，讓終端使用者可以從 SharePoint 網站上的外部清單中刪除資料記錄。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a5e41fbb4f70bd3f5ae2db72b630ae6e524d3def
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915436"
---
# <a name="how-to-add-a-deleter-method"></a>如何：加入刪除者方法
  您可以藉由將刪除者方法加入至模型，讓終端使用者可以從 SharePoint 網站上的外部清單中刪除資料記錄。 如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-create-a-deleter-method"></a>若要建立刪除者方法

1. 在 **BDC 設計** 工具上，選擇實體。

2. 在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **BDC 方法詳細資料**]。

    [ **BDC 方法詳細資料** ] 視窗隨即開啟。 如需此視窗的詳細資訊，請參閱 [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)。

3. 在 [ **加入方法** ] 清單中，選擇 [ **建立刪除者方法**]。

    Visual Studio 將下列元素加入至模型。 這些專案會出現在 [ **BDC 方法詳細資料** ] 視窗中。

   - 名為 **Delete** 的方法。

   - 方法的輸入參數。

   - 參數的類型描述元。

   - 方法的方法實例。

     如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

4. 在 **方案總管** 中，開啟針對實體所產生之服務程式代碼檔案的快捷方式功能表，然後選擇 [ **View code**]。

    Entity service 程式碼檔案會在程式碼編輯器中開啟。 如需實體服務程式代碼檔案的詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

5. 將程式碼加入至刪除者方法以刪除記錄。 下列範例會使用 SQL Server 的 AdventureWorks 範例資料庫，從銷售訂單中刪除明細專案。

   > [!NOTE]
   > 此範例中的方法會使用兩個輸入參數。

   > [!NOTE]
   > 將欄位的值取代為 `ServerName` 您伺服器的名稱。

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>另請參閱
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
