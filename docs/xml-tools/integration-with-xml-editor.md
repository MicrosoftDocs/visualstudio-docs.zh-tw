---
title: XML 架構設計工具與 XML 編輯器的整合
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23a9220d84e2fb1a15545d1a880b0084952da77f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592577"
---
# <a name="integration-with-xml-editor"></a>與 XML 編輯器整合

XML 架構設計工具會與 XML 編輯器整合。 如果您在 XML 編輯器中修改 XSD 檔案，變更就會反映在[Xml 架構瀏覽器](../xml-tools/xml-schema-explorer.md)中。 如果您已開啟 [[圖形視圖]](../xml-tools/graph-view.md)或 [[內容模型] 視圖](../xml-tools/content-model-view.md)，變更也會反映在該處。 您可以透過下列方式，在 XML 架構設計工具和 XML 編輯器之間流覽：

- 在 XML 編輯器中，以滑鼠右鍵按一下節點，然後選取 [**在 Xml 架構瀏覽器中顯示**]。

- 在圖表視圖和**XML 架構瀏覽器**中，按兩下節點，或以滑鼠右鍵按一下節點，然後選取 [ **View Code**]。 在內容模型視圖中，以滑鼠右鍵按一下節點，然後選取 [ **View Code**]。

下列螢幕擷取畫面顯示在**Xml 架構瀏覽器**中開啟的 xml 架構。 **XML 架構瀏覽器**會在樹狀檢視中顯示架構集。 XML 編輯器會顯示**Xml 架構瀏覽器**中目前作用中節點的文本視圖。

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

有時候，在 XML 編輯器和圖形設計工具中並排查看程式碼會很有説明。 若要同時查看這兩個檔案，請以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取 [ **View Designer**]。 在 [Visual Studio Windows] 功能表中，選取 [**新增水準（或垂直）]** 索引標籤群組。

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)
