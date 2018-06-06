---
title: HOW TO：將節點從 XML 結構描述總管加入至工作空間
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e1f5821d3a4207d89eb62b9344cff967c73b536
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752049"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>如何： 將節點加入至工作區中，從 XML 結構描述總管

本主題說明如何將節點加入[XML 結構描述設計工具工作空間](../xml-tools/xml-schema-designer-workspace.md)從**XML 結構描述總管**。 這可以藉由拖放節點從**XML 結構描述總管**放至 XSD 設計工具檢視，或使用**XML 結構描述總管的**操作功能表。 您也可以加入會反白顯示所執行的搜尋結果的節點**XML 結構描述總管**。 如需詳細資訊，請參閱[How to： 將結構描述集合搜尋節點加入至工作區](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)。

> [!NOTE]
> 只有全域節點可以加入至[XML 結構描述設計工具工作空間](../xml-tools/xml-schema-designer-workspace.md)。

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>透過 XML 總管操作功能表加入節點

1.  請依照[How to： 建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。

2.  以滑鼠右鍵按一下`PurchaseOrderType`XSD 總管中的節點。 選取**在圖形檢視中顯示**。

     `purchaseOrderType` 節點會出現在圖表檢視的設計介面上。

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>將節點拖放至檢視上

1.  以滑鼠右鍵按一下`PurchaseOrderType`圖表檢視中的節點。 選取**在 XML 結構描述總管中顯示**。

     節點會反白顯示**XML 結構描述總管**。

2.  以滑鼠右鍵按一下`PurchaseOrderType`節點**XML 結構描述總管**選取**顯示所有參考**。

     `purchaseOrder` 節點會反白顯示。

3.  將 `purchaseOrder` 節點拖曳到圖表檢視上。

     在圖表檢視的設計介面上，`purchaseOrder` 節點和 `PurchaseOrderType` 節點會相互並排顯示。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>使用結構描述總管的搜尋功能加入節點

1.  在搜尋文字方塊中輸入"purchaseOrder" [XML 總管](../xml-tools/xml-schema-explorer.md)工具列，並按一下 [搜尋] 按鈕。

     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif)

     搜尋結果會以反白顯示**XML 結構描述總管**並以刻度標示在垂直捲軸上。

2.  按一下搜尋結果加入工作區**反白顯示的節點新增到工作區**摘要結果面板上的按鈕。

     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`節點和`PurchaseOrderType`節點會相互並排顯示的設計介面上[圖表檢視](../xml-tools/graph-view.md)。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="see-also"></a>另請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)