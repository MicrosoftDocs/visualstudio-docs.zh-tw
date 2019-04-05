---
title: UML 循序圖：參考 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3990d43ae11db3db8eb792883ba62a030cde3a2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930618"
---
# <a name="uml-sequence-diagrams-reference"></a>UML 循序圖：參考資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，*循序圖*顯示代表一系列訊息執行個體的類別、 元件、 子系統或動作項目之間的互動方式。 在圖表中，時間會往下流動，並顯示從某個參與者到另一個參與者的控制流程。 使用循序圖來視覺化執行個體和事件，而非類別和方法。 多個相同類型的執行個體可以出現在圖表上。 相同的訊息也可以出現多次。  
  
 UML 循序圖是 UML 模型的一部分，而且只存在於 UML 模型專案內。 若要建立 UML 循序圖中，在**架構**功能表上，按一下**新增 UML 或分層圖**。 深入了解如何建立和繪製[UML 循序圖](../modeling/uml-sequence-diagrams-guidelines.md)或是[UML 模型圖](../modeling/edit-uml-models-and-diagrams.md)一般。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="reading-sequence-diagrams"></a>讀取循序圖  
 下表描述可在循序圖上看到的項目。 深入了解這些[項目的屬性](../modeling/properties-of-elements-on-uml-sequence-diagrams.md)。  
  
 ![順序圖表的一部分](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**Shape**|**目**|**描述**|  
|---------------|-----------------|---------------------|  
|1|**Lifeline**|垂直線代表互動期間在參與者中發生的一系列事件，而時間沿著這個線條向下。 這個參與者可以是類別、元件或行動的執行個體。|  
|2|**Actor**|所開發系統的外部參與者。<br /><br /> 您可以讓行動符號出現在生命線頂端藉由設定其**動作項目**屬性。|  
|3|**同步訊息**|寄件者會等到同步訊息的回應，才會繼續進行。 這個圖表顯示呼叫和傳回。 同步訊息用來代表程式內的一般函式呼叫，以及行為相同之其他類型的訊息。|  
|4|**非同步訊息**|寄件者繼續之前，不需要回應的訊息。 非同步訊息只會顯示來自寄件者的呼叫。 用來代表個別執行緒或建立新執行緒之間的通訊。|  
|5|**執行出現次數**|一個垂直網底矩形，出現在參與者生命線上，並代表參與者執行作業的期間。<br /><br /> 在參與者收到訊息時開始執行。 如果初始訊息是同步訊息，則會結束執行，並將 «return» 箭號傳回給寄件者。|  
|6|**回呼訊息**|一則訊息，傳回給正在等候較早呼叫傳回的參與者。 產生的執行項目會顯示在現有項目頂端。|  
|7|**自我訊息**|參與者給它自己的訊息。 產生的執行項目會顯示在傳送執行頂端。|  
|8|**建立訊息**|建立參與者的訊息。 如果參與者收到建立訊息，則這應該是它收到的第一個訊息。|  
|9|**找到的訊息**|來自未知或未指定參與者的非同步訊息。|  
|10|**遺失的訊息**|送至未知或未指定參與者的非同步訊息。|  
|11|**註解**|註解可以附加至生命線的任何位置。|  
|12|**互動使用**|包括其他圖表中定義的一系列訊息。<br /><br /> 若要建立**互動使用**，按一下  工具，然後拖曳過您想要包含的生命線。|  
|13|**合併的片段**|片段的集合。 每個片段都可以包括一或多個訊息。 有不同類型的合併片段。 如需詳細資訊，請參閱 <<c0> [ 描述控制流程，以在 UML 循序圖上的片段](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)。<br /><br /> 若要建立片段，以滑鼠右鍵按一下訊息，並指向**環繞**，然後按一下片段類型。|  
|14|**片段成立條件**|可以用來陳述片段是否發生的相關條件。<br /><br /> 若要設定成立條件，請選取片段，並選取成立條件，然後輸入值。|  
|**X**|**終結事件**|代表已刪除或無法再存取物件的位置。 出現在每個生命線底部。|  
||**互動**|顯示在循序圖中的訊息和生命線集合。 若要檢視互動的屬性，您必須選取它在**UML 模型總管**。|  
||**順序圖表**|顯示互動的圖表。 若要檢視其屬性，請按一下圖表的空白部分。 **注意：** 循序圖的名稱、所顯示的互動以及包含圖表的檔案都可以不同。|  
  
## <a name="see-also"></a>另請參閱  
 [UML 順序圖表：指導方針](../modeling/uml-sequence-diagrams-guidelines.md)   
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 使用案例圖表：參考](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)   
 [UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)
