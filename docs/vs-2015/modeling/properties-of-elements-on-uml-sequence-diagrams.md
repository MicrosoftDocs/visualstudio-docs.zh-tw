---
title: 屬性中的項目 UML 循序圖 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7af657496fc95b07c7149f75fa03087eb1988606
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245215"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>UML 循序圖上的項目屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 循序圖中，圖表上的每個項目都會有屬性。 若要查看項目的屬性，以滑鼠右鍵按一下的項目在圖表上或在**UML 模型總管**，然後按一下**屬性**。 屬性會出現在**屬性**視窗。  
  
> [!NOTE]
>  本主題有關 UML 循序圖中的項目屬性。 如需如何閱讀 UML 循序圖的詳細資訊，請參閱[UML 循序圖： 參考](../modeling/uml-sequence-diagrams-reference.md)。 如需如何繪製 UML 循序圖的詳細資訊，請參閱 [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md)。  
  
## <a name="properties-of-elements"></a>項目屬性  
  
|屬性|預設|項目|描述|  
|--------------|-------------|-------------|-----------------|  
|**名稱**|預設名稱|全部|識別項目。|  
|**限定的名稱**|套件 :: 名稱|全部|唯一識別項目。 前面加上含有該項目之套件的合格名稱。|  
|**工作項目**|0 associated|全部|與此項目相關聯的工作項目數。 若要關聯工作項目，請參閱[連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。|  
|**描述**|(空白)|全部|您可以在這裡設定項目的一般注意事項。|  
|**色彩**|(項目類型的預設值)|生命線，訊息|圖案的色彩。 這是圖形的屬性，而不是它所顯示的項目。|  
|**Type**|(空白)|生命線|生命線所代表的執行個體類型。<br /><br /> 如果生命線標頭中顯示參考符號，則此類別或介面分別存在於 UML 模型總管中，而且可以顯示在類別圖上。|  
|**動作項目**|False|生命線|表示生命線代表外部圖表相關元件的使用者、裝置或軟體元件。|  
|**種類**|**完成**-含有寄件者和接收者的訊息。<br /><br /> **找到**-含有未指定的寄件者的訊息。<br /><br /> **遺失**-含有未指定的接收者的訊息。|訊息|代表訊息的哪一端附加至生命線。<br /><br /> 您無法變更這個屬性。 在建立訊息時設定它。|  
|**排序**|**AsynchCall** -非同步訊息。<br /><br /> **SynchCall** -同步訊息。<br /><br /> **回覆**-同步訊息的傳回部分。<br /><br /> **CreateMessage** -執行個體建立訊息。|訊息|訊息的類型。 您無法變更這個屬性。 它取決於用來建立訊息的工具。|  
|**作業**|(空白)|訊息|接收生命線中訊息所呼叫的方法。<br /><br /> 只有在接收生命線連結至介面或類別時才會顯示。|  
|**指的是**|循序圖|互動使用|這個互動使用所呼叫的循序圖。|  
|**互動運算子**|當您使用時設定**環繞**命令|合併片段|這個片段或片段集合所代表的運算子。|  
|**防護**|(空白)|合併片段中的互動運算元|除非 guard 為 true，否則片段中的序列不會出現。<br /><br /> 若要選取任何合併片段的最上層片段，請按一下片段標題下方。|  
|**Min、 Max**|(無限制)|重複合併片段|執行迴圈的最小和最大次數。|  
|**訊息**|(空白)|考慮並<br /><br /> 忽略合併片段|這個片段中考慮或忽略的訊息。|  
  
## <a name="see-also"></a>另請參閱  
 [UML 循序圖： 參考](../modeling/uml-sequence-diagrams-reference.md)   
 [UML 循序圖： 方針](../modeling/uml-sequence-diagrams-guidelines.md)   
 [以 UML 順序圖表說明具有片段的控制流程](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)



