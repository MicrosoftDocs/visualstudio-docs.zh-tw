---
title: XML 結構描述集合搜尋結果節點新增至工作區
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba709e90de580aacda2034eca319a419583dac0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783686"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>HOW TO：將結構描述集合搜尋結果節點新增至工作區

本主題說明如何將會以反白顯示的節點加入**XML 結構描述總管**做為工作區中的關鍵字搜尋的結果。

> [!NOTE]
> 只有全域節點可以加入至[工作區](../xml-tools/xml-schema-designer-workspace.md)。

 此範例使用範例[採購單結構描述](../xml-tools/sample-xsd-file-purchase-order-schema.md)。

## <a name="to-add-schema-set-result-nodes"></a>加入結構描述集合結果節點

1. 請依照下列中的步驟[How to:建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。

2. 在搜尋文字方塊中輸入"purchaseOrder" [XML 總管](../xml-tools/xml-schema-explorer.md)工具列，然後按一下 [搜尋] 按鈕。

     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif)

     搜尋結果會以反白顯示**XML 結構描述總管**和以垂直捲軸的刻度標示。

3. 新增至工作區的搜尋結果中，依序按一下**反白顯示的節點加入工作區**摘要結果面板上的按鈕。

     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`節點和`PurchaseOrderType`節點會相互並排顯示的設計介面上[圖表檢視](../xml-tools/graph-view.md)。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。