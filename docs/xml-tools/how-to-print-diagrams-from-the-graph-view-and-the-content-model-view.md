---
title: 列印圖表
description: 瞭解如何從圖形視圖或 XML 架構設計工具的內容模型視圖列印圖表。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7e1785e4-4aaf-4c66-8735-51e7ca035565
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 16366780d4f8d62cd139d22b09529e9602d9b3c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897411"
---
# <a name="how-to-print-diagrams-from-the-graph-view-and-the-content-model-view"></a>如何：從圖表視圖和內容模型視圖列印圖表

本主題描述如何從圖形視圖或 XML 架構設計工具的內容模型視圖列印圖表。

## <a name="to-print-diagrams-from-the-xml-schema-designer"></a>從 XML 結構描述設計工具列印圖表

1. 在 Visual Studio 中開啟 XSD 檔案，然後將某些節點新增至 [XML 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。

2. 將圖表匯出為 XPS 檔案，方法是使用 [將 **圖表匯出為影像** 內容] (以滑鼠右鍵按一下 [圖形] 視圖的設計介面中的) 功能表項目或 [內容模型視圖]。

     當您從圖形視圖匯出圖表時，整個設計介面都會匯出至 XPS 檔案。 當您從內容模型視圖匯出圖表，且內容模型視圖的設計介面上出現一個以上的節點時，只會將第一個節點匯出至 XPS 檔案。

3. 使用 XPS 檢視器列印儲存在 XPS 檔中的影像。

## <a name="see-also"></a>另請參閱

- [圖形檢視](../xml-tools/graph-view.md)
- [內容模型檢視](../xml-tools/content-model-view.md)
- [XML 架構設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)
