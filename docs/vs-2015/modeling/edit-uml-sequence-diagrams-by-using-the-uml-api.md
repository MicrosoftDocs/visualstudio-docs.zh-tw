---
title: 使用 UML API 編輯 UML 循序圖 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c619ae6efd1de48319bf9c0398ee8ab4e3cd57ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442964"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>使用 UML API 編輯 UML 循序圖
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

互動是一組的生命線之間的訊息序列。 互動會顯示在 UML 循序圖上。  
  
 如需應用程式開發介面的完整詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>。  
  
 撰寫命令和軌跡處理常式的 UML 圖表的一般簡介，請參閱[在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
## <a name="basic-code"></a>基本程式碼  
  
### <a name="namespace-imports"></a>命名空間匯入  
 必須包含下列 `using` 陳述式：  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 如果您正在建立功能表命令和軌跡處理常式，您也會需要：  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 如需詳細資訊，請參閱 <<c0> [ 在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
### <a name="getting-the-context"></a>正在取得內容  
 如果您正在於循序圖中將互動編輯為命令或軌跡處理常式的一部分，您可以取得內容的參考。 例如：  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>已產生的和 UML 循序圖  
 有兩種類型的循序圖：一種在 UML 模型專案中手動建立，一種從程式碼產生。 使用 `UmlMode` 屬性探索您擁有的循序圖。  
  
> [!NOTE]
> 這個屬性只會在產生自使用 Visual Studio 2013 及更早版本之程式碼的循序圖傳回 false。 這包括移轉自 2013 及更早版本之程式碼所產生的循序圖。 此版本的 Visual Studio 不支援產生新的循序圖。  
  
 例如，如果您想創造僅在 UML 循序圖上可見的功能表命令，則 `QueryStatus()` 方法可能包括下列陳述式：  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 在所產生的循序圖上，生命線、訊息和其他項目大部分與 UML 循序圖上的相同。 在 UML 模型中，模型存放區會具有根，也就是擁有所有其他項目的模型。 但是，產生的互動存在於自己的模型存放區，其中具有 Null 根：  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>建立與顯示互動  
 建立作為套件或模型子系的互動。  
  
 例如，如果您正在開發可能執行在空白循序圖上的命令，應該一律先檢查互動是否存在。  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>正在更新互動及其配置  
 當您更新互動時，請一律使用下列方法之一來更新此配置，以結束您的作業：  
  
- `ISequenceDiagram.UpdateShapePositions()` 調整最近已插入或移動的圖形和其相鄰圖形的位置。  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` 會重新繪製整個圖表。 您可以使用參數來指定生命線、訊息或兩者的重新調整位置。  
  
  當您插入新項目或移動現有項目時，這一點格位重要。 必須在您執行其中一項作業之後，這些項目才會出現在圖表的正確位置上。 您只需要在完成一連串變更時，呼叫一次其中一項作業。  
  
  若要避免讓在您命令之後執行復原的使用者困惑，請使用 `ILinkedUndoTransaction` 括住您的變更和最終 `Layout()` 或 `UpdateShapePositions()` 作業。 例如:   
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 若要使用 `ILinkedUndoTransaction`，必須在您的類別中進行這個宣告：  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 如需詳細資訊，請參閱 <<c0> [ 藉由使用異動連結 UML 模型更新](../modeling/link-uml-model-updates-by-using-transactions.md)。  
  
## <a name="building-an-interaction"></a>建置互動  
  
### <a name="to-create-lifelines"></a>建立生命線  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 生命線代表可連接的項目，也就是類型的執行個體。 例如，如果互動用來顯示元件如何委派傳入訊息至其內部組件，則生命線可以表示元件的連接埠和組件：  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 或者，如果互動顯示任意一組物件，您可以在互動本身建立屬性或其他 `IConnectableElement`：  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 做為進一步的替代方案，您可以設定生命線的名稱和類型，而不將它連結至可連接的項目：  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>建立訊息  
 若要建立訊息，您必須識別來源和目標生命線上的插入點。 例如：  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 若要建立具有未定義來源或未定義目標的訊息：  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 有數則您可以用來識別生命線上所有關鍵點之插入點的訊息：  
  
|ILifeline 的方法|使用它在這個點插入|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|生命線頂端。|  
|`FindInsertionPointAtBottom()`|生命線底端。|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|緊跟在指定訊息後的點。|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|這個點可以在生命線上，或在父執行規格區塊上。|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|跟隨在互動使用後的點。|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|跟隨在合併片段後的點。|  
|`FindInsertionPoint(IExecutionSpecification block)`|執行區塊頂部。|  
|`FindInsertionPoint(IInteractionOperand fragment)`|合併片段的運算元頂部。|  
  
 當您建立訊息時，請小心避免定義會跨過另一則訊息的訊息。  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>建立合併片段和互動使用  
 您可以藉由在每條生命線上指定插入點，來建立合併片段和互動使用，其中生命線必須涵蓋在項目中。 請小心避免指定會跨過現有訊息或片段的一組點。  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 您也可以建立涵蓋一組現有訊息的合併片段。 所有訊息必須來自相同的生命線或執行區塊。  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 合併片段一律以單一運算元建立。 若要建立新的運算元，您必須指定想在之前或之後插入的現有運算元，以及您是否要在其之前或之後插入：  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>疑難排解  
 如果變更不是以 `UpdateShapePositions()` 或 `Layout()` 作業完成，圖形會出現在不正確的位置。  
  
 大部分其他問題的成因是插入點配置不當，使得新的訊息或片段必須跨過其他訊息或片段。 徵兆可能是沒有執行任何變更，或擲回例外狀況。 如果沒有執行 `UpdateShapePositions()` 或 `Layout()` 作業，可能不會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)   
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [定義自訂模型工具箱項目](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)   
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)
