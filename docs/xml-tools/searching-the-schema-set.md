---
title: XML 架構瀏覽器-搜尋架構集合
description: 瞭解如何在 XML 架構瀏覽器中對架構設定進行關鍵字搜尋和架構特定的搜尋。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f924e46fa4d32fbea9071bd8a19268f2ee1652e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891874"
---
# <a name="search-the-schema-set"></a>搜尋結構描述集合

**XML 架構瀏覽器** 可讓您以下列方式搜尋架構集合：

- 關鍵字搜尋。

- 結構描述特有的搜尋。

## <a name="keyword-search"></a>關鍵字搜尋

您可以在 **XML 架構瀏覽器** 工具列的 [**搜尋 SchemaSet** ] 文字方塊中輸入子字串，以執行關鍵字搜尋。

![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif)

**XML 架構瀏覽器** 會搜尋架構集合中的下列屬性：

- 符合指定之關鍵字的任何 `name` 或 `ref` 屬性。 您可以依名稱尋找元素、屬性、類型等等。

- include 陳述式的 `schemaLocation` 屬性。

- import 陳述式的 `namespace` 屬性。

## <a name="schema-specific-search"></a>架構特定搜尋

**Xml 架構瀏覽器** 也包含內建的搜尋，您可以使用內容 (以滑鼠右鍵按一下 **XML 架構瀏覽器** 的) 功能表來存取這些搜尋。 如需可用內容功能表的詳細資訊，請參閱 [內容功能表](../xml-tools/context-menus-xml-schema-explorer.md)。 您也可以從開始視圖執行架構特定的搜尋;如需詳細資訊，請參閱 [開始視圖](../xml-tools/start-view.md) 主題中的「架構設定詳細資料」一節。

## <a name="display-and-navigate-search-results"></a>顯示和導覽搜尋結果

搜尋完成後，摘要結果面板會加入含搜尋結果的工具列。 搜尋結果也會在 **XML 架構瀏覽器** 中反白顯示，並在垂直捲動條上以刻度標記。 您可以使用 **XML 架構瀏覽器** 工具列之 [摘要結果] 窗格中的 [**移至下一個搜尋結果**] 和 [**移至上一個搜尋結果**] 按鈕，來流覽搜尋結果。使用鍵盤按鍵 **F3** 和 **Shift** + **f3**; 或按一下捲軸中的刻度標記。

您可以按一下 [摘要結果] 窗格上的 [ **將反白顯示的節點加入工作區** ]，將搜尋結果新增至工作區。

![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>清除搜尋結果

若要清除搜尋結果，請按一下 **XML Schema Explorer** 搜尋工具列之 [摘要結果] 窗格中的 [ **x** ] 按鈕。

## <a name="see-also"></a>另請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)
