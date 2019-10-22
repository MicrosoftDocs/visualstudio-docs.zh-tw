---
title: 與 XML 編輯器整合 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c0d1088e9932613466209ef8517ac5035c0b613
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656247"
---
# <a name="integration-with-xml-editor"></a>與 XML 編輯器整合
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 結構描述設計工具會與 XML 編輯器整合。 如果您在 XML 編輯器中修改 XSD 檔案，變更就會反映在[Xml 架構瀏覽器](../xml-tools/xml-schema-explorer.md)中。 如果您已開啟 [[圖形視圖]](../xml-tools/graph-view.md)或 [[內容模型] 視圖](../xml-tools/content-model-view.md)，變更也會反映在該處。 您可以利用下列方式，在 XML 結構描述設計工具和 XML 編輯器之間巡覽：

- 在 XML 編輯器中，以滑鼠右鍵按一下節點，然後選取 [**在 Xml 架構瀏覽器中顯示**]。

- 在圖表視圖和 XML 架構瀏覽器中，按兩下節點，或以滑鼠右鍵按一下節點，然後選取 [ **View Code**]。 在內容模型視圖中，以滑鼠右鍵按一下節點，然後選取 [ **View Code**]。

  下列螢幕擷取畫面會顯示在 XML 結構描述總管中開啟的 XML 結構描述。 XML 結構描述總管會在樹狀檢閱中顯示結構描述設定。 XML 編輯器會顯示目前在 XML 結構描述總管中使用之節點的文字檢視。

  ![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")

  有時候，在並排顯示的 XML 編輯器和圖形設計工具中查看程式碼相當有用。 若要同時查看這兩個檔案，請以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取 [ **View Designer**]。 在 [Visual Studio Windows] 功能表中，選取 [**新增水準（或垂直）]** 索引標籤群組。

  ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")

## <a name="see-also"></a>請參閱
 [XML 結構描述總管](../xml-tools/xml-schema-explorer.md)
