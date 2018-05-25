---
title: 將 XML 結構描述集合搜尋節點加入至工作區
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6629aef7549a78f7cfdb73bb6d7ee0be3ac7412
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>如何： 將結構描述集合搜尋節點加入至工作區

本主題說明如何將以反白顯示的節點加入**XML 結構描述總管**做為工作區中的關鍵字搜尋的結果。

> [!NOTE]
> 只有全域節點可以加入至[工作區](../xml-tools/xml-schema-designer-workspace.md)。


 此範例使用範例[採購單結構描述](../xml-tools/sample-xsd-file-purchase-order-schema.md)。

## <a name="to-add-schema-set-result-nodes"></a>加入結構描述集合結果節點

1.  請依照[How to： 建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。

2.  在搜尋文字方塊中輸入"purchaseOrder" [XML 總管](../xml-tools/xml-schema-explorer.md)工具列，並按一下 [搜尋] 按鈕。

     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     搜尋結果會以反白顯示**XML 結構描述總管**並以刻度標示在垂直捲軸上。

3.  按一下搜尋結果加入工作區**反白顯示的節點新增到工作區**摘要結果面板上的按鈕。

     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     `purchaseOrder`節點和`PurchaseOrderType`節點會相互並排顯示的設計介面上[圖表檢視](../xml-tools/graph-view.md)。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。