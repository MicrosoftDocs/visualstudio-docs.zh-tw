---
title: "XML 結構描述總管 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1fa99ea63f9af2c69519691add827053b3059ac0
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="xml-schema-explorer"></a>XML 結構描述總管
XML 結構描述總管整合於 Microsoft Visual Studio 和 XML 編輯器，可讓您使用 XML 結構定義語言 (XSD) 結構描述。 當您開啟 XML 結構描述檔案，**結構描述集**節點會出現在 XML 結構描述總管。 所有包含的、匯入的或重新定義的目標檔結構描述，以及透過 `include` 或 `import` 陳述式參考的所有檔案，也會出現在 XML 結構描述總管中。  
  
 XML 結構描述總管可讓您進行下列作業：  
  
-   取得結構描述設定的快速概觀。  
  
-   瀏覽和巡覽樹狀結構。  
  
-   執行關鍵字和結構描述特有的搜尋。 如需詳細資訊，請參閱[搜尋結構描述集](../xml-tools/searching-the-schema-set.md)。  
  
-   將搜尋結果加入至圖表檢視或內容模型檢視  
  
-   依據文件順序、類型或名稱排序樹狀。 如需詳細資訊，請參閱[排序、 篩選與分組](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)。  
  
-   開啟 XML 編輯器並跳到 XSD 檔中的程式碼位置。 如需詳細資訊，請參閱[使用 XML 編輯器整合](../xml-tools/integration-with-xml-editor.md)。  
  
-   針對全域項目產生範例 XML。  
  
XML 結構描述總管會透過樹狀檢視提供結構描述設定的階層式檢視。 XML 結構描述總管也會提供搜尋、篩選、導覽和排序功能。 若要存取 XML 結構描述總管，請執行下列其中一項：  
  
-   如果您在[開始檢視](../xml-tools/start-view.md)，按一下  **XML 結構描述總管**連結。  
  
-   如果您在[圖表檢視](../xml-tools/graph-view.md)或[內容模型檢視](../xml-tools/content-model-view.md)和工作空間中具有節點，請使用操作功能表選取 XML 結構描述總管。  
  
-   您也可以選取 XML 結構描述 Explorerfrom**檢視**功能表。  
  
-   您可以存取 XML 結構描述 Explorerfrom 具有 Visual Basic XML 常值與.xsd 檔案相關聯的.vb 檔案。 若要查看結構描述設定在 XML 結構描述總管中，以滑鼠右鍵按一下 XML 常值中的 XML 節點或 XML 命名空間匯入並選取**在結構描述總管中顯示**命令。 如需詳細資訊，請參閱[整合的 XML 常值與 XML 結構描述總管](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)。  
  
## <a name="tree-view"></a>樹狀檢閱  
 XML 結構描述總管會在樹狀結構中顯示預先編譯的結構描述設定資訊。 此樹狀結構會依照下列方式組織：  
  
-   最上層是結構描述設定節點。  
  
-   第二層包含命名空間。  
  
-   第三層包含檔案。  
  
-   第四層包含全域節點。 這可能包括項目、群組、複雜型別、簡單型別、屬性、屬性群組，以及 `include`、`import` 和 `redefine` 陳述式。  
  
以下是樹狀的範例：  
  
![XML 結構描述總管](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>選取和啟動  
 若要反白顯示並選取節點，請在結構描述總管中按一下。  
  
 若要啟動節點，連按兩下，或按**Enter**選取節點之後。  
  
-   啟動節點會開啟定義該節點的檔案 (如果該檔案尚未開啟)，並且在該檔案中選取此節點。  
  
-   啟動檔案節點會開啟所選的檔案 (若該檔案尚未開啟)，並且反白顯示 `<schema>` 節點。  
  
-   啟動 SchemaSet 或命名空間節點不會有任何反應。  
  
## <a name="draging-and-dropping-nodes"></a>拖放節點  
 您可以將全域節點、檔案節點以及命名空間節點拖放至 XSD 設計工具檢視中。 如果目前的檢視是[開始檢視](../xml-tools/start-view.md)，拖曳到檢視的節點會開啟[圖表檢視](../xml-tools/graph-view.md)。 如果目前的檢視是[內容模型檢視](../xml-tools/content-model-view.md)或圖表檢視，檢視不會變更當您卸除至其本身的節點。  
  
 卸除檢視上的檔案會在檔案中新增所有全域節點[XSD 設計工具工作空間](../xml-tools/xml-schema-designer-workspace.md)。 將命名空間置於檢視上則會將命名空間中的所有全域節點加入至該工作空間。 工作空間在所有檢視之間共用。  
  
 您無法拖放本機節點或匯入。  
  
## <a name="in-this-section"></a>本章節內容  
  
-   [搜尋結構描述集合](../xml-tools/searching-the-schema-set.md)  
  
-   [排序、 篩檢與群組](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [操作功能表](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [整合 XML 常值與 XML 結構描述總管](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何：將節點從 XML 結構描述總管新增至工作區](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)