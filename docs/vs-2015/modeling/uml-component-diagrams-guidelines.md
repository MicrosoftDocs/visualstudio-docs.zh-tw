---
title: UML 元件圖：方針 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297157"
---
# <a name="uml-component-diagrams-guidelines"></a>UML 元件圖表：方針
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，可以繪製 *「元件圖」* (Component Diagram) 顯示軟體系統的結構。 如需影片示範，請參閱[使用元件圖設計實體結構](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)。

 若要查看哪些版本的 Visual Studio 支援此功能，請參閱 [Architecture and Modeling Tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

 若要建立 UML 元件圖，請按一下 [架構] 功能表上的 [新增 UML 或分層圖]。

 元件是模組單位，可在其環境內進行取代。 它的內部項目已隱藏，但具有一個或多個已妥善定義的「*提供的介面*」(Provided Interface)，透過該介面可以存取其函式。 元件也可以具有「*需要的介面*」(Required Interface)。 需要的介面會定義其需要的其他元件的函式或服務。 透過連接數個元件之提供的介面和需要的介面，可以建構較大型元件。 完整軟體系統可以視為元件。

 繪製元件圖有數個優點：

- 根據主要區塊考慮您的設計，可協助開發小組了解現有設計並建立新設計。

- 透過將系統視為具有已妥善定義之提供的介面和需要的介面的元件集合，您可改進元件之間的分離。 這反而能夠讓設計更易於理解，並在需求變更時更易於做出相應變更。

  您可以使用元件圖來代表設計，無論設計使用或將使用何種語言或平台。

## <a name="OtherDiagrams"></a>與其他圖表的關聯性
 您可以與其他圖表一起使用元件圖。

|其他圖表|協助您討論和溝通設計的以下方面|
|-------------------|--------------------------------------------------------------------|
|UML 循序圖表|-系統元件之間的互動<br />-元件內的部分互動和之間的互動。<br /><br /> 如需詳細資訊，請參閱 [UML 順序圖表：方針](../modeling/uml-sequence-diagrams-guidelines.md)。|
|UML 類別圖表|-元件的介面。 類別圖可讓您將詳細說明介面的方法。<br />-跨元件介面的參數所傳送的資料。<br /><br /> 如需詳細資訊，請參閱 [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)。|
|活動圖|-元件為了回應傳入訊息而執行的內部處理。<br /><br /> 如需詳細資訊，請參閱 [UML 活動圖表：方針](../modeling/uml-activity-diagrams-guidelines.md)。|
|圖層圖表|-元件的邏輯架構層。<br /><br /> 如需詳細資訊，請參閱[分層圖：參考](../modeling/layer-diagrams-reference.md)。|

## <a name="Basics"></a>繪製元件圖的基本步驟
 如需元件圖上元素的參考資訊，請參閱[UML 元件圖：參考](../modeling/uml-component-diagrams-reference.md)。

 如需如何在設計流程中使用元件圖的詳細資訊，請參閱[模型應用程式的架構](../modeling/model-your-app-s-architecture.md)。

> [!NOTE]
> 如需建立任何模型圖表的詳細步驟，請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。

#### <a name="to-create-a-component-diagram"></a>建立元件圖

1. 在 [架構] 功能表上，按一下 [新增 UML 或分層圖]。

2. 在 [**範本**] 下，按一下 [**UML 元件圖**]。

3. 命名圖表。

4. 在 [**加入至模型專案**] 中，選取方案中的現有模型專案，或按一下 [**建立新模型專案**]，然後按一下 [**確定**]。

     新的元件圖隨即出現，並帶有 [**UML 元件圖**] 工具箱。 工具箱包含需要的項目和關聯。

### <a name="drawing-components"></a>繪製元件
 ![具有介面的元件](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 針對系統或應用程式中每個主要功能單元，建立「*元件*」(Component) (1)。

 範例包括應用程式、硬體裝置、Web 服務、.NET 組譯碼、程式類別或類別群組，或者程式的任何可分隔片段。

##### <a name="to-create-components"></a>若要建立元件

1. 按一下工具箱上的 [**元件**]，然後按一下圖表的空白部分。

     \-或-

     複製和貼上現有元件。

    1. 在圖表或 [**UML 模型總管**] 中尋找現有元件。

    2. 以滑鼠右鍵按一下元件，然後按一下 [**複製**]。

    3. 開啟要顯示複製元件的圖表。

    4. 以滑鼠右鍵按一下圖表的空白部分，然後按一下 [**貼上**]。

         具有新名稱的元件複本隨即出現。

2. 按一下元件的名稱以變更名稱。

3. 如果只要查看元件的標頭，請按一下＞形箭號 (5)。

### <a name="showing-the-ports-of-a-component"></a>顯示元件的連接埠
 「*連接埠*」(Port) (2、3) 代表傳入或傳出元件的訊息或作業呼叫群組。 該群組可在介面中進行說明，而介面會定義連接埠的類型。 連接埠可以提供介面或要求介面。

 具有「*提供的介面*」(Provided Interface) (2) 的連接埠可提供由該元件實作，且其他元件可以使用的作業。

 範例包括使用者介面、Web 服務、.NET 介面或任何程式設計語言的函式集合。

 具有「*需要的介面*」(Required Interface) (3) 的連接埠代表元件需要由其他元件或外部系統提供的作業或服務群組。

 例如，Web 瀏覽器需要 Web 伺服器，應用程式增益集則需要應用程式的服務。

 元件連接埠的數量沒有限制。

##### <a name="to-add-ports-to-a-component"></a>若要將連接埠加入至元件

1. 在工具箱中，按一下 [**提供的介面**] 或 [**需要的介面**]。

2. 按一下您要將連接埠加入至的元件。

    連接埠隨即出現在元件的界限上。

    如此即會建立新介面做為連接埠的類型。 這個介面會出現在 [**UML 模型總管**] 中。

3. 拖曳元件界限周圍的連接埠，將其放置在需要的位置。

4. 拖曳連接埠的標籤，來調整其位置。

5. 按一下標籤對其進行變更。 標籤會顯示介面的名稱。 如果變更名稱，則會變更介面的名稱。

   如果您要列出介面的屬性和作業，您可以將其新增至 UML 模型總管中的介面。 或者，您可以將介面從 UML Model Explorer 拖曳至類別圖，然後在圖表中新增作業和屬性。

### <a name="linking-between-components"></a>元件之間的連結
 使用相依性 (4) 顯示一個元件的需求可以由其他元件提供的作業或服務來滿足。

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>若要顯示提供的介面可以滿足需要的介面

1. 按一下工具箱中的 [**相依性**]。

2. 按一下需要的介面位於一個元件上的連接埠，然後按一下提供的介面位於其他元件的連接埠。

   您應嘗試避免設計相依性迴圈，其中群組中的每個元件都與其他所有元件相依。

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>若要將現有介面的連接埠加入至元件

- 在 [**UML 模型總管**] 中尋找介面，然後將該介面拖曳至元件。

     -或-

- 複製和貼上圖表中介面的參考。

    1. 在類別圖或元件圖上，以滑鼠右鍵按一下介面，然後按一下 [**複製**]。

    2. 在元件圖上，以滑鼠右鍵按一下元件，然後按一下 [**貼上參考**]。

         提供的介面隨即出現在元件上。 旁邊顯示動作標籤。

        > [!NOTE]
        > 如果使用 [**貼上**] 而非 [**貼上參考**]，則會建立具有新名稱的新介面。

    3. 如果想要建立需要的介面，請按一下動作標籤，然後按一下 [**轉換成需要的介面**]。

## <a name="Parts"></a>顯示元件的內部部分
 ![顯示內部部分的元件圖](../modeling/media/uml-compshowing.png "UML_CompShowing")

 您可以將組件 (3) 放置在元件 (1) 中，以顯示該元件是如何由彼此互動的較小型元件組成的。

 示範中的圖表說明類型為「立即進餐」Web 服務的每個執行個體都包含一個「客戶伺服器」執行個體和一個「廚房伺服器」執行個體。

 組件是其父元件的屬性 (Property)，與屬性 (Attribute) 屬於一般類別非常類似。 組件具有自己的類型，這通常也是一個元件。 組件的標籤具有與一般屬性相同的格式：

 `+ partName : TypeName`

 在父元件內，每個組件都會顯示針對其類型 (4、5) 定義的提供的介面和需要的介面。 一個組件需要的作業或服務可由其他組件提供。 您可以使用 [**組件組譯碼**] 連接器來顯示組件之間如何互相連接 (6)。

 您也可以顯示父元件的介面實際上是該介面其中一個組件所提供或需要的介面。 您可以使用 [**委派**] 關聯 (9)，將父項的連接埠連接至內部組件的連接埠。 兩個連接埠必須是相同類型 (提供的或要求的)，且介面類型應相容。

 您可以使用新類型或從現有類型建立新組件。

#### <a name="to-add-parts-to-a-component"></a>若要將組件加入至元件

1. 針對視為父元件一部分的每個主要功能單元，建立組件。

    1. 按一下工具箱上的 [**元件**]，然後按一下父元件 (1) 的內部。

         新組件 (3) 隨即出現在父元件內。

         即會在 [**UML 模型總管**] 中建立新元件。 這是新組件的類型。

         \-或-

         從 [UML 模型總管] 中，將現有元件拖曳至父元件。

         新組件 (3) 隨即出現在父元件內。 它的類型是從 [UML 模型總管] 中拖曳的元件。

         \-或-

         以滑鼠右鍵按一下圖表或 [UML 模型總管] 中的元件，然後按一下 [**複製**]。

         以滑鼠右鍵按一下父元件，然後按一下 [**貼上參考**]。

         新組件 (3) 隨即出現在父元件內。 它的類型是複製的元件。

    2. 按一下新組件的名稱以變更名稱。 您不能變更其類型。

    3. 您可以將提供的介面和需要的介面 (4、5) 加入至新組件。 按一下 [**提供的介面**] 或 [**需要的介面**] 工具，然後按一下組件。

         \-或-

         從 [**UML 模型總管**] 中，將現有介面拖曳至組件。

         介面會加入至組件的類型，並出現在組件自身上。 需要的話，父元件會調整其大小。

2. 將組件連接至另一個組件。

    - 使用 [**相依性**] 工具來連接不同組件 (6) 的連接埠。

3. 將組件連接至父元件的連接埠：

    1. 在父元件上建立一個或多個連接埠 (7)。 按一下工具箱上的 [**需要的介面**] 或 [**提供的介面**]，然後按一下父元件。

    2. 將連接埠委派 (9) 至一個或多個組件。 按一下 [**委派**] 工具，並按一下父元件上的連接埠，然後按一下組件上的連接埠。 您可以使用相同的方式，來連接提供或需要介面的連接埠。

### <a name="showing-the-parts-of-a-part"></a>顯示組件的部分
 在將元件分解為各個組件之後，您可以將每個組件類型分解為自己的內部組件。

 在個別元件圖中執行每個分解層是最容易的。 您必須首先找到組件的類型。 例如，在示範中，其中一個組件命名為 `DNCustomerServer`，而其類型是稱為 `CustomerServer` 的元件。 您可以在 [UML 模型總管] 中找到該類型，然後將其放置在其他圖表中。 然後，您可以建立其自己的內部組件。

##### <a name="to-place-a-parts-type-on-a-diagram"></a>若要將組件的類型放置在圖表上

1. 決定組件類型的完整限定名稱。

     以滑鼠右鍵按一下組件，然後按一下 [**屬性**]。

     類型名稱隨即出現在 [屬性] 視窗的 [**類型**] 欄位中。

2. 在 [**UML 模型總管**] 中找到組件的類型。

     按一下 [**檢視**]，指向 [**其他視窗**]，然後按一下 [**UML 模型總管**]。

     展開此類型屬於的專案和任何封裝 (必要的話)。

     類型會做為 [**元件**] 列出。

     必要時可以在這裡變更其名稱。

3. 開啟或建立其他元件圖。

4. 從 [UML 模型總管]，將類型拖曳至圖表。

     類型的檢視會顯示為圖表中的元件。

     它具有與您針對組件定義的相同介面。

     現在您可以在其中加入組件。

## <a name="Designing"></a>設計元件

### <a name="describing-how-the-parts-collaborate"></a>說明組件如何共同合作
 您可以繪製順序圖表，以顯示組件如何共同合作，以回應到達父元件的訊息。

 您可以使用這些圖表來說明現有元件，以及設計新元件。

 如果仍在設計元件，則可以繪製順序圖表，然後決定該圖表要包含哪些組件。 您可以使用順序圖表來實驗不同組件、需要的介面和訊息順序。 針對最常見最重要的流入訊息繪製順序圖表。 然後，您可以在元件中建立組件，對應至您已決定的各個生命線。

 使用順序圖表評定系統的工作如何在不同元件之間分佈。

- 如果太多工作堆積在一個組件，則與平均分佈工作相比，應用程式可能更難更新。

- 如果工作分佈太廣泛，且具有許多互動，則系統效能可能會變慢，且難於掌握。

  ![顯示共同作業元件的順序圖表](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>若要繪製順序圖表，以顯示組件之間的共同合作

1. 建立新的順序圖表。

     如需詳細資訊，請參閱 [UML 順序圖表：方針](../modeling/uml-sequence-diagrams-guidelines.md)。

2. 建立將訊息傳送至這個元件的外部元件、使用者、裝置或其他行動 (1) 的生命線。

     您可以將這個生命線的 [**行動**] 屬性設定為 true，以指出它在要考慮的元件之外。 生命線上隨即出現桿狀圖形。

3. 針對這個元件之提供的介面 (2) 建立生命線，選擇的行動會將訊息傳送給該元件。

4. 針對元件的每個組件 (3) 建立生命線。

5. 針對元件的每個需要的介面 (4) 建立生命線。

6. 從外部行動 (5) 繪製訊息。 顯示訊息如何傳遞給組件，以及它們如何共同合作以回應訊息。

7. 必要時，顯示傳送至需要的介面 (6) 的訊息。 不要顯示訊息執行內的任何詳細資料。

### <a name="is-the-component-more-than-its-parts"></a>元件多於組件嗎？
 在某些情況下，元件只是指定給組合部分集合的名稱。 所有工作都是組件執行的，且在執行階段沒有代表元件的程式碼或其他成品。

 您可以在模型中指出此項，方法是設定元件的 [**Is Indirectly Instantiated**] 屬性。 在此情況下，所有元件的介面都應在連接埠上，並委派至內部組件。

### <a name="describing-the-process-inside-each-part"></a>說明每個組件內的程序
 您可以使用活動圖來顯示元件如何處理每則流入訊息。 如需詳細資訊，請參閱 [UML 活動圖表：方針](../modeling/uml-activity-diagrams-guidelines.md)。

 ![具有資料緩衝區的活動圖](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 使用 [接受事件動作] (1) 顯示流入訊息啟動新的執行緒。

 使用物件節點和輸入/輸出連接來顯示資訊流程，以及顯示將資訊儲存在何處。 在範例中，物件節點 (2) 用於顯示在執行緒之間緩衝的項目。

### <a name="defining-data-and-classes"></a>定義資料和類別
 您可以使用 UML 類別圖描述下列項目的詳細內容：

- 元件的介面。 當您將要求和提供連接埠新增至元件時，介面會出現在 UML 模型總管中。 您可以將其拖曳或複製至 UML 類別圖中以顯示其屬性、作業，以及和其他介面的關聯性。

- 介面中傳送之作業參數中的資料。

- 元件中儲存的資料，例如活動圖中物件流程所示內容。

### <a name="general-dependencies-between-components"></a>元件之間的一般相依性
 您可以僅將元件圖用於顯示設計的主要組件及其相依性。

 ![元件之間的相依性](../modeling/media/uml-compdepend.png "UML_CompDepend")

 使用 [**相依性**] 工具繪製相依性。 這表示一個元件的設計依賴於另一個元件。

 相依性的典型類型包括下列項目：

- 一個元件呼叫其他元件內的程式碼。

- 一個元件具現化在其他類別中定義的類別。

- 一個元件使用其他元件建立的資訊。

  您可以使用相依性箭號的名稱，來表示特定類型的用法。 若要設定名稱，請以滑鼠右鍵按一下箭號，然後按一下 [**屬性**]，並設定屬性視窗中的 [**名稱**] 欄位。

## <a name="see-also"></a>另請參閱
 [編輯 uml 模型和圖表](../modeling/edit-uml-models-and-diagrams.md) [uml 元件圖](../modeling/uml-component-diagrams-reference.md)：參考 uml[順序圖](../modeling/uml-sequence-diagrams-reference.md)：參考 uml[使用案例圖](../modeling/uml-use-case-diagrams-reference.md)：參考 uml[類別圖](../modeling/uml-class-diagrams-reference.md)：參考[Uml 元件圖](../modeling/uml-component-diagrams-reference.md)：參考[影片：使用元件圖設計實體結構](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
