---
title: 以 UML 順序圖表說明具有片段的控制流程 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbb3d6dd6e83d245afc8d2367e120db245d8285f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942954"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>以 UML 循序圖說明具有片段的控制流程
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 循序圖中， *「合併片段」* (combined fragment) 可讓您顯示迴圈、分支，與其他替代方案。  
  
 合併片段包含一或多個 *「互動運算元」*(interaction operand)，而這每一個都含括一或多個訊息、互動使用或合併片段。  
  
> [!NOTE]
>  本主題是有關在循序圖中的片段。 如需如何閱讀 UML 循序圖的詳細資訊，請參閱[UML 循序圖：參考資料](../modeling/uml-sequence-diagrams-reference.md)。 如需如何繪製 UML 循序圖的詳細資訊，請參閱[UML 循序圖：指導方針](../modeling/uml-sequence-diagrams-guidelines.md)。  
  
 ![合併片段有兩個互動運算元](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 圖中顯示的項目如下所示。  
  
1.  合併片段。 有不同類型的合併片段。 這個範例是 Alt 合併片段，您可以用來顯示訊息可能發生的替代順序。  
  
2.  互動運算元。 每個合併片段包含至少一個互動運算元，它可以包含訊息、互動使用和較小的合併片段。 在此範例中，Alt 合併片段有兩個互動作業，顯示兩個替代的訊息順序。  
  
3.  您可以在每個互動運算元裡面按一下，個別選取它們。 在此範例中，會選取最上層的互動運算元，讓您可以看到它的界限。 一般而言，只會看見互動運算元之間的分隔線。  
  
    > [!NOTE]
    >  若要選取最上層的互動運算元，您不能按太靠近合併片段頂端之處。  
  
4.  成立條件。 您可以賦予每個互動運算元一個成立條件。 這說明執行互動運算元內訊息的條件。  
  
## <a name="creating-combined-fragments"></a>建立合併片段  
 如需您可以建立的片段類型清單，請參閱 [合併片段的類型](#KindsOfFragment)。  
  
#### <a name="to-create-a-combined-fragment"></a>建立合併片段  
  
1. 選取一則訊息，或一系列全由相同生命線或執行出現次數開始的訊息。  
  
   > [!NOTE]
   >  如果您選取多則訊息，它們必須形成不可中斷的序列。  
  
2. 以滑鼠右鍵按一下其中一個訊息，並指向 [環繞] ，然後按一下您想要的合併片段類型，例如 [Alt 合併片段] 。  
  
    新的合併片段隨即出現。 標題表示您選取的合併片段類型，例如 [Alt] 。  
  
    在合併片段中，有一個片段包含您選取的訊息。  
  
   您可以將更多互動運算元加入某些類型的合併片段。  
  
   重新排列合併片段中的訊息之後，選擇捷徑功能表上的 [重新整理配置]  調整合併片段框架的大小。  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>將新的互動運算元加入合併片段  
  
1. 在互動運算元 (2) 內、任何包含的片段外，以及合併片段的標題下方的空白區域按一下滑鼠右鍵。  
  
2. 指向 [加入] 。  
  
3. 按一下 [Before 互動運算元] 或 [After 互動運算元] 。  
  
4. 您可以在新的互動運算元內使用訊息工具加入訊息，或是藉由複製並貼上現有的訊息來加入。  
  
   您可以設定互動運算元的 [成立條件]  屬性，來描述執行其中訊息的條件。 例如，在 [Loop]  合併片段中，您可以使用成立條件來指定迴圈繼續的條件。 在 [Alt]  合併片段中，您可以為每個互動運算元指定不同的條件。  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>設定互動運算元的成立條件  
  
1. 按一下互動運算元 (2) 內、任何包含的片段之外的空白區域。  
  
    互動運算元週圍和成立條件週圍，會顯示選取框線。  
  
    [屬性]  視窗中的標題會顯示 [互動運算元] 。  
  
2. 輸入成立條件。  
  
    條件會靠近片段頂端 (4)。  
  
   您可以設定某些類型的合併片段屬性。  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>設定或檢視合併片段的屬性  
  
-   以滑鼠右鍵按一下合併片段的標題，然後按一下 [屬性] 。  
  
    > [!NOTE]
    >  不同類型的合併片段有不同的屬性。  
  
##  <a name="KindsOfFragment"></a> 類型的合併片段  
  
### <a name="fragments-describing-control-flow"></a>描述控制流程的片段  
 簡單的循序圖只會顯示一個典型的序列。 您可以使用下列類型的合併片段來描述在不同的情況下，可能會發生的變化。  
  
|片段類型|描述|  
|-------------------|-----------------|  
|**Opt**|選擇性。 圍繞不一定會發生的序列。 您可以在成立條件中指定發生的條件。|  
|**Alt**|包含一份包含替代之訊息序列的片段清單。 在任何情況下只會有一個序列發生。<br /><br /> 您可以在每個片段放入成立條件，表示在哪些條件下可以執行。 **else** 的成立條件表示在沒有其他成立條件為 true 時，應該執行的片段。 如果所有成立條件都為 false，而且沒有任何 **else**，則片段都不會執行。|  
|**Loop**|片段會重複一些次數。 您可以在成立條件中表示它應該重複的條件。<br /><br /> Loop 合併片段有屬性 [Min]  和 [Max] ，它們表示可以重複片段的最小和最大次數。 預設為無限制。|  
|**Break**|如果執行此片段，則會放棄序列的其餘部分。 您可以使用成立條件來表示將發生中斷的條件。|  
|**Par**|Parallel 片段中的事件可以交錯。|  
|**Critical**|在 Par 或 Seq 片段內使用。 表示在此片段中的訊息不得與其他訊息交錯。|  
|**Seq**|有兩個或多個運算元片段。 牽涉到相同生命線的訊息必須按照片段順序發生。 不牽涉到相同的生命線時，可能會以平行方式交錯來自不同片段的訊息。|  
|**Strict**|有兩個或多個運算元片段。 片段必須按照指定的順序發生。|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>有關如何解譯序列的片段  
 根據預設，循序圖會說明一系列可能發生的訊息。 在執行系統中，您未選擇要在圖表上顯示的其他訊息可能會發生。  
  
 下列片段類型可用來變更此解譯。  
  
|片段類型|描述|  
|-------------------|-----------------|  
|**請考慮**|指定此片段描述的訊息清單。 其他訊息可能會發生在執行中的系統，但對於這項描述的目的而言不重要。<br /><br /> 在 [訊息]  屬性中輸入清單。|  
|[略過]|此片段未描述的訊息清單。 它們可能會發生在執行中的系統，但對於這項描述的目的而言不重要。<br /><br /> 在 [訊息]  屬性中輸入清單。|  
|**Assert**|運算元片段只指定有效的序列。 通常在 Consider 或 Ignore 片段中使用。|  
|**neg**|此片段中所顯示的序列不得發生。 通常在 Consider 或 Ignore 片段中使用。|  
  
## <a name="see-also"></a>另請參閱  
 [UML 順序圖表：指導方針](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)   
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)
