---
title: 自訂工具和工具箱
description: 瞭解如何為您想要讓使用者新增至其模型的元素定義工具箱專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 40341a0c74b371c4c84429474e58c7d338bb8059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935426"
---
# <a name="customizing-tools-and-the-toolbox"></a>自訂工具和工具箱

您必須針對要讓使用者加入至其模型的項目 (Element)，定義工具箱項目 (Item)。 工具有兩種類型：項目工具和連接工具。 在產生的設計工具中，使用者可以選取一個項目工具將圖形拖曳至圖表，也可以選取一個連接工具來繪製圖形之間的連結。 一般而言，項目工具可讓使用者將網域類別執行個體加入至其模型，而連接工具可讓使用者加入網域關聯性執行個體。

## <a name="how-the-toolbox-is-defined"></a><a name="ToolboxDef"></a> 工具箱的定義方式
 在 [DSL 總管] 中，展開 [編輯器] 節點和下方節點。 一般而言，您會看到類似如下的階層架構：

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

在 [DSL 總管] 的這個部分中，您可以：

- 建立新的索引標籤。 索引標籤定義工具箱中的區段標題。

- 建立新的工具。

- 複製並貼上工具。

- 在清單中向上或向下移動工具。

- 刪除索引標籤和工具。

> [!IMPORTANT]
> 若要在 [DSL 總管] 中加入或貼上項目，請以滑鼠右鍵按一下新節點的上兩層節點。 例如，若要加入工具，請以滑鼠右鍵按一下索引標籤，而不是 [ **工具** ] 節點。 若要加入索引標籤，請以滑鼠右鍵按一下 [ **編輯器** ] 節點。

每個工具的 [ **工具箱] 圖示** 屬性都會參考16個位圖檔案。 這些檔案通常會保留在 **Dsl\Resources** 資料夾中。

專案工具的 **類別** 屬性是指實體網域類別。 根據預設，該工具會建立這個類別的執行個體。 不過，您可以撰寫程式碼，讓工具建立項目群組或不同類型的項目。

連接工具的 **連接** 產生器屬性是指連接產生器，它會定義工具可連接的專案類型，以及在它們之間建立的關聯性。 連接產生器已定義為 [DSL 總管] 中的節點。 當您定義網域關聯性時，會自動建立連接產生器；不過您可以撰寫程式碼，來自訂這些產生器。

#### <a name="to-add-a-tool-to-the-toolbox"></a>將工具加入至工具箱

1. 您通常會先建立圖形類別並將其對應至網域類別，再建立項目工具。

     您通常會先建立連接線類別並將其對應至參考關聯性，再建立連接工具。

2. 在 [DSL Explorer] 中 ，展開 [編輯器 **]** 節點和 [工具箱索引標籤] 節點。

     以滑鼠右鍵按一下 [工具箱] 索引標籤節點，然後按一下 [ **加入新專案工具** ] 或 [ **加入新的連接工具**]。

3. 將 [ **工具箱] 圖示** 屬性設定為參考16x16 點陣圖。

     如果您想要定義新的圖示，請在 [ **Dsl\Resources** ] 資料夾的方案總管中建立點陣圖檔案。 檔案應該具有下列屬性值：**組建動作**  =  **內容**;**複製到輸出目錄**  = **請勿複製**。

4. **針對元素工具：** 將工具的 [ **類別** ] 屬性設定為參考對應到圖形的實體網域類別。

     **針對連接器工具：** 將工具的 [ **連接** 產生器] 屬性設定為下拉式清單中提供的其中一個專案。 當您將連接線對應至網域關聯性時，會自動建立連接產生器。 如果您最近剛建立連接線，通常會選取相關聯的連接產生器。

5. 若要測試 DSL，請按 F5 或 CTRL + F5，然後在 Visual Studio 的實驗實例中，開啟範例模型檔案。 新工具應顯示在工具箱上。 將工具拖曳至圖表上，驗證工具是否會建立新項目。

     如果工具沒有出現，請停止實驗性 Visual Studio。 在 Windows [ **開始** ] 功能表中，執行 **[重設 Microsoft Visual Studio 2010 實驗實例**]。 在 [建置] 功能表上，按一下 [重建方案]。 然後再測試一次 DSL。

## <a name="customizing-element-tools"></a><a name="customizing"></a> 自訂元素工具
 根據預設，此工具會建立指定類別的單一執行個體，但是您可以透過下列兩個方式來改變：

- 定義其他類別的 Element Merge 指示詞，讓這些類別接受這個類別的新執行個體，並讓這些類別在建立新項目時建立其他連結。 例如，您可以允許使用者將一個註解拖曳到另一個項目上，藉此建立兩者之間的參考連結。

     這些自訂也會影響當使用者貼上或拖放項目時所發生的狀況。

     如需詳細資訊，請參閱 [自訂元素建立和移動](../modeling/customizing-element-creation-and-movement.md)。

