---
title: HOW TO：將節點從 XML 結構描述總管新增至工作區
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 699f57829e2f7d9bfd7a8841f5b1c82de5b9c7f7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012101"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>HOW TO：將節點從 XML 結構描述總管加入至工作區

本主題說明如何將節點加入到[XML 結構描述設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)從**XML 結構描述總管**。 這可以藉由拖放節點來達成**XML 結構描述總管**拖曳至 XSD 設計工具檢視，或使用**XML 結構描述總管的**操作功能表。 您也可以加入會反白顯示所執行的搜尋結果的節點**XML 結構描述總管**。 如需詳細資訊，請參閱[＜How to：將結構描述集合搜尋節點加入工作空間](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)。

> [!NOTE]
> 只有全域節點可以加入至[XML 結構描述設計工具工作空間](../xml-tools/xml-schema-designer-workspace.md)。

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>若要新增節點能夠透過 XML 總管操作功能表

1.  請依照下列中的步驟[How to:建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。

2.  以滑鼠右鍵按一下`PurchaseOrderType`XSD 總管中的節點。 選取 **在圖形檢視中顯示**。

     `purchaseOrderType` 節點會出現在圖表檢視的設計介面上。

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>將節點拖放至檢視上

1.  以滑鼠右鍵按一下`PurchaseOrderType`圖表檢視中的節點。 選取 **在 XML 結構描述總管中顯示**。

     中的節點會反白顯示**XML 結構描述總管**。

2.  以滑鼠右鍵按一下`PurchaseOrderType`中的節點**XML 結構描述總管**，然後選取**顯示所有參考**。

     `purchaseOrder` 節點會反白顯示。

3.  將 `purchaseOrder` 節點拖曳到圖表檢視上。

     在圖表檢視的設計介面上，`purchaseOrder` 節點和 `PurchaseOrderType` 節點會相互並排顯示。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>使用結構描述總管的搜尋功能加入節點

1.  在搜尋文字方塊中輸入"purchaseOrder" [XML 總管](../xml-tools/xml-schema-explorer.md)工具列，然後按一下 [搜尋] 按鈕。

     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif)

     搜尋結果會以反白顯示**XML 結構描述總管**和以垂直捲軸的刻度標示。

2.  新增至工作區的搜尋結果中，依序按一下**反白顯示的節點加入工作區**摘要結果面板上的按鈕。

     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`節點和`PurchaseOrderType`節點會相互並排顯示的設計介面上[圖表檢視](../xml-tools/graph-view.md)。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="see-also"></a>另請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)