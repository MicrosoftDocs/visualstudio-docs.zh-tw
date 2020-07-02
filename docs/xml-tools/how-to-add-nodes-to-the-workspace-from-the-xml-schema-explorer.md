---
title: 從 XML 架構瀏覽器將節點加入工作區
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 751e291188e6357343936d61d56f07bd86f97eaf
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816393"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>如何：從 XML 架構瀏覽器將節點加入至工作區

本主題說明如何從**Xml 架構瀏覽器**將節點加入至[xml 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。 將節點從**XML 架構流覽**器拖放到 XSD 設計工具視圖，或使用**XML 架構瀏覽器的**內容功能表，即可達成此目的。 您也可以加入因為**XML 架構瀏覽器**所執行的搜尋結果而反白顯示的節點。 如需詳細資訊，請參閱[如何：將架構集合搜尋結果節點新增至工作區](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)。

> [!NOTE]
> 只有全域節點可以加入至[XML 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>透過 XML Explorer 內容功能表加入節點

1. 請依照[如何：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 以滑鼠右鍵按一下 `PurchaseOrderType` XSD Explorer 中的節點。 選取 [**在圖表視圖中顯示]**。

     `purchaseOrderType` 節點會出現在圖表檢視的設計介面上。

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>將節點拖放至檢視上

1. 以滑鼠右鍵按一下 `PurchaseOrderType` 圖形視圖中的節點。 選取 [**在 XML 架構瀏覽器中顯示**]。

     節點會在**XML 架構瀏覽器**中反白顯示。

2. 以滑鼠右鍵按一下 `PurchaseOrderType` **XML 架構瀏覽器**中的節點，然後選取 [**顯示所有參考**]。

     `purchaseOrder` 節點會反白顯示。

3. 將 `purchaseOrder` 節點拖曳到圖表檢視上。

     在圖表檢視的設計介面上，`purchaseOrder` 節點和 `PurchaseOrderType` 節點會相互並排顯示。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>使用結構描述總管的搜尋功能加入節點

1. 在 [ [XML Explorer](../xml-tools/xml-schema-explorer.md) ] 工具列的 [搜尋] 文字方塊中輸入 "purchaseOrder"，然後按一下 [搜尋] 按鈕。

     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif)

     搜尋結果會在**XML 架構瀏覽器**中反白顯示，並在垂直捲動條上以刻度標示。

2. 按一下 [摘要] 結果窗格上的 [**將反白顯示的節點新增至工作區**] 按鈕，將搜尋結果新增至工作區。

     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif)

     在 `purchaseOrder` `PurchaseOrderType` [圖表視圖](../xml-tools/graph-view.md)的設計介面上，節點和節點會彼此旁顯示。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="see-also"></a>另請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)
