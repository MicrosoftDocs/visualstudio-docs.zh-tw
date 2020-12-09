---
title: 如何：加入 Finder 方法 |Microsoft Docs
description: 在 Visual Studio 中加入 Finder 方法，可讓商務資料連線 (BDC) 服務，以顯示 SharePoint web 元件或清單中的實體清單。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b7e2bb74278194878ed4496c12c918707cdc1e6e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915085"
---
# <a name="how-to-add-a-finder-method"></a>如何：加入搜尋工具方法
  若要啟用商務資料連線 (BDC) 服務來顯示 web 元件或清單中的實體清單，您必須建立 *Finder* 方法。 Finder 方法是傳回實體實例集合的特殊方法。 如需詳細資訊，請參閱 [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)。

### <a name="to-create-a-finder-method"></a>若要建立 Finder 方法

1. 在 **BDC 設計** 工具上，選擇實體。

    如需詳細資訊，請參閱 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。

2. 在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **BDC 方法詳細資料**]。

    [ **BDC 方法詳細資料** ] 視窗隨即開啟。 如需 [ **Bdc 方法詳細資料** ] 視窗的詳細資訊，請參閱 [bdc 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)。

3. 在 [ **加入方法** ] 清單中，選擇 [ **建立 Finder 方法**]。

    Visual Studio 加入方法、傳回參數和類型描述元。

4. 將類型描述元設定為實體集合類型描述元。 如需如何建立實體集合類型描述項的詳細資訊，請參閱 [如何：定義參數的類型描述](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)元。

   > [!NOTE]
   > 如果您已將特定 Finder 方法加入至實體，就不需要執行此步驟。 Visual Studio 會使用您在特定搜尋工具方法中定義的型別描述項。

5. 在 **方案總管** 中，開啟針對實體所產生之服務程式代碼檔案的快捷方式功能表，然後選擇 [ **View code**]。 如需服務程式代碼檔案的詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

6. 將程式碼新增至搜尋工具方法。 此程式碼會執行下列工作：

   - 從資料來源提取資料。

   - 傳回 BDC 服務的實體清單。

     下列範例會 `Contact` 使用 SQL Server 的 AdventureWorks 範例資料庫中的資料，傳回實體集合。

   > [!NOTE]
   > 將欄位的值取代為 `ServerName` 您伺服器的名稱。

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>另請參閱
- [BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：新增特定搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)
