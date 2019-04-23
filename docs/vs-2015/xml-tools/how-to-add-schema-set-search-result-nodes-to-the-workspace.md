---
title: HOW TO：結構描述集合搜尋結果節點新增至工作區 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5df4b9c3bdefb6b807850e2b9f58fed8b2fd2a3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670104"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>HOW TO：將結構描述集合搜尋結果節點新增至工作區
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明如何將 XML 結構描述總管中反白顯示為關鍵字搜尋結果的節點加入工作空間。  
  
> [!NOTE]
>  只有全域節點可以加入至[工作區](../xml-tools/xml-schema-designer-workspace.md)。  
  
 此範例使用範例[採購單結構描述](../xml-tools/sample-xsd-file-purchase-order-schema.md)。  
  
### <a name="to-add-schema-set-result-nodes"></a>加入結構描述集合結果節點  
  
1.  請依照下列中的步驟[How to:建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。  
  
2.  在搜尋文字方塊中輸入"purchaseOrder" [XML 總管](../xml-tools/xml-schema-explorer.md)工具列，然後按一下 [搜尋] 按鈕。  
  
     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     搜尋結果會在 XML 結構描述總管中反白顯示，並以刻度標示在垂直捲軸上。  
  
3.  新增至工作區的搜尋結果中，依序按一下**反白顯示的節點加入工作區**摘要結果面板上的按鈕。  
  
     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder`節點和`PurchaseOrderType`節點會相互並排顯示的設計介面上[圖表檢視](../xml-tools/graph-view.md)。 由於兩個節點是相關的 (`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別)，因此兩個節點之間會畫上箭號。
