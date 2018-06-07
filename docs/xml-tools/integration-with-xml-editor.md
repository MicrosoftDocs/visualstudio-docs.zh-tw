---
title: 使用 XML 編輯器的 XML 結構描述設計工具整合
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ae7595121fcefa36998a88b53aae466d3a726cb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573319"
---
# <a name="integration-with-xml-editor"></a>與 XML 編輯器整合

XML 結構描述設計工具會與 XML 編輯器整合。 如果您修改 XSD 檔案在 XML 編輯器中，此變更會反映在[XML 結構描述總管](../xml-tools/xml-schema-explorer.md)。 如果您有[圖表檢視](../xml-tools/graph-view.md)或[內容模型檢視](../xml-tools/content-model-view.md)開啟時，變更也會反映那里。 您可以利用下列方式，在 XML 結構描述設計工具和 XML 編輯器之間巡覽：

-   在 XML 編輯器中，以滑鼠右鍵按一下節點，然後選取**在 XML 結構描述總管中顯示**。

-   在 [圖形] 檢視和**XML 結構描述總管**、 按兩下的節點，或以滑鼠右鍵按一下節點並選取**檢視程式碼**。 在內容模型檢視中，以滑鼠右鍵按一下節點並選取**檢視程式碼**。

下列螢幕擷取畫面顯示 XML 結構描述中開啟**XML 結構描述總管**。 **XML 結構描述總管**顯示在樹狀檢視中設定的結構描述。 XML 編輯器會顯示目前作用中節點的文字檢視**XML 結構描述總管**。

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

有時候，在並排顯示的 XML 編輯器和圖形設計工具中查看程式碼相當有用。 若要同時檢視兩個檔案，以滑鼠右鍵按一下 XML 編輯器中，然後選取**檢視表設計工具**。 在 Visual Studio 視窗功能表中，選取**新增水平 （或垂直） 索引標籤群組**。

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>另請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)