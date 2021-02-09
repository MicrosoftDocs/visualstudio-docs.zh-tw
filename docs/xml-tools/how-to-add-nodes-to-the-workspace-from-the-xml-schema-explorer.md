---
title: 從 XML 架構瀏覽器將節點新增至工作區
description: 瞭解如何使用內容功能表或將節點拖放到視圖上，從 XML 架構設計工具將節點加入至 XML 架構設計工具工作區。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f895d29e46556bff8543563841939640c501f84d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879263"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>如何：從 XML 架構瀏覽器將節點加入至工作區

本主題說明如何從 **Xml 架構瀏覽器** 將節點加入至 [xml 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。 將節點從 **XML 架構瀏覽器** 拖曳到 XSD 設計工具視圖，或使用 **XML 架構瀏覽器的** 內容功能表，即可達成此目的。 您也可以加入由於 **XML 架構瀏覽器** 執行搜尋結果而反白顯示的節點。 如需詳細資訊，請參閱 [如何：將架構集合搜尋結果節點新增至工作區](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)。

> [!NOTE]
> 只有全域節點可以加入至 [XML 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>透過 XML Explorer 內容功能表加入節點

1. 遵循 how [to：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟。

2. 以滑鼠右鍵按一下 `PurchaseOrderType` XSD Explorer 中的節點。 選取 [ **在圖形視圖中顯示]**。

     `purchaseOrderType` 節點會出現在圖表檢視的設計介面上。

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>將節點拖放至檢視上

1. 以滑鼠右鍵按一下 `PurchaseOrderType` 圖形視圖中的節點。 選取 [ **在 XML 架構瀏覽器中顯示**]。

     節點會在 **XML 架構瀏覽器** 中反白顯示。

2. 在 `PurchaseOrderType` **XML 架構瀏覽器** 中，以滑鼠右鍵按一下節點，然後選取 [ **顯示所有參考**]。

     `purchaseOrder` 節點會反白顯示。

3. 將 `purchaseOrder` 節點拖曳到圖表檢視上。

     在圖表檢視的設計介面上，`purchaseOrder` 節點和 `PurchaseOrderType` 節點會相互並排顯示。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>使用結構描述總管的搜尋功能加入節點

1. 在 [XML Explorer](../xml-tools/xml-schema-explorer.md) 工具列的 [搜尋] 文字方塊中輸入 "purchaseOrder"，然後按一下 [搜尋] 按鈕。

     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif)

     搜尋結果會在 **XML 架構瀏覽器** 中反白顯示，並在垂直捲動條上以刻度標記。

2. 按一下 [摘要結果] 窗格上的 [ **將反白顯示的節點加入工作區** ]，以將搜尋結果新增至工作區。

     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`節點和 `PurchaseOrderType` 節點會出現在[圖形視圖](../xml-tools/graph-view.md)的設計介面旁。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。

## <a name="see-also"></a>另請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)
