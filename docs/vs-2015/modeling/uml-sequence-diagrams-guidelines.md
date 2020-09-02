---
title: UML 順序圖表：指導方針 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cdd853307bdea28c48762a6a3f0416e698b577ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850128"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sequence Diagrams: Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，您可以繪製 *順序圖表* 來顯示互動。 互動是類別、元件、子系統或行動之一般執行個體間的一連串訊息。

 UML 循序圖是 UML 模型的一部分，而且只存在於 UML 模型專案內。 若要建立 UML 順序圖表，請按一下 [ **架構** ] 功能表上的 [ **新增 UML 或分層圖**]。 深入瞭解 [uml 順序圖表元素](../modeling/uml-sequence-diagrams-reference.md) 或 [uml 模型圖](../modeling/edit-uml-models-and-diagrams.md) 一般。 如需影片示範，請參閱 [使用順序圖表 (2010) 的草繪互動 ](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams)。

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="in-this-topic"></a>本主題內容
 [使用 UML 循序圖](#Using)

 [繪製循序圖的基本步驟](#BasicSteps)

 [建立和使用簡單循序圖](#Simple)

 [類別和生命線](#ClassesAndLifelines)

 [建立可重複使用的互動序列](#Multiple)

 [摺疊生命線群組](#Collapse)

 [描述含片段的控制結構](#Fragments)

## <a name="using-uml-sequence-diagrams"></a><a name="Using"></a> 使用 UML 順序圖表
 您可以將循序圖用於不同程式詳細程度的各種用途。 繪製循序圖的一般情況如下：

- 如果您的使用案例圖彙總系統使用者和其目標，則可以繪製循序圖來描述系統的主要元件如何互動以滿足每個使用案例的目標。 如需詳細資訊，請參閱 [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)。

- 如果您已識別到達元件之介面的訊息，則可以繪製循序圖來描述元件的內部組件如何互動以達成每個內送訊息所需的結果。 如需詳細資訊，請參閱 [UML 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)。

  繪製循序圖具有數個優點：

- 您可以輕鬆地查看工作如何分散在各元件之間。

- 您可以識別很難更新軟體的互動模式。

## <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性
 您可以透過數種方式來搭配使用 UML 循序圖與其他圖表。

#### <a name="lifelines-and-types"></a>生命線和類型
 您在循序圖中繪製的生命線可以代表系統中元件或類別的一般執行個體。 您可以從類型建立生命線、從生命線建立類型，並在 UML 類別圖和 UML 元件圖上顯示類型。 如需詳細資訊，請參閱 [類別和生命線](#ClassesAndLifelines)。

#### <a name="parameter-types"></a>參數類型
 您也可以在 UML 類別圖中描述參數類型以及生命線之間傳送之訊息中所使用的傳回值。

#### <a name="use-case-details"></a>使用案例詳細資料
 使用案例代表使用者目標，以及達成目標的一連串步驟。 您可以使用數種方式來描述這一連串的步驟。 其中一個選項是繪製循序圖，以顯示使用者與系統主要元件之間的互動。 如需詳細資訊，請參閱 [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)。

## <a name="basic-steps-for-drawing-sequence-diagrams"></a><a name="BasicSteps"></a> 繪製順序圖表的基本步驟
 如需順序圖表上元素的完整清單，請參閱 [UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)。

> [!NOTE]
> [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)中說明如何建立任何模型圖表的詳細步驟。

#### <a name="to-create-a-sequence-diagram"></a>建立循序圖

1. 在 [ **架構** ] 功能表上，按一下 [ **新增 UML 或分層圖**]。

2. 在 [ **範本**] 底下，按一下 [ **UML 順序圖表**]。

3. 命名圖表。

4. 在 [ **加入至模型專案**] 中，選取方案中的現有模型專案，或 **建立新的模型專案**，然後按一下 **[確定]**。

    具有 **順序圖表** 工具箱的新順序圖表隨即出現。 工具箱包含需要的項目和接頭。

   ![順序圖表的各部分](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>繪製循序圖

1. 將 [ **生命線** ] (1) 從 [ **工具箱** ] 拖曳到圖表上，以代表類別、元件、動作專案或裝置的實例。

    > [!NOTE]
    > 您也可以將現有的類別、介面、執行者或元件從 **UML 模型瀏覽器** 拖曳到圖表上，以建立生命線。 這會建立生命線，以代表所選擇類型的執行個體。

2. 繪製訊息，以顯示生命線如何協作以達成特定目標。

     若要建立訊息 (3、4、6、7)，請按一下訊息工具。 然後按一下訊息開始處的傳送端生命線，接著按一下接收端生命線。

     執行出現次數 (5) 會出現在接收端生命線。 執行出現次數代表執行個體執行方法的期間。 您可以建立從執行出現次數開始的其他訊息。

3. 若要顯示來自未知事件來源 (9) 或廣播給未知收件者 (10) 的訊息，請繪製圖表上傳送至空白空間或從中接收的非同步訊息。 這些訊息 *稱為 (9) 的訊息，* 以及 (10) 的 *遺失訊息* 。

    > [!NOTE]
    > 若要移動已遺失或已找到訊息的生命線群組，請遵循下列步驟來選取生命線，然後移動它們：在這些生命線周圍繪製矩形，或在按一下每個生命線時按住 **CTRL** 鍵。 如果您使用 [**全選**] 或**CTRL** + **A**選取所有生命線，然後移動它們，則附加至這些生命線的任何遺失或找到的訊息都不會移動。 如果發生此案例，則您可以分別移動這些訊息。

4. 為送至相同元件或系統的每個主要訊息，繪製循序圖。

#### <a name="to-change-the-order-of-messages"></a>變更訊息的順序

- 在生命線中，向上或向下拖曳訊息。 您可以將它拖曳至其他訊息上方，或拖曳至或拖曳離開執行區塊。

     \- 或 -

- 按一下該訊息，然後使用 **向上鍵** 和 **向下** 鍵來調整訊息位置。 使用 **shift + 向上鍵** 和 **shift + 向下鍵** 來變更訊息的順序。

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>移動或複製循序圖上的訊息順序

1. 以滑鼠右鍵按一下訊息 (3，4) 然後按一下 [ **複製**]。

2. 以滑鼠右鍵按一下執行發生次數 (5) 或生命線 (1) 您要從中傳送新訊息，然後按一下 [ **貼**上]。 如果想要的話，新的寄件者可以在不同的圖表上。

     訊息和其所有附屬訊息的副本會加入執行出現次數或生命線的結尾。

    > [!NOTE]
    > 貼上的訊息永遠會出現在執行出現次數或生命線的結尾。 貼上之後，即可將它拖曳至先前的位置。

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>顯示和編輯訊息的簽章文字

- 目標生命線必須繫結或對應至類型，才會顯示簽章文字。 若要完成這項作業，請執行下列其中一個步驟：

  - 以滑鼠右鍵按一下生命線，然後選擇 [ **建立類別**]。

     -或-

  - 選取生命線，按 **F4**，然後在 [ **屬性** ] 視窗中，將 [ **類型** ] 屬性設定為現有的類型或指定新類型的名稱。 以滑鼠右鍵按一下 [訊息] 標籤，然後選擇 [ **建立**作業]。

    簽章文字會出現在訊息標籤下方。 現在，您可以編輯簽章文字。 如需詳細資訊，請參閱 [類別和生命線](#ClassesAndLifelines)。

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>改善循序圖的版面配置

- 以滑鼠右鍵按一下圖表的空白部分，然後按一下 [ **重新整理版面**配置]。

- 若要復原操作，請按一下 [ **編輯**]，然後按一下 [ **復原**]。

#### <a name="to-change-the-package-that-owns-the-interaction"></a>變更擁有互動的套件

1. 在 [ **UML 模型瀏覽器**] 中，尋找順序圖表顯示的互動。

    > [!NOTE]
    > 除非您將第一個生命線新增至順序圖表，否則互動不會出現在 [ **UML 模型瀏覽器** ] 中。

2. 將互動拖曳至套件。

     \- 或 -

     在 [互動] 上按一下滑鼠右鍵，然後按一下 [ **剪**下]。 以滑鼠右鍵按一下封裝，然後按一下 [ **貼**上]。

## <a name="creating-and-using-simple-sequence-diagrams"></a><a name="Simple"></a> 建立和使用簡單順序圖表
 最簡單且最廣泛使用的循序圖形式僅包含生命線和訊息。 這類型的圖表可讓您清楚地顯示設計中物件之間或系統與其使用者之間的一般互動系列。 這通常就足以協助您討論和溝通設計。

 以下是您繪製簡單循序圖時必須考慮一些事項。

### <a name="types-of-message"></a>訊息類型
 有三種工具可用來建立訊息。

- 使用 [ **同步** ] 工具描述傳送者等待接收者傳迴響應 (3) 的互動。

     在 **<\<return>>** 執行發生的結束時，會顯示箭號。 它指出將控制權傳回給寄件者。

- 使用 **非同步** 工具描述傳送者可以立即繼續的互動，而不需等待接收器 (4) 。

- 您可以使用 [ **建立** ] 工具來描述傳送者建立接收者 (8) 的互動。

     建立訊息應該是接收者收到的第一個訊息。

### <a name="annotating-the-interactions"></a>加入互動的附註
 若要描述序列的詳細資訊，您可以將 **批註** 放在圖表上的任何位置。

 使用 **批註連結**，您可以將批註連結至生命線、執行、互動使用和片段。

> [!CAUTION]
> 想要將註解附加至序列中的特定點時，請將它連結至執行出現次數、互動使用或片段。 請不要將它連結至生命線，因為，在此情況下，它不會附加至序列中的正確點。

 使用註解：

- 注意已在序列中的關鍵點達成的項目。 這可協助讀者看到互動目標。

- 描述整個序列的整體目標。 將註解附加至初始執行出現次數，或將它卸離。 例如，"Customer has chosen items from the menu and has been given a price"。

- 描述每個生命線的責任。 將註解附加至生命線。 例如，"Ordering Manager collects the customer's menu choices"。

- 請注意例外狀況或可能會執行為所顯示一般序列的替代方案。 例如，"Customer can choose to skip the rest of this sequence"。

  - 請考慮使用片段做為這類附註的更正式替代方案。 請參閱 [使用片段描述控制項結構](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>決定圖表範圍
 請務必清楚了解圖表想要顯示的內容。

#### <a name="initiating-event"></a>啟始事件
 每個圖表都應該顯示某個啟始事件所導致的一連串互動。 例如，這可能是：

- 啟始使用案例的使用者，例如，開啟購買餐點的網頁。

- 從某個系統元件到另一個系統元件的訊息，例如，查詢客戶想要購買之項目的可用性。

- 透過狀態變更所觸發的事件，例如，股票低於臨界值的項目。

#### <a name="level-of-detail"></a>詳細資料層級
 循序圖可以顯示不同的詳細資料層級。 您幾乎可以獨立決定兩個不同維度中的詳細資料層級：

 生命線可以代表其中一種詳細資料層級：

- 現有或正在開發之程式碼中的物件。

- 元件或其子元件，通常會省略 Facade、Proxy 和其他連線機制。

- 您的系統與外部行動

  訊息可以代表其中一種詳細資料層級：

- 程式碼、API 或 Web 介面中的軟體訊息。

- 例如，使用者與系統之間或程式碼與資料庫之間的交易或子交易。

- 使用案例 - 使用者與系統之間的主要互動。

  不論探索現有程式碼還是描述新的設計，繪製和討論較不詳細的檢視通常十分有用。

## <a name="describing-variations"></a>描述變化
 此圖表顯示單一一般事件序列。 如果您想要顯示替代可能性 (例如失敗情況)，則可以使用其中一個選項：

- 繪製不同的循序圖來描述這些案例。

- 使用 [描述具有片段的控制項結構](#Fragments) 來顯示迴圈、替代專案等等。

## <a name="assessing-the-design"></a>評估設計
 您可以使用圖表來評估工作在其物件或元件之間的分佈。 如果您看到這些模式，請考慮進行重整：

- 某個生命線似乎透過呼叫所有項目來執行所有工作，其他生命線則只會被動回應。

- 跨生命線的許多訊息。 每個生命線都應該只將訊息傳送至幾個鄰接項目，而且不應該與相鄰的鄰接項目通訊。 通常應該可以排列生命線，讓訊息只有在幾個地方才能跨生命線，而且，如果發生這種跨越情況，目標生命線也不應該交換具有跨生命線的訊息。

- 有些生命線似乎處理多種類型的工作。 應該可以輕鬆地找到一個簡潔的句子來描述每個生命線的責任，並彙總回應所收到之每個訊息所執行的工作。

## <a name="classes-and-lifelines"></a><a name="ClassesAndLifelines"></a> 類別和生命線
 循序圖中的生命線顯示類別或元件介面的執行個體。 您可以使用兩種方式來命名生命線：

|**針對這個用途**|**使用此格式**|
|--------------------------|-------------------------|
|類型的匿名執行個體。<br /><br /> 如果每種類型都只有一個生命線，請使用此項目。|*typeName*|
|類型的具名執行個體。<br /><br /> 如果您想要顯示的系列包含相同類型的多個執行個體，請使用此項目。|*objectName*：*typeName*|

### <a name="creating-lifelines-from-types"></a>從類型建立生命線
 您可以從已定義的類別建立新的生命線 (例如在類別圖上)。

> [!NOTE]
> 請確定您有現有循序圖，再執行這項工作。

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>從現有類型建立生命線

- 將類別、元件或介面從 [UML 模型總管] 拖曳至循序圖。

   \- 或 -

  1. 以滑鼠右鍵按一下其個別圖表上的類別、元件或介面，然後按一下 [ **建立生命線**]。

  2. 在 [ **建立生命線** ] 對話方塊中，選取順序圖表，然後按一下 **[確定]**。

     新的具名執行個體生命線隨即出現，而其類型就是您所拖曳的類型。

  > [!NOTE]
  > 您可以依需要重複此動作多次。 這會建立具有不同執行個體名稱的生命線。

##### <a name="to-change-the-type-of-a-lifeline"></a>變更生命線的類型

1. 以滑鼠右鍵按一下生命線，然後按一下 [ **屬性**]。

2. 在 [ **屬性** ] 視窗中，設定 [ **類型** ] 屬性。 您可以從下拉式功能表中選取類型，或輸入新的名稱。

### <a name="creating-classes-from-lifelines"></a>從生命線建立類別
 建立一或多個循序圖時，從生命線建立類別或介面，即可彙總生命線。

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>從生命線建立類別或介面

1. 以滑鼠右鍵按一下生命線，然後按一下 [ **建立類別** ] 或 [ **建立介面**]。

     新的類別或介面會出現在 [UML 模型總管] 中。

2. 在生命線所收到之每個訊息的類別或介面中建立作業：

    1. 選取您想要包括的所有訊息。

    2. 在其中一個訊息上按一下滑鼠右鍵，然後按一下 [ **建立方法**]。

         新的類別或介面都有每個所選取訊息的作業。

         作業名稱會出現在每個訊息箭號下方，以及訊息的 **operation** 屬性中。

         如果您的訊息包括 "(parameter: type)" 形式的參數，則參數會出現在新作業的參數清單中。

        > [!NOTE]
        > 如果您在循序圖中加入新的訊息，則必須重複此步驟。

3. 若要詳細檢視新的類別或介面，請將它加入類別圖或元件圖。

    1. 開啟或建立類別圖或元件圖。

    2. 將新的類別或介面從 [ **UML 模型瀏覽器** ] 拖曳至類別圖。

         類別或介面會出現在類別圖中。

         \- 或 -

    3. 將新介面從 [ **UML 模型瀏覽器** ] 拖曳至元件圖中的元件或埠。

         介面會以棒棒糖符號出現在元件上。

### <a name="creating-classes-for-parameters"></a>建立參數的類別
 您可以在循序圖的訊息中包括參數。 您可以使用 UML 類別圖描述參數類型。

## <a name="creating-reusable-interaction-sequences"></a><a name="Multiple"></a> 建立可重複使用的互動順序
 您可以使用個別的圖表來描述序列，其中包含您想要區分出來或在數個圖表之間共用的詳細資料。

 您可以在某個圖表上建立一個指向另一個圖表中詳細資料的互動使用矩形 (12)。

 按兩下 [互動使用]，開啟與其連結的循序圖。

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>從現有生命線建立可重複使用的互動序列

1. 在 [ **工具箱**] 中，按一下 [ **互動使用**]。

2. 在循序圖上，按住滑鼠按鈕並跨您想要包括在可重複使用序列中的生命線進行拖曳。 從您想要插入互動使用的垂直位置開始。

     循序圖上所選取的生命線之間會出現互動使用。

3. 按兩下互動使用上的名稱，然後將它重新命名以描述可重複使用序列在此圖表中的影響。

     \- 或 -

     使用參數撰寫名稱 (如函式呼叫)。

4. 將互動使用連結至另一個循序圖。 以滑鼠右鍵按一下互動使用，然後：

     按一下 [ **建立新序列** ] 以建立新的順序圖表

     \- 或 -

     按一下 [ **連結至順序** ] 連結至現有的圖表。

     Visual Studio 會建立互動使用與新互動序列之間的連結。

     新的循序圖會出現在您的方案中。 它包含您用來建立互動使用的生命線。

    > [!NOTE]
    > 只會包括您用來建立互動使用的生命線。 新的圖表將不會包括您在互動使用之後所建立的生命線，即使互動使用現在涵蓋它們也是一樣。

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>從現有訊息建立可重複使用的序列

- 以滑鼠右鍵按一下您要移動的訊息，然後按一下 [ **移至圖表**]。

  Visual Studio：

  - 將所選取的訊息和任何附屬訊息取代為互動使用。

  - 將已取代的訊息移至新的循序圖。

  - 會建立互動使用與新循序圖之間的連結。

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>瀏覽至互動使用所參考的序列

- 按兩下互動使用。

     \- 或 -

     以滑鼠右鍵按一下互動使用，然後按一下 [ **移至順序**]。

### <a name="creating-a-placeholder-with-an-interaction-use"></a>使用互動使用建立預留位置
 您可以建立互動使用，而不需要將它連結至另一個圖表。 您可以使用它做為某個順序的預留位置，而該部分的詳細資料尚未經過處理。使用互動使用的名稱來指出您想要的結果。

## <a name="collapsing-groups-of-lifelines"></a><a name="Collapse"></a> 折迭生命線群組
 您可以將一組生命線摺疊在一起，讓群組顯示為一個生命線。 這可協助您將一組物件視覺化為單一元件。 會隱藏摺疊群組中生命線之間的訊息和互動使用。 會顯示包含其他生命線的訊息和互動序列。

#### <a name="to-collapse-a-group-of-lifelines-together"></a>將一組生命線摺疊在一起

1. 選取兩個或多個生命線。

2. 以滑鼠 **按右鍵其中**一個，然後按一下 [折迭]。

     個別的生命線會取代為單一生命線。

     會隱藏只包含群組成員的訊息和互動使用。

3. 若要重新命名群組，請按一下名稱。

    > [!NOTE]
    > 展開群組時，會遺失群組名稱。

#### <a name="to-expand-a-collapsed-group"></a>展開已摺疊的群組

- 以滑鼠右鍵按一下折迭的生命線，然後按一下 [ **展開**]。

    > [!NOTE]
    > 將會遺失群組名稱，以及任何從群組到註解或工作項目的連結。

## <a name="describing-control-structures-with-fragments"></a><a name="Fragments"></a> 使用片段描述控制項結構
 您可以在循序圖中使用合併片段 (13) 來定義迴圈、分支和並行處理。 或者，請改成考慮使用活動圖。 活動圖不適用於在行動之間顯示訊息，但在某些情況下適用於顯示迴圈、分支和並行。

 如需片段類型的完整清單，請參閱 [以 UML 順序圖表上的片段描述控制流程](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)。

#### <a name="to-create-a-combined-fragment"></a>建立合併片段

1. 選取一則訊息，或一系列全由相同執行出現次數或生命線開始的訊息。

    > [!NOTE]
    > 選取訊息箭號，而非訊息所指向的執行出現次數。

2. 以滑鼠右鍵按一下其中一個訊息，並指向 [ **環繞**]，然後按一下您需要的片段類型。

     新的片段隨即出現。 它會包含您所選取的訊息。

     如果合併片段類型允許多個片段，則也會出現空的片段。

3. 若要設定片段的保護，請以滑鼠右鍵按一下片段框線，然後按一下 [ **屬性**]。 設定 **Guard** 屬性。

     成立條件用來定義分支或迴圈的條件。

4. 若要將新片段新增至允許多個片段的類型，請以滑鼠右鍵按一下片段的界限，然後指向 [ **新增**]。 按一下 [After **互動運算元** ] 或 [ **互動運算元**]。

5. 若要將新訊息加入片段中，請使用訊息工具，或進行複製並貼上。

## <a name="see-also"></a>另請參閱
 [Uml 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)[編輯 uml 模型和圖表](../modeling/edit-uml-models-and-diagrams.md) [UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)Uml[類別圖表](../modeling/uml-class-diagrams-reference.md)：參考 uml[元件](../modeling/uml-component-diagrams-reference.md)圖：參考[Uml 元件圖表](../modeling/uml-component-diagrams-reference.md)：參考[影片：使用順序圖表的草繪互動](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases)
