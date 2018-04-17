---
title: 自訂工具和 [工具箱] |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0644aa33d0e091fc3a2ff856109fe9661e2dc805
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-tools-and-the-toolbox"></a>自訂工具和工具箱
您必須針對要讓使用者加入至其模型的項目 (Element)，定義工具箱項目 (Item)。 工具有兩種類型：項目工具和連接工具。 在產生的設計工具中，使用者可以選取一個項目工具將圖形拖曳至圖表，也可以選取一個連接工具來繪製圖形之間的連結。 一般而言，項目工具可讓使用者將網域類別執行個體加入至其模型，而連接工具可讓使用者加入網域關聯性執行個體。  
  
 本主題內容：  
  
-   [[工具箱] 中的定義方式](#ToolboxDef)  
  
-   [自訂項目工具](#customizing)  
  
-   [從工具中建立項目群組](#groups)  
  
-   [自訂連接工具](#connections)  
  
##  <a name="ToolboxDef"></a> 工具箱 中的定義方式  
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
  
-   建立新的索引標籤。 索引標籤定義工具箱中的區段標題。  
  
-   建立新的工具。  
  
-   複製並貼上工具。  
  
-   在清單中向上或向下移動工具。  
  
-   刪除索引標籤和工具。  
  
> [!IMPORTANT]
>  若要在 [DSL 總管] 中加入或貼上項目，請以滑鼠右鍵按一下新節點的上兩層節點。 例如，若要新增一項工具，以滑鼠右鍵按一下索引標籤上，而非**工具**節點。 若要加入索引標籤，以滑鼠右鍵按一下**編輯器**節點。  
  
 **工具箱圖示**屬性每個工具的參考是 16 x 16 的點陣圖檔案。 這些檔案通常會保留在**Dsl\Resources**資料夾。  
  
 **類別**項工具的屬性參考到具象的領域類別。 根據預設，該工具會建立這個類別的執行個體。 不過，您可以撰寫程式碼，讓工具建立項目群組或不同類型的項目。  
  
 **連接產生器**連線工具的屬性是指定義哪些類型的項目都可以連線工具，以及哪些關聯性會建立它們之間的連接產生器。 連接產生器已定義為 [DSL 總管] 中的節點。 當您定義網域關聯性時，會自動建立連接產生器；不過您可以撰寫程式碼，來自訂這些產生器。  
  
#### <a name="to-add-a-tool-to-the-toolbox"></a>將工具加入至工具箱  
  
1.  您通常會先建立圖形類別並將其對應至網域類別，再建立項目工具。  
  
     您通常會先建立連接線類別並將其對應至參考關聯性，再建立連接工具。  
  
2.  在 [DSL 總管] 中，展開**編輯器**節點和**工具箱索引標籤**節點。  
  
     [工具箱] 索引標籤] 節點中，以滑鼠右鍵按一下，然後按一下 [**加入新項目工具**或**加入新的連接工具**。  
  
3.  設定**工具箱圖示**屬性來參照 16 x 16 點陣圖。  
  
     如果您想要定義新的圖示，請在 [方案總管] 中建立點陣圖檔案**Dsl\Resources**資料夾。 檔案應該具有下列屬性值：**建置動作** = **內容**;**複製到輸出目錄** = **不要複製**。  
  
4.  **項目工具：**設定**類別**工具的參考會對應至圖形的具象網域類別的屬性。  
  
     **連接器工具：**設定**連接產生器**工具的其中一個項目下拉式清單中所提供的屬性。 當您將連接線對應至網域關聯性時，會自動建立連接產生器。 如果您最近剛建立連接線，通常會選取相關聯的連接產生器。  
  
5.  若要測試 DSL，請按 F5 鍵或 CTRL+F5，然後在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的實驗執行個體中開啟範例模型檔案。 新工具應顯示在工具箱上。 將工具拖曳至圖表上，驗證工具是否會建立新項目。  
  
     如果工具未出現，請停止實驗 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在 Windows 中**啟動**功能表上，執行**重設 Microsoft Visual Studio 2010 實驗執行個體**。 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**建置**功能表上，按一下 **重建方案**。 然後再測試一次 DSL。  
  
##  <a name="customizing"></a> 自訂項目工具  
 根據預設，此工具會建立指定類別的單一執行個體，但是您可以透過下列兩個方式來改變：  
  
-   定義其他類別的 Element Merge 指示詞，讓這些類別接受這個類別的新執行個體，並讓這些類別在建立新項目時建立其他連結。 例如，您可以允許使用者將一個註解拖曳到另一個項目上，藉此建立兩者之間的參考連結。  
  
     這些自訂也會影響當使用者貼上或拖放項目時所發生的狀況。  
  
     如需詳細資訊，請參閱[自訂項目建立及移動](../modeling/customizing-element-creation-and-movement.md)。  
  
-   撰寫程式碼來自訂此工具，使其可以建立項目群組。 此工具是由您可以覆寫之 ToolboxHelper.cs 中的方法初始化。 如需詳細資訊，請參閱[建立群組的項目從工具](#groups)。  
  
##  <a name="groups"></a> 從工具中建立項目群組  
 每個項目工具包含該工具應建立的項目原型。 根據預設，每個項目工具會建立一個項目，但也可能透過一個工具來建立一組相關的物件。 若要執行這項操作，您可以使用內含相關項目的 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> 來初始化工具。  
  
 下列範例取自內含電晶體類型的 DSL。 每個電晶體有三個具名端子。 電晶體的項目工具會儲存內含四個模型項目和三個關聯性連結的原型。 當使用者將工具拖曳至圖表上時，原型會具現化並連結至模型根。  
  
 此程式碼會覆寫方法中定義**Dsl\GeneratedCode\ToolboxHelper.cs**。  
  
 如需使用程式碼以自訂模型的詳細資訊，請參閱[巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
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
  
##  <a name="connections"></a> 自訂連接工具  
 您通常會在建立新的連接線類別時，建立項目工具。 或者，您可以允許由兩個端點類型來決定關聯性類型，藉此多載一個工具。 例如，您可以定義一個連接工具，該工具可建立人與人的關聯性，以及人與鄉鎮的關聯性。  
  
 連接工具會叫用連接產生器。 使用連接產生器可指定使用者在產生的設計工具中連結項目的方式。 連接產生器指定可連結的項目，以及在項目之間建立的連結類型。  
  
 當您在網域類別之間建立參考關聯性時，會自動建立連接產生器。 您可以在對應連接工具時，使用此連接產生器。 如需如何建立連接工具的詳細資訊，請參閱[設定工具箱](../modeling/customizing-tools-and-the-toolbox.md)。  
  
 您可以修改預設連接產生器，讓產生器處理不同範圍的來源和目標類型，以及建立不同類型的關聯性。  
  
 您也可以為連接產生器撰寫自訂程式碼，以指定連接的來源和目標類別、定義要建立的連接類型，以及執行與建立連接相關聯的其他動作。  
  
### <a name="the-structure-of-connection-builders"></a>連接產生器的結構  
 連接產生器包含一個或多個 Link Connect 指示詞，可指定網域關聯性以及來源和目標項目。 例如，在這個工作流程方案範本時，您可以看到**CommentReferencesSubjectsBuilder**中**DSL 總管**。 此連接產生器包含一個連結連線指示詞**CommentReferencesSubjects**，這會對應到網域關係**CommentReferencesSubjects**。 此 Link Connect 指示詞包含指向 `Comment` 網域類別的來源角色指示詞，以及指向 `FlowElement` 網域類別的目標角色指示詞。  
  
### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>使用連接產生器限制來源和目標角色  
 您可以使用連接產生器，限制特定類別在指定網域關聯性之來源角色或目標角色中的發生次數。 例如，您可以有一個基底網域類別，內含對另一個網域類別的網域關聯性，但您可能不想讓該基底類別的所有衍生類別在該關聯性中具有相同角色。 在工作流程方案中，有四個網域具象類別 (**StartPoint**，**端點**， **MergeBranch**，和**同步**)，直接繼承自抽象的領域類別**FlowElement**，和兩個實體的網域類別 (**工作**和**ObjectInState**)，間接繼承自它。 另外還有**流程**參考關聯性，會採用**FlowElement**中其來源角色和目標角色的網域類別。 不過，執行個體**端點**網域類別不能執行個體的來源**流程**關聯性，也應該執行個體不**StartPoint**類別是目標執行個體**流程**關聯性。 **FlowBuilder**連接產生器有連線指示詞的連結**流程**指定的網域類別可以播放來源角色 (**工作**， **MergeBranch**， **StartPoint**，和**同步**) 和它可以播放的目標角色 (**MergeBranch**， **端點**，和**同步**)。  
  
### <a name="connection-builders-with-multiple-link-connect-directives"></a>使用多個 Link Connect 指示詞的連接產生器  
 您可以將多個 Link Connect 指示詞加入至連接產生器。 這可協助您隱藏某些使用者的網域模型的複雜性，並讓**工具箱**爆太。 您可以針對數個不同的網域關聯性，將多個 Link Connect 指示詞加入至一個連接產生器。 不過，您應該將執行類似功能的網域關聯性合併在一起。  
  
 在工作流程方案中，**流程**連接工具用來繪製兩個執行個體**流程**和**物件流程**網域關聯性。 **FlowBuilder**連接產生器對，此外**流程**連結連線稍早所述的指示詞，兩個連結連線名為指示詞**物件流程**。 這些指示詞指定的執行個體**物件流程**關聯性的執行個體之間繪製**ObjectInState**網域類別或執行個體的**ObjectInState**的執行個體**工作**，但不是介於兩個執行個體**工作**，或從執行個體**工作**的執行個體**ObjectInState**。 不過，執行個體**流程**關聯性可能會繪製兩個執行個體之間**工作**。 如果您編譯和執行工作流程方案時，您可以看到該繪圖**流程**的執行個體從**ObjectInState**的執行個體**工作**建立的執行個體**物件流程**，但繪圖**流程**的兩個執行個體之間**工作**建立的執行個體**流程**。  
  
### <a name="custom-code-for-connection-builders"></a>連接產生器的自訂程式碼  
 使用者介面中有四個核取方塊，用於定義連接產生器的不同自訂類型：  
  
-   **自訂接受**來源或目標的角色指示詞上的核取方塊  
  
-   **自訂連接**來源或目標的角色指示詞上的核取方塊  
  
-   **使用自訂連接**連線指示詞上的核取方塊  
  
-   **是自訂**連接產生器的屬性  
  
 您必須提供一些程式碼來建立這些自訂。 若要探索必須提供的程式碼，請核取上述其中一個方塊，按一下 [轉換所有範本]，然後建置您的方案。 錯誤報告隨即產生。 按兩下錯誤報告，以檢視說明應加入之程式碼的註解。  
  
> [!NOTE]
>  若要加入自訂程式碼，請使用與 GeneratedCode 資料夾中的程式碼檔案不同的程式碼檔案，建立部分類別定義。 為了避免遺失工作，請勿編輯產生的程式碼檔案。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。  
  
#### <a name="creating-custom-connection-code"></a>建立自訂連接程式碼  
 在 [每個連結連接指示詞，**來源角色指示詞**] 索引標籤定義從項目類型與您可以拖曳。 同樣地，**目標角色指示詞** 索引標籤來定義項目類型與您可以拖曳。 針對每個類型，您可以進一步指定是否要允許藉由設定連線 （適用於該連結連線指示詞）**自訂接受**旗標，然後提供額外的程式碼。  
  
 您也可以自訂建立連接時所發生的狀況。 例如，您可以自訂拖曳出或拖曳至特定類別的單一案例，一個 Link Connect 指示詞管理的所有案例，或整個 FlowBuilder 連接產生器。 針對上述每個選項，您可以在適當層級設定自訂旗標。 當您轉換所有範本並嘗試建置方案時，會出現錯誤訊息，將您引導至所產生之程式碼中的註解。 這些註解指出您必須提供的程式碼。  
  
 在「元件圖表」範例中，會自訂「連接」網域關聯性的連接產生器，限制只能在通訊埠之間建立連接。 下圖顯示您只能建立 `OutPort` 項目到 `InPort` 項目的連接，不過您可以讓元件彼此巢狀其中。  
  
 **從巢狀元件進入 OutPort 的連線**  
  
 ![連接產生器](../modeling/media/connectionbuilder_3.png "ConnectionBuilder_3")  
  
 因此，您可能需要指定可從巢狀元件連接至 OutPort。 若要指定這類的連線，您將**使用自訂接受**上**InPort**與來源角色類型和**OutPort**與中的目標角色類型**DSL 詳細資料**視窗下圖中所示：  
  
 **連結連線的 DSL 總管 中的指示詞**  
  
 ![連接產生器影像](../modeling/media/connectionbuilder_4a.png "ConnectionBuilder_4a")  
  
 **連結連線 DSL 詳細資料視窗中的指示詞**  
  
 ![](../modeling/media/connectionbuilder_4b.png "ConnectionBuilder_4b")  
  
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
  
 如需使用程式碼以自訂模型的詳細資訊，請參閱[巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
 例如，您可以使用類似的程式碼，防止使用者建立具有父子連結的迴圈。 這些限制會被視為 「 硬性 」 條件約束，因為使用者不能違反其在任何時間。 您也可以建立使用者就可以略過暫時建立不正確的設定，他們無法儲存的 「 軟性 」 的驗證檢查。  
  
### <a name="good-practice-in-defining-connection-builders"></a>定義連接產生器的最佳做法  
 您應該只在不同類型的關聯性在概念上相關時，才定義一個連接產生器來建立不同類型的關聯性。 在工作流程範例中，您使用同一個產生器來建立工作與工作之間，以及工作與物件之間的流程。 不過，使用同一個產生器來建立註解與工作之間的關聯性，可能會造成混淆。  
  
 如果您要定義用於多種關聯性類型的連接產生器，請確保該產生器不會對應至同一組來源和目標物件中的多種類型； 否則可能會發生無法預期的結果。  
  
 您使用自訂程式碼來套用 「 硬性 」 條件約束，但您應該考慮使用者是否應該可以暫時將無效的連接。 如果應該，您可以修改條件約束，在使用者嘗試儲存變更之前都不會驗證連接。  
  
## <a name="see-also"></a>另請參閱  
 [自訂項目建立和移動](../modeling/customizing-element-creation-and-movement.md)   
 [自訂複本的行為](../modeling/customizing-copy-behavior.md)   
 [如何： 加入拖放的處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [DSL 的循環圖範例](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)