---
title: 搜尋架構集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656163"
---
# <a name="searching-the-schema-set"></a>搜尋結構描述集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 結構描述總管可讓您以下列方式搜尋結構描述集：

- 關鍵字搜尋。

- 結構描述特有的搜尋。

## <a name="keyword-search"></a>關鍵字搜尋
 您可以在 XML 架構瀏覽器工具列的 [**搜尋 SchemaSet** ] 文字方塊中輸入子字串，以執行關鍵字搜尋。

 ![XML 架構瀏覽器關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 XML 結構描述總管會搜尋下列結構描述集：

- 符合指定之關鍵字的任何 `name` 或 `ref` 屬性。 這項功能可讓您依名稱尋找項目、屬性和型別等。

- include 陳述式的 `schemaLocation` 屬性。

- import 陳述式的 `namespace` 屬性。

## <a name="schema-specific-search"></a>結構描述的特定搜尋
 XML 結構描述總管也包含一些內建的搜尋，可讓您使用 XML 結構描述總管的操作功能表進行存取。 如需可用內容功能表的詳細資訊，請參閱[內容功能表](../xml-tools/context-menus-xml-schema-explorer.md)。 您也可以從 [開始] 視圖執行架構特定的搜尋。如需詳細資訊，請參閱[開始查看](../xml-tools/start-view.md)主題中的「架構集詳細資料」一節。

## <a name="displaying-and-navigating-search-results"></a>顯示和導覽搜尋結果
 搜尋完成後，摘要結果面板會加入含搜尋結果的工具列。 搜尋結果也會在 XML 結構描述總管中反白顯示並以刻度標示在垂直捲軸上。 您可以在 XML 架構瀏覽器工具列的 [摘要結果] 窗格中，使用 [**移至下一個搜尋結果**] 和 [**移至上一個搜尋結果**] 按鈕，流覽搜尋結果。使用鍵盤按鍵 F3 和 Shift + F3;或按一下捲軸中的刻度標記。

 您可以按一下 [摘要] 結果窗格上的 [**將反白顯示的節點新增至工作區**] 按鈕，將搜尋結果新增至工作區。

 ![XML 架構瀏覽器搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>清除搜尋結果
 若要清除搜尋結果，請按一下 XML 架構瀏覽器 [搜尋] 工具列之 [摘要] 結果窗格上的 [ **x** ] 按鈕。

## <a name="see-also"></a>請參閱
 [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)
