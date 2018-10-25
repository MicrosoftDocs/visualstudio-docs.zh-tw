---
title: UML 元件圖： 參考 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.componentdiagram.diagram
- vs.teamarch.componentdiagram.toolbox
- vs.teamarch.UMLModelExplorer.componentdiagram
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 5eddff6a-892a-4c3c-9278-687ac1eccc50
caps.latest.revision: 38
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 322fb842f3e4ea5aa8afbec7835dc0bedc38f55b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829452"
---
# <a name="uml-component-diagrams-reference"></a>UML 元件圖表：參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，*元件圖*顯示軟體系統的設計的部分。 元件圖可協助您視覺化系統和服務行為的高階結構，而這些部分是透過介面來提供和取用。 若要建立 UML 元件圖，在**架構**功能表上，按一下**新增 UML 或分層圖**。  

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  

 您可以使用元件圖來描述在任何語言或樣式中實作的設計。 只需要識別透過一組有限的輸入和輸出與設計的其他部分互動的設計部分。 元件可以是任何小數位數，也可以透過任何方式互連。  

 如需如何使用在設計流程中的元件圖的詳細資訊，請參閱[您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)。  

> [!NOTE]
>  本主題描述元件圖中可以使用的項目。 如需詳細資訊如何繪製元件圖的詳細資訊，請參閱[UML 元件圖： 方針](../modeling/uml-component-diagrams-guidelines.md)。 如需如何在一般情況下繪製模型圖表的詳細資訊，請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。  

## <a name="reading-component-diagrams"></a>讀取元件圖  
 下表描述可在元件圖上使用的項目，以及其主要屬性。 元素的屬性完整清單，請參閱 < [UML 元件圖上項目的屬性](../modeling/properties-of-elements-on-uml-component-diagrams.md)。  

 ![使用元件圖的項目](../modeling/media/uml-compovreading.png "UML_CompOvReading")  


|  **圖形**  |         **目**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         **描述和主要屬性**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|-------------|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      1      |        **元件**        |                                                                                                                                                                                                                                                                                                                                  系統功能的可重複使用部分。 元件透過介面來提供和使用行為，以及使用其他元件。<br /><br /> 您可以使用展開/摺疊控制項 (9) 來隱藏或顯示元件的內部組件。<br /><br /> 元件是一種類別。<br /><br /> -   **間接具現化**。 如果為 true (預設值)，元件只以設計成品方式存在。 在執行階段，只有其組件存在。                                                                                                                                                                                                                                                                                                                                  |
|      2      | **提供介面連接埠** |                                                                                                                                                                                                                                                                                                                                                                                                                                                            代表元件所實作以及其他元件或外部系統可使用的一組訊息或呼叫。 連接埠是將介面做為其類型之元件的屬性。                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|      3      | **所需的介面連接埠** |                                                                                                                                                                                                                                                                                                                                                                                                                                    代表元件傳送給其他元件或外部系統的一組訊息或呼叫。 元件設計成聯繫到至少提供這些作業的元件。 連接埠是將介面做為其類型。                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|      4      |       **相依性**        |                                                                                                                                                                                                                                                                                                                                                                                                                     可用來指出另一個元件上的 [提供的介面] 可以滿足某個元件上的 [需要的介面]。<br /><br /> 相依性也可以更廣泛地用於模型項目之間，以顯示某個元件的設計與其他元件的設計相依。                                                                                                                                                                                                                                                                                                                                                                                                                      |
|      5      |          **組件**           | 元件的屬性，其類型通常是另一個元件。 組件用於其父元件的內部設計中。 組件會以圖形方式顯示，而且是父元件內的巢狀組件。<br /><br /> 若要建立現有元件類型的組件，請將元件從 [UML 模型總管] 拖曳至擁有者元件。<br /><br /> 若要建立新類型的組件，按一下**元件**工具，然後按一下 擁有者元件。<br /><br /> 例如，元件 `Car` 具有組件 `engine:CarEngine`、`backLeft:Wheel`、`frontRight:Wheel` 等。<br /><br /> 多個組件的類型可以相同，而不同的元件也可以有相同類型的組件。<br /><br /> -   **型別**。 定義在模型其他位置之組件的類型。 此類型通常是另一個元件。<br />-   **多重性**。 預設值為 1。 您可以將它設定為**0..1**指出組件可以具有值**null**， **\\** \*表示的部分是執行個體的集合指定的型別，或任何運算式，可評估為一連串數字。 |
|      6      |      **組件**      |                                                                                                                                                                                                                                                                                                                                                                                                                                  某個組件的「需要的介面連接埠」與另一個組件的「提供的介面連接埠」之間的連接。 組件的實作可能會根據元件而不同。 連接的組件必須具有相同的父元件。                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|      7      |       **委派**        |                                                                                                                                                                                                                                                                                                                                                                                                                                                 將連接埠連結至其中一個元件之組件的介面。 指出組件會處理傳送給元件的訊息，或從父元件送出從組件所送出的訊息。                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| (未顯示) |     **一般化**      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          指出某個元件繼承另一個元件。 會繼承組件和介面。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|      9      |   展開/摺疊控制項   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                使用此選項來隱藏或顯示元件的內部組件。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| (未顯示) |         **註解**         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                其他備註。 您也可以使用任何數目的圖表上的項目連結註解**連接器**工具。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

## <a name="see-also"></a>另請參閱  
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 元件圖： 方針](../modeling/uml-component-diagrams-guidelines.md)   
 [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)   
 [UML 使用案例圖： 參考](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 活動圖表： 參考](../modeling/uml-activity-diagrams-reference.md)   
 [UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)



