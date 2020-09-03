---
title: XML 架構瀏覽器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e9f61c56dd7ff2a9c6c19afc20ed279a7fdf855
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669366"
---
# <a name="xml-schema-explorer"></a>XML 結構描述總管
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 結構描述總管整合於 Microsoft Visual Studio 和 XML 編輯器，可讓您使用 XML 結構定義語言 (XSD) 結構描述。 當您開啟 XML 架構檔案時，[ **架構集** ] 節點會出現在 Xml 架構瀏覽器中。 所有包含的、匯入的或重新定義的目標檔結構描述，以及透過 `include` 或 `import` 陳述式參考的所有檔案，也會出現在 XML 結構描述總管中。

 XML 結構描述總管可讓您進行下列作業：

- 取得結構描述設定的快速概觀。

- 瀏覽和巡覽樹狀。

- 執行關鍵字和結構描述特有的搜尋。 如需詳細資訊，請參閱 [搜尋架構集合](../xml-tools/searching-the-schema-set.md)。

- 將搜尋結果加入至圖表檢視或內容模型檢視

- 依據文件順序、類型或名稱排序樹狀。 如需詳細資訊，請參閱 [排序、篩選和分組](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)。

- 開啟 XML 編輯器並跳到 XSD 檔中的程式碼位置。 如需詳細資訊，請參閱 [與 XML 編輯器整合](../xml-tools/integration-with-xml-editor.md)。

- 針對全域項目產生範例 XML。

  XML 結構描述總管會透過樹狀檢閱提供結構描述設定的階層式檢閱。 XML 結構描述總管也會提供搜尋、篩選、導覽和排序功能。 若要存取 XML 結構描述總管，請執行下列其中一項：

- 如果您在 [ [開始] 視圖](../xml-tools/start-view.md)上，請按一下 [ **XML 架構瀏覽器** ] 連結。

- 如果您是在 [圖形視圖](../xml-tools/graph-view.md) 或 [內容模型視圖](../xml-tools/content-model-view.md) 上，而且您的工作區中有節點，請使用內容功能表選取 XML 架構瀏覽器。

- 您也可以選取 [ **View** ] 功能表中的 [XML 架構] Explorerfrom。

- 您可以存取 XML 架構 Explorerfrom 具有與 .xsd 檔案相關聯 Visual Basic XML 常值的 .vb 檔案。 若要查看 XML 架構瀏覽器中的架構集，請以滑鼠右鍵按一下 XML 常值或 XML 命名空間匯入中的 XML 節點，然後選取 [ **在架構瀏覽器中顯示** ] 命令。 如需詳細資訊，請參閱 [Xml 常值與 Xml 架構瀏覽器的整合](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)。

## <a name="tree-view"></a>樹狀目錄檢視
 XML 結構描述總管會在樹狀中顯示預先編譯的結構描述設定資訊。 此樹狀會依照下列方式組織：

- 最上層是結構描述設定節點。

- 第二層包含命名空間。

- 第三層包含檔案。

- 第四層包含全域節點。 這可能包括項目、群組、複雜型別、簡單型別、屬性、屬性群組，以及 `include`、`import` 和 `redefine` 陳述式。

  以下是樹狀的範例：

  ![XML 結構描述總管](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")

## <a name="selection-and-activation"></a>選取和啟動
 若要反白顯示並選取節點，請在結構描述總管中按一下。

 若要啟動節點，請在選取節點時按兩下或按 **enter** 鍵。

- 啟動節點會開啟定義該節點的檔案 (如果該檔案尚未開啟)，並且在該檔案中選取此節點。

- 啟動檔案節點會開啟所選的檔案 (若該檔案尚未開啟)，並且反白顯示 `<schema>` 節點。

- 啟動 SchemaSet 或命名空間節點不會有任何反應。

## <a name="draging-and-dropping-nodes"></a>拖放節點
 您可以將全域節點、檔案節點以及命名空間節點拖放至 XSD 設計工具檢視中。 如果目前的 view 是 [開始視圖](../xml-tools/start-view.md)，則將節點拖曳至視圖上將會開啟 [圖形視圖](../xml-tools/graph-view.md)。 如果目前的視圖是 [內容模型視圖](../xml-tools/content-model-view.md) 或圖形視圖，則當您將節點拖放到該視圖上時，它不會變更。

 將檔案拖放到視圖上會將檔案中的所有全域節點加入至 [XSD 設計工具工作區](../xml-tools/xml-schema-designer-workspace.md)。 將命名空間置於檢視上則會將命名空間中的所有全域節點加入至該工作空間。 工作空間在所有檢視之間共用。

 您無法拖放本機節點或匯入。

## <a name="in-this-section"></a>本節內容

- [搜尋結構描述集](../xml-tools/searching-the-schema-set.md)

- [排序、篩檢與群組](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)

- [快顯功能表](../xml-tools/context-menus-xml-schema-explorer.md)

- [整合 XML 常值與 XML 結構描述總管](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)

## <a name="see-also"></a>另請參閱
 [如何：將節點從 XML 結構描述總管新增至工作區](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
