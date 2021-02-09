---
title: XML 結構描述設計工具工作空間
description: 在 Visual Studio 中，瞭解 XML 架構設計工具中的 [開始]、[圖形] 和 [內容] 模型視圖 (XSD 設計工具) 工作區。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 588fa495-fe7f-4b16-8a9f-6b6b8d2d502a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ca91d586be9a351d113aed758d4312dab1a98299
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874855"
---
# <a name="xml-schema-designer-workspace-views"></a>XML 架構設計工具工作區視圖

XML 結構描述設計工具 (XSD 設計工具) 是一種圖形化工具，可協助您瀏覽 XML 結構描述。 除了 [Xml 架構瀏覽器](../xml-tools/xml-schema-explorer.md)（可讓您流覽和流覽 xml 架構樹狀結構和執行搜尋）之外，XSD 設計工具也提供三個可讓您更詳細地探索 XSD 架構的視圖。

- [ **開始] 視圖** 是 XSD 設計工具的啟動點。從 [開始] 視圖中，您可以流覽至 XSD 設計工具的其他視圖，並查看架構集合的詳細資料。
- **圖形視圖** 可讓您查看架構集的總覽，以及架構節點之間的關聯性。
- **內容模型視圖** 提供本機和全域架構節點詳細資料的圖形表示，包括簡單和複雜類型、元素、群組、屬性和屬性群組。

若要開始探索您感興趣的節點，您必須將它們新增至工作區。 工作空間在所有檢視之間共用。

## <a name="add-nodes-to-the-workspace"></a>將節點新增至工作區

您可以利用下列方式將節點加入至工作空間：

- 在 [ [開始] 視圖](../xml-tools/start-view.md)的 [架構設定詳細資料] 區段中，按一下全域節點類型旁的 [ **新增** ] 連結。

- 將全域節點、檔案節點以及命名空間節點從 **XML 架構瀏覽器** 拖放到三個視圖的任一個。 如需詳細資訊，請參閱 [XML 架構瀏覽器](../xml-tools/xml-schema-explorer.md)中的「拖放節點」一節。

- 使用內容 (以滑鼠右鍵按一下 **XML 架構瀏覽器** 中的) 功能表。 如需詳細資訊，請參閱 [快顯功能表](../xml-tools/context-menus-xml-schema-explorer.md)。

- 在 XSD Explorer 中執行搜尋，然後按一下 [摘要結果] 窗格上的 [ **將反白顯示的節點加入工作區** ] 按鈕。 如需詳細資訊，請參閱 [搜尋架構集合](../xml-tools/searching-the-schema-set.md)。

## <a name="switch-views"></a>切換檢視

若要切換檢視，請使用下列其中一項：

- XSD 設計工具工具列。

- 內容 (以滑鼠右鍵按一下內容模型視圖的) 功能表和圖形視圖。

- 開始檢視頁上的浮水印，或空白內容模型檢視或圖表檢視上的浮水印。

- 快速鍵： **ctrl** + **1** 適用于開始視圖、 **ctrl** + **2** （適用于圖形視圖）和 **ctrl** + **3** （內容模型視圖）。
