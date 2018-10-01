---
title: 搜尋結構描述集合 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6ce05cbaf203649ce62d13285f7304c04be6497
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488407"
---
# <a name="searching-the-schema-set"></a>搜尋結構描述集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[搜尋結構描述集](https://docs.microsoft.com/visualstudio/xml-tools/searching-the-schema-set)。  
  
  
XML 結構描述總管可讓您以下列方式搜尋結構描述集：  
  
-   關鍵字搜尋。  
  
-   結構描述特有的搜尋。  
  
## <a name="keyword-search"></a>關鍵字搜尋  
 輸入中的子字串執行關鍵字搜尋**搜尋 SchemaSet** XML 結構描述總管工具列的 [文字] 方塊。  
  
 ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML 結構描述總管會搜尋下列結構描述集：  
  
-   符合指定之關鍵字的任何 `name` 或 `ref` 屬性。 這項功能可讓您依名稱尋找項目、屬性和型別等。  
  
-   include 陳述式的 `schemaLocation` 屬性。  
  
-   import 陳述式的 `namespace` 屬性。  
  
## <a name="schema-specific-search"></a>結構描述的特定搜尋  
 XML 結構描述總管也包含一些內建的搜尋，可讓您使用 XML 結構描述總管的操作功能表進行存取。 如需可用的內容功能表的詳細資訊，請參閱[快顯功能表](../xml-tools/context-menus-xml-schema-explorer.md)。 您也可以從 [啟動] 檢視中，執行結構描述特有的搜尋如需詳細資訊，請參閱中的 < 結構描述設定的詳細資料 > 一節[開始檢視](../xml-tools/start-view.md)主題。  
  
## <a name="displaying-and-navigating-search-results"></a>顯示和導覽搜尋結果  
 搜尋完成後，摘要結果面板會加入含搜尋結果的工具列。 搜尋結果也會在 XML 結構描述總管中反白顯示並以刻度標示在垂直捲軸上。 您可以使用瀏覽搜尋結果**移至下一個搜尋結果**並**移至前一個搜尋結果**; 使用鍵盤按鍵的 XML 結構描述總管工具列中的 [摘要結果] 窗格上的按鈕F3 和 shift+f3或按一下捲軸的刻度標記。  
  
 您可以將搜尋結果加入工作空間，即可**反白顯示的節點加入工作區**摘要結果面板上的按鈕。  
  
 ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>清除搜尋結果  
 若要清除搜尋結果，請按一下**x** XML 結構描述總管搜尋工具列的摘要結果面板上的按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)



