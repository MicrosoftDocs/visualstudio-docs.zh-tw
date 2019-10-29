---
title: 如何：將實體加入至模型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1a7ec1eab5cdcf2e415a4803c51c9da91be29c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985248"
---
# <a name="how-to-add-an-entity-to-a-model"></a>如何：將實體加入至模型
  若要建立實體，請將 [Visual Studio 工具箱] 中的實體控制項加入至 [商務資料連線（BDC）] 設計**工具**。

### <a name="to-add-an-entity-to-the-model"></a>若要將實體加入至模型

1. 建立 BDC 專案，或開啟現有的 BDC 專案。 如需詳細資訊，請參閱[建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

2. 在 [**工具箱**] 的 [ **BusinessDataCatalog** ] 群組中，將 [**實體**] 控制項加入至設計工具。

     新的實體會出現在設計工具上。 Visual Studio 會將 `<Entity>` 元素加入至專案中 BDC 模型檔案的 XML。 如需實體元素之屬性的詳細資訊，請參閱[entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14))。

3. 在設計工具上，開啟實體的快捷方式功能表，選擇 [**新增**]，然後選擇 [**識別碼**]。

     實體上會出現新的識別碼。

    > [!NOTE]
    > 您可以在 [**屬性**] 視窗中變更實體的名稱和識別碼。

4. 在類別中定義實體的欄位。 您可以將新類別加入至專案，或使用使用其他工具（例如物件關聯式設計工具（O/R 設計工具）所建立的現有類別。 下列範例顯示名為 Contact 的實體類別。

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>請參閱
- [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：新增更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [如何：加入 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：加入特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)
