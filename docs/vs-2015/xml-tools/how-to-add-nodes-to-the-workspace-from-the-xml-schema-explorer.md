---
title: 如何：從 XML 架構瀏覽器將節點加入工作區 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c8fe9d5ba8c096a03de7a9df85945f4aeb4a0a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656349"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>HOW TO：將節點從 XML 結構描述總管加入至工作空間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明如何從 XML 架構瀏覽器將節點加入至[Xml 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。 只要將 XML 結構描述總管中的節點拖曳到 XSD 設計工具檢視上，或者使用 XML 結構描述總管的操作功能表，即可達到此目的。 您也可以加入以 XML 結構描述總管執行搜尋後反白顯示為結果的節點。 如需詳細資訊，請參閱[如何：將架構集合搜尋結果節點新增至工作區](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)。

> [!NOTE]
> 只有全域節點可以加入至[XML 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。

### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>透過 XML 總管操作功能表加入節點

1. 請依照[如何：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 以滑鼠右鍵按一下 XSD 總管中的 `PurchaseOrderType` 節點。 選取 [**在圖表視圖中顯示]** 。

     `purchaseOrderType` 節點會出現在圖表檢視的設計介面上。

### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>將節點拖放至檢視上

1. 以滑鼠右鍵按一下圖表檢視中的 `PurchaseOrderType` 節點。 選取 [**在 XML 架構瀏覽器中顯示**]。

     該節點會在 XML 結構描述總管中反白顯示。

2. 以滑鼠右鍵按一下 XML 架構瀏覽器中的 [`PurchaseOrderType`] 節點，然後選取 [**顯示所有參考**]。

     `purchaseOrder` 節點會反白顯示。

3. 將 `purchaseOrder` 節點拖曳到圖表檢視上。

     在圖表檢視的設計介面上，`purchaseOrder` 節點和 `PurchaseOrderType` 節點會相互並排顯示。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>使用結構描述總管的搜尋功能加入節點

1. 在 [ [XML Explorer](../xml-tools/xml-schema-explorer.md) ] 工具列的 [搜尋] 文字方塊中輸入 "purchaseOrder"，然後按一下 [搜尋] 按鈕。

     ![XML 架構瀏覽器關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     搜尋結果會在 XML 結構描述總管中反白顯示，並以刻度標示在垂直捲軸上。

2. 按一下 [摘要] 結果窗格上的 [**將反白顯示的節點新增至工作區**] 按鈕，將搜尋結果新增至工作區。

     ![XML 架構瀏覽器搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     [@No__t_0] 節點和 [`PurchaseOrderType`] 節點會顯示在[圖形視圖](../xml-tools/graph-view.md)的設計介面上。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="see-also"></a>請參閱
 [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)
