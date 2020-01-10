---
title: 將 XML 架構集合搜尋結果節點新增至工作區
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1bdb21c2b9ce3f6a79bf24738c84fcb3064c24cb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592785"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>如何：將架構集合搜尋結果節點新增至工作區

本主題說明如何加入在**XML 架構瀏覽器**中反白顯示的節點，做為工作區中關鍵字搜尋的結果。

> [!NOTE]
> 只有全域節點可以新增至[工作區](../xml-tools/xml-schema-designer-workspace.md)。

這個範例會使用範例[採購單架構](../xml-tools/sample-xsd-file-purchase-order-schema.md)。

## <a name="to-add-schema-set-result-nodes"></a>加入結構描述集合結果節點

1. 請依照[如何：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 在 [ [XML Explorer](../xml-tools/xml-schema-explorer.md) ] 工具列的 [搜尋] 文字方塊中輸入 "purchaseOrder"，然後按一下 [搜尋] 按鈕。

     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif)

     搜尋結果會在**XML 架構瀏覽器**中反白顯示，並在垂直捲動條上以刻度標示。

3. 按一下 [摘要] 結果窗格上的 [**將反白顯示的節點新增至工作區**] 按鈕，將搜尋結果新增至工作區。

     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif)

     [`purchaseOrder`] 節點和 [`PurchaseOrderType`] 節點會顯示在[圖形視圖](../xml-tools/graph-view.md)的設計介面上。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。
