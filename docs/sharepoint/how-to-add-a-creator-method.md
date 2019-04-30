---
title: HOW TO：新增建立者方法 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38312384c3e6ce51aa1b5b0b16df378286fc58b0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443577"
---
# <a name="how-to-add-a-creator-method"></a>HOW TO：新增建立者方法
  建立者方法會將新資料加入至實體的資料來源。 商務資料連接 (BDC) 服務會呼叫這個方法，當使用者選擇**新的項目**按鈕**功能區**的模型為基礎的清單。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-add-a-creator-method"></a>若要加入建立者方法

1. 在  **BDC 設計工具**，選擇實體。

2. 在功能表列上選擇 **檢視** > **其他 Windows** >**BDC 方法詳細資料**。

    **BDC 方法詳細資料**視窗隨即開啟。 如需該視窗的詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。

3. 在 **將方法加入**清單中，選擇**建立建立者方法**。

    Visual Studio 會將下列項目加入至模型，而這些項目會出現在**BDC 方法詳細資料**視窗。

   - 名為的方法**建立**。

   - 方法的輸入的參數。

   - 方法的傳回參數。

   - 輸入參數的描述元。

   - 方法執行個體方法。

     如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

4. 在 **方案總管**，開啟實體時，所產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。

    實體服務程式碼檔會開啟在程式碼編輯器。 如需有關實體服務程式碼檔的詳細資訊，請參閱[建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

5. 將資料加入至資料來源的建立者方法中加入程式碼。 下列範例會將 SQL Server 的 AdventureWorks 範例資料庫的連絡人。

   > [!NOTE]
   > 值取代`ServerName`欄位與您伺服器的名稱。

    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]

## <a name="see-also"></a>另請參閱
- [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：新增更新者方法](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：新增參數至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)
