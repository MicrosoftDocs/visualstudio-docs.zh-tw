---
title: 使用 XML 編輯器中的 XML 結構描述設計工具整合
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e2cb44f3416aabfa859d4a8ef2126003b3ce59e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992122"
---
# <a name="integration-with-xml-editor"></a>與 XML 編輯器整合

XML 結構描述設計工具會與 XML 編輯器整合。 如果您修改 XSD 檔案在 XML 編輯器 中，變更將會反映在[XML 結構描述總管](../xml-tools/xml-schema-explorer.md)。 如果您有[圖表檢視](../xml-tools/graph-view.md)或[內容模型檢視](../xml-tools/content-model-view.md)開啟時，變更也會反映那里。 您可以利用下列方式，在 XML 結構描述設計工具和 XML 編輯器之間巡覽：

-   在 XML 編輯器中，以滑鼠右鍵按一下節點，然後選取**在 XML 結構描述總管中顯示**。

-   在 [圖表] 檢視中， **XML 結構描述總管**，按兩下節點，或以滑鼠右鍵按一下節點並選取**檢視程式碼**。 在內容模型檢視中，以滑鼠右鍵按一下節點，然後選取**檢視程式碼**。

下列螢幕擷取畫面顯示在中開啟 XML 結構描述**XML 結構描述總管**。 **XML 結構描述總管**顯示在樹狀檢視中設定的結構描述。 XML 編輯器中顯示的文字檢視是目前作用中節點**XML 結構描述總管**。

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

有時候，在並排顯示的 XML 編輯器和圖形設計工具中查看程式碼相當有用。 若要檢視這兩個檔案，在相同的時間，以滑鼠右鍵按一下 XML 編輯器中，然後選取**檢視表設計工具**。 在 Visual Studio Windows 功能表中，選取**新增水平 （或垂直） 索引標籤群組**。

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>另請參閱

- [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)