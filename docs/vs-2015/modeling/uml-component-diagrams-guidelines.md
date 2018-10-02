---
title: UML 元件圖： 方針 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2a01e81b54f5ee4a581cff4705d3751dd370bc0e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485714"
---
# <a name="uml-component-diagrams-guidelines"></a>UML 元件圖表：方針
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[UML 元件圖： 方針](https://docs.microsoft.com/visualstudio/modeling/uml-component-diagrams-guidelines)。  
  
在 Visual Studio 中，您可以繪製*元件圖*來顯示軟體系統的結構。 如需影片示範，請參閱 <<c0> [ 使用元件圖設計實體架構](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 若要建立 UML 元件圖，在**架構**功能表上，按一下**新增 UML 或分層圖**。  
  
 元件是模組單位，可在其環境內進行取代。 其內部項目隱藏的但具有一個或更完善*提供的介面*透過可存取其函式。 元件也可以*所需的介面*。 需要的介面會定義其需要的其他元件的函式或服務。 透過連接數個元件之提供的介面和需要的介面，可以建構較大型元件。 完整軟體系統可以視為元件。  
  
 繪製元件圖有數個優點：  
  
-   根據主要區塊考慮您的設計，可協助開發小組了解現有設計並建立新設計。  
  
-   透過將系統視為具有已妥善定義之提供的介面和需要的介面的元件集合，您可改進元件之間的分離。 這反而能夠讓設計更易於理解，並在需求變更時更易於做出相應變更。  
  
 您可以使用元件圖來代表設計，無論設計使用或將使用何種語言或平台。  
  
##  <a name="OtherDiagrams"></a> 與其他圖表的關聯性  
 您可以與其他圖表一起使用元件圖。  
  
|其他圖表|協助您討論和溝通設計的以下方面|  
|-------------------|--------------------------------------------------------------------|  
|UML 循序圖表|-系統的元件之間的互動<br />-互動元件內組件之間。<br /><br /> 如需詳細資訊，請參閱 < [UML 循序圖： 方針](../modeling/uml-sequence-diagrams-guidelines.md)。|  
|UML 類別圖表|-介面的元件。 類別圖可讓您將詳細說明介面的方法。<br />-傳送資料參數中跨元件的介面。<br /><br /> 如需詳細資訊，請參閱 < [UML 類別圖： 方針](../modeling/uml-class-diagrams-guidelines.md)。|  
|活動圖|-內部處理執行以回應傳入訊息的元件。<br /><br /> 如需詳細資訊，請參閱 < [UML 活動圖表： 指導方針](../modeling/uml-activity-diagrams-guidelines.md)。|  
|圖層圖表|您的元件的邏輯架構層。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 分層圖： 參考](../modeling/layer-diagrams-reference.md)。|  
  
##  <a name="Basics"></a> 繪製元件圖的基本步驟  
 如需元件圖 參考之元素的相關資訊，請參閱[UML 元件圖： 參考](../modeling/uml-component-diagrams-reference.md)。  
  
 如需如何使用在設計流程中的元件圖的詳細資訊，請參閱[您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)。  
  
> [!NOTE]
>  建立任何模型圖的詳細的步驟所述[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。  
  
#### <a name="to-create-a-component-diagram"></a>建立元件圖  
  
1.  在 **架構**功能表上，按一下**新增 UML 或分層圖**。  
  
2.  底下**範本**，按一下**UML 元件圖**。  
  
3.  命名圖表。  
  
4.  在**加入至模型專案**，在您方案中，選取現有的模型專案或**建立新的模型專案**，然後按一下 **確定**...  
  
     新的元件圖表會顯示為與 UML**元件圖**工具箱。 工具箱包含需要的項目和關聯。  
  
### <a name="drawing-components"></a>繪製元件  
 ![具有介面的元件](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 建立*元件*(1) 的系統或應用程式中每個主要功能單元。  
  
 範例包括應用程式、硬體裝置、Web 服務、.NET 組譯碼、程式類別或類別群組，或者程式的任何可分隔片段。  
  
##### <a name="to-create-components"></a>若要建立元件  
  
1.  按一下 **元件**在工具箱中，然後按一下圖表的空白部分。  
  
     \-或-  
  
     複製和貼上現有元件。  
  
    1.  尋找現有元件圖表中或在**UML 模型總管**。  
  
    2.  以滑鼠右鍵按一下元件，然後按一下**複製**。  
  
    3.  開啟要顯示複製元件的圖表。  
  
    4.  以滑鼠右鍵按一下圖表的空白部分，然後按一下**貼上**。  
  
         具有新名稱的元件複本隨即出現。  
  
2.  按一下元件的名稱以變更名稱。  
  
3.  如果只要查看元件的標頭，請按一下＞形箭號 (5)。  
  
### <a name="showing-the-ports-of-a-component"></a>顯示元件的連接埠  
 A*連接埠*(2，3） 代表訊息或作業呼叫的傳入或傳出元件的群組。 該群組可在介面中進行說明，而介面會定義連接埠的類型。 連接埠可以提供介面或要求介面。  
  
 使用的連接埠*提供介面*元件所實作，並可用於其他元件的 （2） 提供作業。  
  
 範例包括使用者介面、Web 服務、.NET 介面或任何程式設計語言的函式集合。  
  
 使用的連接埠*必要的介面*(3) 代表元件需要由其他元件或外部系統所提供的作業或服務群組。  
  
 例如，Web 瀏覽器需要 Web 伺服器，應用程式增益集則需要應用程式的服務。  
  
 元件連接埠的數量沒有限制。  
  
##### <a name="to-add-ports-to-a-component"></a>若要將連接埠加入至元件  
  
1.  在 [工具箱] 中，按一下**提供的介面**或是**需要的介面**。  
  
2.  按一下您要將連接埠加入至的元件。  
  
     連接埠隨即出現在元件的界限上。  
  
     如此即會建立新介面做為連接埠的類型。 此介面會出現在**UML 模型總管**。  
  
3.  拖曳元件界限周圍的連接埠，將其放置在需要的位置。  
  
4.  拖曳連接埠的標籤，來調整其位置。  
  
5.  按一下標籤對其進行變更。 標籤會顯示介面的名稱。 如果變更名稱，則會變更介面的名稱。  
  
 如果您要列出介面的屬性和作業，您可以將其新增至 UML 模型總管中的介面。 或者，您可以將介面從 UML Model Explorer 拖曳至類別圖，然後在圖表中新增作業和屬性。  
  
### <a name="linking-between-components"></a>元件之間的連結  
 使用相依性 (4) 顯示一個元件的需求可以由其他元件提供的作業或服務來滿足。  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>若要顯示提供的介面可以滿足需要的介面  
  
1.  在 [工具箱] 中，按一下**相依性**。  
  
2.  按一下需要的介面位於一個元件上的連接埠，然後按一下提供的介面位於其他元件的連接埠。  
  
 您應嘗試避免設計相依性迴圈，其中群組中的每個元件都與其他所有元件相依。  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>若要將現有介面的連接埠加入至元件  
  
-   尋找在介面中的**UML 模型總管**然後將它拖曳至元件。  
  
     -或-  
  
-   複製和貼上圖表中介面的參考。  
  
    1.  在類別圖或元件圖，以滑鼠右鍵按一下介面，然後按一下**複製**。  
  
    2.  在元件圖中，以滑鼠右鍵按一下元件，然後**貼上參考**。  
  
         提供的介面隨即出現在元件上。 旁邊顯示動作標籤。  
  
        > [!NOTE]
        >  如果您使用**貼上**而不是**貼上參考**，將會建立具有新名稱的新介面。  
  
    3.  如果您想要建立需要的介面，請按一下動作標籤，然後按一下**轉換成需要的介面**。  
  
##  <a name="Parts"></a> 顯示元件的內部組件  
 ![顯示內部組件的元件圖表](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 您可以將組件 (3) 放置在元件 (1) 中，以顯示該元件是如何由彼此互動的較小型元件組成的。  
  
 示範中的圖表說明類型為「立即進餐」Web 服務的每個執行個體都包含一個「客戶伺服器」執行個體和一個「廚房伺服器」執行個體。  
  
 組件是其父元件的屬性 (Property)，與屬性 (Attribute) 屬於一般類別非常類似。 組件具有自己的類型，這通常也是一個元件。 組件的標籤具有與一般屬性相同的格式：  
  
 `+ partName : TypeName`  
  
 在父元件內，每個組件都會顯示針對其類型 (4、5) 定義的提供的介面和需要的介面。 一個組件需要的作業或服務可由其他組件提供。 您可以使用**組件**連接器，以顯示組件彼此 (6) 連線的方式。  
  
 您也可以顯示父元件的介面實際上是該介面其中一個組件所提供或需要的介面。 您可以連接至內部組件使用的連接埠的父代的連接埠**委派**關聯 (9)。 兩個連接埠必須是相同類型 (提供的或要求的)，且介面類型應相容。  
  
 您可以使用新類型或從現有類型建立新組件。  
  
#### <a name="to-add-parts-to-a-component"></a>若要將組件加入至元件  
  
1.  針對視為父元件一部分的每個主要功能單元，建立組件。  
  
    1.  按一下 **元件**工具箱，然後按一下父元件 (1) 內部中。  
  
         新組件 (3) 隨即出現在父元件內。  
  
         在 [建立新的元件**UML 模型總管]**。 這是新組件的類型。  
  
         \-或-  
  
         從 [UML 模型總管] 中，將現有元件拖曳至父元件。  
  
         新組件 (3) 隨即出現在父元件內。 它的類型是從 [UML 模型總管] 中拖曳的元件。  
  
         \-或-  
  
         以滑鼠右鍵按一下元件，在圖表中或在 [UML 模型總管] 中，然後按一下**複製**。  
  
         以滑鼠右鍵按一下父元件，然後**貼上參考**。  
  
         新組件 (3) 隨即出現在父元件內。 它的類型是複製的元件。  
  
    2.  按一下新組件的名稱以變更名稱。 您不能變更其類型。  
  
    3.  您可以將提供的介面和需要的介面 (4、5) 加入至新組件。 按一下 **提供的介面**或是**需要的介面**工具，然後按一下組件。  
  
         \-或-  
  
         將現有的介面，從**UML 模型總管**拖曳至部分。  
  
         介面會加入至組件的類型，並出現在組件自身上。 需要的話，父元件會調整其大小。  
  
2.  將組件連接至另一個組件。  
  
    -   使用**相依性**工具來連接的連接埠的不同部分 (6)。  
  
3.  將組件連接至父元件的連接埠：  
  
    1.  在父元件上建立一個或多個連接埠 (7)。 按一下 **需要的介面**或**提供的介面**工具箱，然後按一下父元件。  
  
    2.  將連接埠委派 (9) 至一個或多個組件。 按一下 **委派**工具，則父元件上的連接埠和組件上的連接埠。 您可以使用相同的方式，來連接提供或需要介面的連接埠。  
  
### <a name="showing-the-parts-of-a-part"></a>顯示組件的部分  
 在將元件分解為各個組件之後，您可以將每個組件類型分解為自己的內部組件。  
  
 在個別元件圖中執行每個分解層是最容易的。 您必須首先找到組件的類型。 例如，在示範中，其中一個組件命名為 `DNCustomerServer`，而其類型是稱為 `CustomerServer` 的元件。 您可以在 [UML 模型總管] 中找到該類型，然後將其放置在其他圖表中。 然後，您可以建立其自己的內部組件。  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>若要將組件的類型放置在圖表上  
  
1.  決定組件類型的完整限定名稱。  
  
     以滑鼠右鍵按一下組件，然後按一下**屬性**。  
  
     類型名稱會出現在**型別**欄位 [屬性] 視窗。  
  
2.  找出組件中的型別**UML 模型總管**。  
  
     按一下 [**檢視**，指向**其他 Windows**，然後按一下**UML 模型總管]**。  
  
     展開此類型屬於的專案和任何封裝 (必要的話)。  
  
     型別會被列為**元件**。  
  
     必要時可以在這裡變更其名稱。  
  
3.  開啟或建立其他元件圖。  
  
4.  從 [UML 模型總管]，將類型拖曳至圖表。  
  
     類型的檢視會顯示為圖表中的元件。  
  
     它具有與您針對組件定義的相同介面。  
  
     現在您可以在其中加入組件。  
  
##  <a name="Designing"></a> 設計元件  
  
### <a name="describing-how-the-parts-collaborate"></a>說明組件如何共同合作  
 您可以繪製順序圖表，以顯示組件如何共同合作，以回應到達父元件的訊息。  
  
 您可以使用這些圖表來說明現有元件，以及設計新元件。  
  
 如果仍在設計元件，則可以繪製順序圖表，然後決定該圖表要包含哪些組件。 您可以使用順序圖表來實驗不同組件、需要的介面和訊息順序。 針對最常見最重要的流入訊息繪製順序圖表。 然後，您可以在元件中建立組件，對應至您已決定的各個生命線。  
  
 使用順序圖表評定系統的工作如何在不同元件之間分佈。  
  
-   如果太多工作堆積在一個組件，則與平均分佈工作相比，應用程式可能更難更新。  
  
-   如果工作分佈太廣泛，且具有許多互動，則系統效能可能會變慢，且難於掌握。  
  
 ![順序圖表顯示共同作業的組件](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>若要繪製順序圖表，以顯示組件之間的共同合作  
  
1.  建立新的順序圖表。  
  
     如需詳細資訊，請參閱 < [UML 循序圖： 方針](../modeling/uml-sequence-diagrams-guidelines.md)。  
  
2.  建立將訊息傳送至這個元件的外部元件、使用者、裝置或其他行動 (1) 的生命線。  
  
     您可以設定**動作項目**屬性為 true，表示它是外部列入考量的元件，這個生命線。 生命線上隨即出現桿狀圖形。  
  
3.  針對這個元件之提供的介面 (2) 建立生命線，選擇的行動會將訊息傳送給該元件。  
  
4.  針對元件的每個組件 (3) 建立生命線。  
  
5.  針對元件的每個需要的介面 (4) 建立生命線。  
  
6.  從外部行動 (5) 繪製訊息。 顯示訊息如何傳遞給組件，以及它們如何共同合作以回應訊息。  
  
7.  必要時，顯示傳送至需要的介面 (6) 的訊息。 不要顯示訊息執行內的任何詳細資料。  
  
### <a name="is-the-component-more-than-its-parts"></a>元件多於組件嗎？  
 在某些情況下，元件只是指定給組合部分集合的名稱。 所有工作都是組件執行的，且在執行階段沒有代表元件的程式碼或其他成品。  
  
 您可以先將此模型中指出，藉由設定**Is Indirectly Instantiated**元件的屬性。 在此情況下，所有元件的介面都應在連接埠上，並委派至內部組件。  
  
### <a name="describing-the-process-inside-each-part"></a>說明每個組件內的程序  
 您可以使用活動圖來顯示元件如何處理每則流入訊息。 如需詳細資訊，請參閱 < [UML 活動圖表： 指導方針](../modeling/uml-activity-diagrams-guidelines.md)。  
  
 ![活動圖表，連同資料緩衝區一起](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 使用 [接受事件動作] (1) 顯示流入訊息啟動新的執行緒。  
  
 使用物件節點和輸入/輸出連接來顯示資訊流程，以及顯示將資訊儲存在何處。 在範例中，物件節點 (2) 用於顯示在執行緒之間緩衝的項目。  
  
### <a name="defining-data-and-classes"></a>定義資料和類別  
 您可以使用 UML 類別圖描述下列項目的詳細內容：  
  
-   元件的介面。 當您將要求和提供連接埠新增至元件時，介面會出現在 UML 模型總管中。 您可以將其拖曳或複製至 UML 類別圖中以顯示其屬性、作業，以及和其他介面的關聯性。  
  
-   介面中傳送之作業參數中的資料。  
  
-   元件中儲存的資料，例如活動圖中物件流程所示內容。  
  
### <a name="general-dependencies-between-components"></a>元件之間的一般相依性  
 您可以僅將元件圖用於顯示設計的主要組件及其相依性。  
  
 ![元件之間的相依性](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 使用**相依性**工具繪製相依性。 這表示一個元件的設計依賴於另一個元件。  
  
 相依性的典型類型包括下列項目：  
  
-   一個元件呼叫其他元件內的程式碼。  
  
-   一個元件具現化在其他類別中定義的類別。  
  
-   一個元件使用其他元件建立的資訊。  
  
 您可以使用相依性箭號的名稱，來表示特定類型的用法。 若要設定的名稱，以滑鼠右鍵按一下箭號，然後按一下 [**屬性**，並將**名稱**欄位屬性] 視窗中。  
  
## <a name="see-also"></a>另請參閱  
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 元件圖： 參考](../modeling/uml-component-diagrams-reference.md)   
 [UML 循序圖： 參考](../modeling/uml-sequence-diagrams-reference.md)   
 [UML 使用案例圖： 參考](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 元件圖： 參考](../modeling/uml-component-diagrams-reference.md)   
 [影片： 使用元件圖設計實體架構](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)



