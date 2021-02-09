---
title: XML 結構描述總管
description: 瞭解與 Visual Studio 和 XML 編輯器整合之 XML 架構瀏覽器的功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4b16c1baa039a2f1e812d35e7a4994ffc0d5e5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874882"
---
# <a name="xml-schema-explorer"></a>XML 結構描述總管

**Xml 架構瀏覽器** 已與 MICROSOFT VISUAL STUDIO 和 xml 編輯器整合，可讓您使用 xml 架構定義語言 (XSD) 架構。 當您開啟 XML 架構檔案時，[ **架構集** ] 節點會出現在 **Xml 架構瀏覽器** 中。 所有包含、匯入或重新定義之目標檔案的架構，以及透過或語句所參考的任何檔案， `include` `import` 也會出現在 **XML 架構瀏覽器** 中。

**XML 架構瀏覽器** 可讓您執行下列作業：

- 取得結構描述設定的快速概觀。

- 瀏覽和巡覽樹狀。

- 執行關鍵字和結構描述特有的搜尋。 如需詳細資訊，請參閱 [搜尋架構集合](../xml-tools/searching-the-schema-set.md)。

- 將搜尋結果新增至 Graph 視圖或內容模型視圖

- 依據文件順序、類型或名稱排序樹狀。 如需詳細資訊，請參閱 [排序、篩選和分組](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)。

- 開啟 XML 編輯器，並跳至 XSD 檔案中的程式碼位置。 如需詳細資訊，請參閱 [與 XML 編輯器整合](../xml-tools/integration-with-xml-editor.md)。

- 針對全域項目產生範例 XML。

**XML 架構瀏覽器** 會透過樹狀檢視提供架構設定的階層視圖。 **XML 架構瀏覽器** 也提供搜尋、篩選、流覽和排序。 若要存取 **XML 架構瀏覽器**，請執行下列其中一項：

- 如果您在 [ [開始] 視圖](../xml-tools/start-view.md)上，請按一下 [ **XML 架構瀏覽器** ] 連結。

- 如果您是在 [圖形視圖](../xml-tools/graph-view.md) 或 [內容模型視圖](../xml-tools/content-model-view.md) 上，而且您的工作區中有節點，請使用內容 (以滑鼠右鍵按一下 [) ] 功能表，以選取 [ **XML 架構瀏覽器**]。

- 您也可以從 [ **View** ] 功能表中選取 [ **XML 架構瀏覽器**]。

- 您可以從具有與 *.xsd* 檔案相關聯之 Visual Basic xml 常值的 .vb 檔案，存取 **Xml 架構瀏覽器** *。* 若要查看 **Xml 架構瀏覽器** 中的架構集，請以滑鼠右鍵按一下 xml 常值或 xml 命名空間匯入中的 xml 節點，然後選取 [ **在架構瀏覽器中顯示** ] 命令。 如需詳細資訊，請參閱 [xml 常值與 Xml 架構瀏覽器的整合](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)。

## <a name="tree-view"></a>樹狀目錄檢視
**XML 架構瀏覽器** 會在樹狀結構中顯示預先編譯的架構集資訊。 此樹狀會依照下列方式組織：

- 最上層是結構描述設定節點。

- 第二層包含命名空間。

- 第三層包含檔案。

- 第四層包含全域節點。 這可能包括項目、群組、複雜型別、簡單型別、屬性、屬性群組，以及 `include`、`import` 和 `redefine` 陳述式。

以下是樹狀的範例：

![XML 結構描述總管](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>選取和啟用
若要反白顯示並選取節點，請在結構描述總管中按一下。

若要啟動節點，請在選取節點時按兩下或按 **enter** 鍵。

- 啟動節點會開啟定義該節點的檔案 (如果該檔案尚未開啟)，並且在該檔案中選取此節點。

- 啟動檔案節點會開啟所選的檔案 (若該檔案尚未開啟)，並且反白顯示 `<schema>` 節點。

- 啟動 SchemaSet 或命名空間節點不會有任何反應。

## <a name="drag-and-drop-nodes"></a>拖放節點
您可以將全域節點、檔案節點以及命名空間節點拖放至 XSD 設計工具檢視中。 如果目前的 view 是 [開始視圖](../xml-tools/start-view.md)，則將節點拖曳至視圖上將會開啟 [圖形視圖](../xml-tools/graph-view.md)。 如果目前的視圖是 [內容模型視圖](../xml-tools/content-model-view.md) 或圖形視圖，則當您將節點拖放到該視圖上時，它不會變更。

將檔案拖放到視圖上會將檔案中的所有全域節點加入至 [XSD 設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。 將命名空間置於檢視上則會將命名空間中的所有全域節點加入至該工作空間。 工作空間在所有檢視之間共用。

 您無法拖放本機節點或匯入。

## <a name="see-also"></a>另請參閱

- [如何：從 XML 架構瀏覽器將節點加入至工作區](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