- 撰寫程式碼來自訂此工具，使其可以建立項目群組。 此工具是由您可以覆寫之 ToolboxHelper.cs 中的方法初始化。 如需詳細資訊，請參閱 [從工具建立元素群組](#groups)。

## <a name="creating-groups-of-elements-from-a-tool"></a><a name="groups"></a> 從工具建立元素群組
 每個項目工具包含該工具應建立的項目原型。 根據預設，每個項目工具會建立一個項目，但也可能透過一個工具來建立一組相關的物件。 若要執行這項操作，您可以使用內含相關項目的 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> 來初始化工具。

 下列範例取自內含電晶體類型的 DSL。 每個電晶體有三個具名端子。 電晶體的項目工具會儲存內含四個模型項目和三個關聯性連結的原型。 當使用者將工具拖曳至圖表上時，原型會具現化並連結至模型根。

 此程式碼會覆寫 **Dsl\GeneratedCode\ToolboxHelper.cs** 中定義的方法。

 如需使用程式碼自訂模型的詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="customizing-connection-tools"></a><a name="connections"></a> 自訂連接工具
 您通常會在建立新的連接線類別時，建立項目工具。 或者，您可以允許由兩個端點類型來決定關聯性類型，藉此多載一個工具。 例如，您可以定義一個連接工具，該工具可建立人與人的關聯性，以及人與鄉鎮的關聯性。

 連接工具會叫用連接產生器。 使用連接產生器可指定使用者在產生的設計工具中連結項目的方式。 連接產生器指定可連結的項目，以及在項目之間建立的連結類型。

 當您在網域類別之間建立參考關聯性時，會自動建立連接產生器。 您可以在對應連接工具時，使用此連接產生器。 如需如何建立連接工具的詳細資訊，請參閱設定 [工具箱](../modeling/customizing-tools-and-the-toolbox.md)。

 您可以修改預設連接產生器，讓產生器處理不同範圍的來源和目標類型，以及建立不同類型的關聯性。

 您也可以為連接產生器撰寫自訂程式碼，以指定連接的來源和目標類別、定義要建立的連接類型，以及執行與建立連接相關聯的其他動作。

### <a name="the-structure-of-connection-builders"></a>連接產生器的結構
 連接產生器包含一個或多個 Link Connect 指示詞，可指定網域關聯性以及來源和目標項目。 例如，在 [工作流程] 方案範本中，您可以在 [ **DSL Explorer**] 中看到 **CommentReferencesSubjectsBuilder** 。 此連接產生器包含一個名為 **CommentReferencesSubjects** 的 link connect 指示詞，它會對應至網域關聯性 **CommentReferencesSubjects**。 此 Link Connect 指示詞包含指向 `Comment` 網域類別的來源角色指示詞，以及指向 `FlowElement` 網域類別的目標角色指示詞。

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>使用連接產生器限制來源和目標角色
 您可以使用連接產生器，限制特定類別在指定網域關聯性之來源角色或目標角色中的發生次數。 例如，您可以有一個基底網域類別，內含對另一個網域類別的網域關聯性，但您可能不想讓該基底類別的所有衍生類別在該關聯性中具有相同角色。 在工作流程方案中，有四個具象的網域類別 (**StartPoint**、 **端點**、 **MergeBranch** 和 **同步** 處理) 直接繼承自抽象網域類別 **FlowElement**，以及兩個具象網域 **類別 (工作** 和 **ObjectInState**) ，間接繼承自它。 此外，也有 **流程** 參考關聯性，會在其來源角色和目標角色中採用 **FlowElement** 網域類別。 不過， **端點** 網域類別的實例不應該是 **流程** 關聯性實例的來源，也不應該是 **StartPoint** 類別的實例，就是 **流程** 關聯性實例的目標。 **FlowBuilder** 連接產生器具有名為 **Flow** 的 link connect 指示詞，可指定哪些網域類別可扮演來源 **角色 (工作**、 **MergeBranch**、 **StartPoint** 和 **同步**) ，而且可以 (**MergeBranch**、**端點** 和 **同步** 處理) 來播放目標角色。

### <a name="connection-builders-with-multiple-link-connect-directives"></a>使用多個 Link Connect 指示詞的連接產生器
 您可以將多個 Link Connect 指示詞加入至連接產生器。 這可協助您隱藏某些網域模型的複雜度，並防止 **工具箱** 變得太雜亂。 您可以針對數個不同的網域關聯性，將多個 Link Connect 指示詞加入至一個連接產生器。 不過，您應該將執行類似功能的網域關聯性合併在一起。

 在工作流程方案中， **flow** 連接工具是用來繪製 **流程** 和 **ObjectFlow** 網域關聯性的實例。 **FlowBuilder** 連接產生器除了稍早所述的 **Flow** link connect 指示詞之外，還有兩個名為 **ObjectFlow** 的連結連接指示詞。 這些指示詞會指定 **ObjectFlow** 關聯性的實例可在 **ObjectInState** 網域類別的實例之間繪製，或從 **ObjectInState** 的實例，而不是在工作的實例之間 **繪製，而** 不 **是在工作** 的兩個實例之間，或從工作的 **實例到** **ObjectInState** 的實例之間。 不過，可能會在工作的兩個實例之間繪製 **流程** 關聯性的 **實例。** 如果您編譯並執行工作流程方案，可以看到從 **ObjectInState** 實例到工作實例的繪製 **流程** 會建立 **ObjectFlow** 的實例，但是在兩 **個工作實例** 之間繪製 **流程****會建立****流程** 的實例。

### <a name="custom-code-for-connection-builders"></a>連接產生器的自訂程式碼
 使用者介面中有四個核取方塊，用於定義連接產生器的不同自訂類型：

- 來源或目標角色指示詞上的 [ **自訂接受** ] 核取方塊

- 來源或目標角色指示詞上的 [ **自訂連接]** 核取方塊

- connect 指示詞上的 [ **使用自訂連接]** 核取方塊

- 連接產生器的 **自訂** 屬性

  您必須提供一些程式碼來建立這些自訂。 若要探索必須提供的程式碼，請核取上述其中一個方塊，按一下 [轉換所有範本]，然後建置您的方案。 錯誤報告隨即產生。 按兩下錯誤報告，以檢視說明應加入之程式碼的註解。

> [!NOTE]
> 若要加入自訂程式碼，請使用與 GeneratedCode 資料夾中的程式碼檔案不同的程式碼檔案，建立部分類別定義。 為了避免遺失工作，請勿編輯產生的程式碼檔案。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。

#### <a name="creating-custom-connection-code"></a>建立自訂連接程式碼
 在每個連結連接指示詞中，[ **來源角色** 指示詞] 索引標籤會定義您可以拖曳的類型。 同樣地，[ **目標角色** 指示詞] 索引標籤會定義您可以拖曳的類型。 您可以針對每個類型，藉由設定 **自訂接受** 旗標，然後提供額外的程式碼，進一步指定是否允許該連結 connect 指示詞的連接 () 。

 您也可以自訂建立連接時所發生的狀況。 例如，您可以自訂拖曳出或拖曳至特定類別的單一案例，一個 Link Connect 指示詞管理的所有案例，或整個 FlowBuilder 連接產生器。 針對上述每個選項，您可以在適當層級設定自訂旗標。 當您轉換所有範本並嘗試建置方案時，會出現錯誤訊息，將您引導至所產生之程式碼中的註解。 這些註解指出您必須提供的程式碼。

 在「元件圖表」範例中，會自訂「連接」網域關聯性的連接產生器，限制只能在通訊埠之間建立連接。 下圖顯示您只能建立 `OutPort` 項目到 `InPort` 項目的連接，不過您可以讓元件彼此巢狀其中。

 **從巢狀元件連入 OutPort 的連接**

 ![連接產生器](../modeling/media/connectionbuilder_3.png)

 因此，您可能需要指定可從巢狀元件連接至 OutPort。 若要指定這類連接，您可以在 [ **DSL 詳細資料**] 視窗中，將 [ **InPort** 類型] 上的 [**使用自訂接受**] 設定為 [來源角色]，並使用 [ **OutPort** 類型] 作為 [目標角色]，

 **[DSL 總管] 中的 Link Connect 指示詞**

 ![連接產生器影像](../modeling/media/connectionbuilder_4a.png)

 **[DSL 詳細資料] 視窗中的 Link Connect 指示詞**

 ![[DSL 詳細資料] 視窗中的 Link connect 指示詞](../modeling/media/connectionbuilder_4b.png)

 您必須接著提供 ConnectionBuilder 類別中的方法：

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 如需使用程式碼自訂模型的詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

 例如，您可以使用類似的程式碼，防止使用者建立具有父子連結的迴圈。 這些限制會被視為「硬式」條件約束，因為使用者隨時無法違反這些限制。 您也可以建立無法儲存的無效設定，以建立使用者可以暫時略過的「軟」驗證檢查。

### <a name="good-practice-in-defining-connection-builders"></a>定義連接產生器的最佳做法
 您應該只在不同類型的關聯性在概念上相關時，才定義一個連接產生器來建立不同類型的關聯性。 在工作流程範例中，您使用同一個產生器來建立工作與工作之間，以及工作與物件之間的流程。 不過，使用同一個產生器來建立註解與工作之間的關聯性，可能會造成混淆。

 如果您要定義用於多種關聯性類型的連接產生器，請確保該產生器不會對應至同一組來源和目標物件中的多種類型； 否則可能會發生無法預期的結果。

 您可以使用自訂程式碼來套用「硬式」條件約束，但您應該考慮使用者是否應該能夠暫時進行不正確連接。 如果應該，您可以修改條件約束，在使用者嘗試儲存變更之前都不會驗證連接。

## <a name="see-also"></a>另請參閱

- [自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)
- [自訂複製行為](../modeling/customizing-copy-behavior.md)
- [如何：加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [電路圖範例 DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
