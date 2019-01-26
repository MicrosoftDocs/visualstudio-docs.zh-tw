---
title: 從圖表檢視] 和 [XML 結構描述設計工具的內容模型檢視列印圖表
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52e5fcf61bcb8c625d25707f235f15879cf46313
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013180"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>HOW TO：從 [圖形] 檢視和內容模型檢視列印圖表

本主題描述如何從圖表檢視或內容模型檢視的 XML 結構描述設計工具列印圖表。

## <a name="to-print-diagrams-from-the-xml-schema-designer"></a>從 XML 結構描述設計工具列印圖表

1.  在 Visual Studio 中開啟 XSD 檔案，並加入一些節點[XML 結構描述設計工具工作空間](../xml-tools/xml-schema-designer-workspace.md)。

2.  將圖表匯出至 XPS 檔案，使用**將圖表匯出為影像**操作 （右鍵） 功能表項目在設計介面中的 [圖形] 檢視或內容模型檢視。

     當您從圖表檢視匯出圖表時，就會將整個設計介面匯出至 XPS 檔。 當您從內容模型檢視匯出圖表和一個以上的節點會出現在內容模型檢視的設計介面上時，只有第一個節點被匯出至 XPS 檔。

3.  使用 XPS 檢視器列印儲存在 XPS 檔中的影像。

## <a name="see-also"></a>另請參閱

- [圖形檢視](../xml-tools/graph-view.md)
- [內容模型檢視](../xml-tools/content-model-view.md)
- [XML 結構描述設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)