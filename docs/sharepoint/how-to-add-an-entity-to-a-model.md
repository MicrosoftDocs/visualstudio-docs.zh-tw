---
title: 如何：將實體加入至模型 |Microsoft Docs
description: 將實體控制項從 Visual Studio 工具箱加入至商務資料連線 (BDC) 設計工具，以將實體新增至模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94d34e6a623438cd0e2d63d74ee2321841a0582a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216770"
---
# <a name="how-to-add-an-entity-to-a-model"></a>如何：將實體加入至模型
  若要建立實體，請將 Visual Studio 工具箱中的實體控制項加入至 [商務資料連線 (BDC) 設計 **工具** ]。

### <a name="to-add-an-entity-to-the-model"></a>若要將實體加入至模型

1. 建立 BDC 專案，或開啟現有的 BDC 專案。 如需詳細資訊，請參閱 [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

2. 在 [ **工具箱**] 中，將 [ **BusinessDataCatalog** ] 群組中的 [ **實體** ] 控制項加入至設計工具。

     新的實體會出現在設計工具上。 Visual Studio 將 `<Entity>` 專案加入至專案中 BDC 模型檔案的 XML。 如需實體元素屬性的詳細資訊，請參閱 [實體](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14))。

3. 在設計工具中，開啟實體的快捷方式功能表，選擇 [ **加入**]，然後選擇 [ **識別碼**]。

     新的識別碼會出現在實體上。

    > [!NOTE]
    > 您可以在 [ **屬性** ] 視窗中變更實體的名稱和識別碼。

4. 在類別中定義實體的欄位。 您可以將新類別加入至專案，或使用其他工具（例如物件關聯式設計工具 (O/R 設計工具) ）所建立的現有類別。 下列範例顯示名為 Contact 的實體類別。

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs" id="Snippet1":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb" id="Snippet1":::

## <a name="see-also"></a>另請參閱
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)
