---
title: 搜尋結構描述設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6328e3febf8d7279ad0a4bcac3ca4be54eb42c20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="searching-the-schema-set"></a>搜尋結構描述集
XML 結構描述總管可讓您以下列方式搜尋結構描述集：  
  
-   關鍵字搜尋。  
  
-   結構描述特有的搜尋。  
  
## <a name="keyword-search"></a>關鍵字搜尋  
 您輸入的子字串，執行關鍵字搜尋**搜尋 SchemaSet** XML 結構描述總管工具列的文字方塊。  
  
 ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML 結構描述總管會搜尋下列結構描述集：  
  
-   符合指定之關鍵字的任何 `name` 或 `ref` 屬性。 這項功能可讓您依名稱尋找項目、屬性和型別等。  
  
-   include 陳述式的 `schemaLocation` 屬性。  
  
-   import 陳述式的 `namespace` 屬性。  
  
## <a name="schema-specific-search"></a>結構描述的特定搜尋  
 XML 結構描述總管也包含一些內建的搜尋，可讓您使用 XML 結構描述總管的操作功能表進行存取。 如需可用的內容功能表的詳細資訊，請參閱[操作功能表](../xml-tools/context-menus-xml-schema-explorer.md)。 您也可以從開始檢視上; 執行結構描述特定搜尋如需詳細資訊，請參閱中的 < 結構描述設定的詳細資料 > 一節[開始檢視](../xml-tools/start-view.md)主題。  
  
## <a name="displaying-and-navigating-search-results"></a>顯示和導覽搜尋結果  
 搜尋完成後，摘要結果面板會加入含搜尋結果的工具列。 搜尋結果也會在 XML 結構描述總管中反白顯示並以刻度標示在垂直捲軸上。 您可以使用瀏覽搜尋結果**移至下一個搜尋結果**和**移至前一個搜尋結果**; 使用鍵盤按鍵的 XML 結構描述總管工具列的摘要結果面板上的按鈕F3 和 Shift + F3或按一下捲軸的刻度標記。  
  
 您可以將搜尋結果加入工作區依序按一下**反白顯示的節點新增到工作區**摘要結果面板上的按鈕。  
  
 ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>清除搜尋結果  
 若要清除搜尋結果，請按一下**x** XML 結構描述總管搜尋工具列的摘要結果面板上的按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)