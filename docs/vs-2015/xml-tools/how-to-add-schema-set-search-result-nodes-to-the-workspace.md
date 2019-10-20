---
title: 如何：將架構集合搜尋結果節點新增至工作區 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b34be331ad3ec67e2c3bd8d9ecc500cd256b1b09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666544"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>HOW TO：將結構描述集合搜尋節點加入工作空間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明如何將 XML 結構描述總管中反白顯示為關鍵字搜尋結果的節點加入工作空間。

> [!NOTE]
> 只有全域節點可以新增至[工作區](../xml-tools/xml-schema-designer-workspace.md)。

 這個範例會使用範例[採購單架構](../xml-tools/sample-xsd-file-purchase-order-schema.md)。

### <a name="to-add-schema-set-result-nodes"></a>加入結構描述集合結果節點

1. 請依照[如何：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 在 [ [XML Explorer](../xml-tools/xml-schema-explorer.md) ] 工具列的 [搜尋] 文字方塊中輸入 "purchaseOrder"，然後按一下 [搜尋] 按鈕。

     ![XML 架構瀏覽器關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     搜尋結果會在 XML 結構描述總管中反白顯示，並以刻度標示在垂直捲軸上。

3. 按一下 [摘要] 結果窗格上的 [**將反白顯示的節點新增至工作區**] 按鈕，將搜尋結果新增至工作區。

     ![XML 架構瀏覽器搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     [@No__t_0] 節點和 [`PurchaseOrderType`] 節點會顯示在[圖形視圖](../xml-tools/graph-view.md)的設計介面上。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。
