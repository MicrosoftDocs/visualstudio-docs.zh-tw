---
title: HOW TO：新增更新者方法 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26b917b04314c99ba6575842b8e102113b22b469
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596955"
---
# <a name="how-to-add-an-updater-method"></a>HOW TO：新增更新者方法
  您可以讓使用者藉由更新 SharePoint 外部清單中的商務資料*Updater*方法。 如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-create-an-updater-method"></a>若要建立 Updater 方法

1. 在 BDC 設計工具中，選擇 [實體]。

2. 在功能表列上選擇 **檢視** > **其他 Windows** > **BDC 方法詳細資料**。

    [BDC 方法詳細資料] 視窗隨即開啟。 如需有關此視窗的詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。

3. 在 **將方法加入**清單中，選擇**建立 Updater 方法**。

    Visual Studio 會將下列項目加入至模型。 這些項目會出現在 [BDC 方法詳細資料] 視窗中。

   - 方法，稱為**更新**。

   - 方法的輸入的參數。

   - 參數型別描述項。 根據預設，Visual Studio 會使用您所定義的實體型別描述元的搜尋工具方法 (例如：請連絡）。

   - 方法執行個體方法。

     如需詳細資訊，請參閱 <<c0> [ 設計 business data connectivity 模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

   > [!NOTE]
   >  如果實體類型的識別項表示不會自動產生的資料庫資料表中的欄位，設定**預先更新者欄位**屬性設 **，則為 True**。

4. 在 **方案總管**，開啟實體時，所產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。

    實體服務程式碼檔案中開啟**程式碼編輯器**。 如需有關該檔案的詳細資訊，請參閱[建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

5. 加入程式碼來更新資料的 Update 方法。 下列範例會更新為 SQL Server 的 AdventureWorks 範例資料庫中的連絡人資訊。

   > [!NOTE]
   >  值取代`ServerName`欄位與您伺服器的名稱。

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>另請參閱
- [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：新增更新者方法](../sharepoint/how-to-add-an-updater-method.md)
- [如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)
- [如何：新增參數至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)
