---
title: 在模型圖表上定義軌跡處理常式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fbf111dbf8297994994f10b9b867e03321268679
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654876"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>在模型圖表上定義軌跡處理常式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，您可以定義當使用者按兩下，或將項目拖曳至 UML 圖表時會執行的命令。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780))，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。

 如果您要拖曳的圖表類型及項目類型已有內建行為，您可能無法加入或覆寫這個行為。

## <a name="requirements"></a>需求
 請參閱 [需求](../modeling/extend-uml-models-and-diagrams.md#Requirements)。

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="creating-a-gesture-handler"></a>建立軌跡處理常式
 若要定義 UML 設計工具的軌跡處理常式，您必須建立一個類別來定義軌跡處理常式的行為，並將該類別內嵌在 Visual Studio 整合擴充功能 (VSIX)。 VSIX 會做為容器，可安裝該處理常式。 定義軌跡處理程式有兩個替代方法：

- **使用專案範本在自己的 VSIX 中建立軌跡處理常式。** 這是較快速的方法。 它適用於您不想結合您的處理常式與其他類型的擴充功能時，例如驗證擴充功能、自訂工具箱項目或功能表命令。

- **建立個別的手勢處理常式和 VSIX 專案。** 如果您想要將數種類型的擴充功能結合成相同的 VSIX，則請使用這個方法。 比方說，如果軌跡處理常式預期模型要觀察特定的條件約束，您可以將它內嵌至與驗證方法相同的 VSIX。

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>在自己的 VSIX 中建立軌跡處理常式

1. 在 [新增專案] 對話方塊中，於 [模型專案]之下，選取 [軌跡擴充功能]。

2. 在新的專案開啟 **.cs** 檔案，並修改 `GestureExtension` 類別來實作軌跡處理常式。

    如需詳細資訊，請參閱 [實作軌跡處理常式](#Implementing)。

3. 按 F5 測試軌跡處理常式。 如需詳細資訊，請參閱 [執行軌跡處理常式](#Executing)。

4. 將軌跡處理常式安裝在另一部電腦上，方法是複製專案所建立的**bin \\ \* \\ \* .vsix**檔案。 如需詳細資訊，請參閱 [安裝和解除安裝擴充功能](#Installing)。

   以下是替代程序：

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>為軌跡處理常式建立不同的類別庫 (DLL) 專案

1. 在新的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案或現有的方案中，建立類別庫專案。

   1. 在 [檔案] 功能表上，依序選擇 [新增]和 [專案]。

   2. 在 [已安裝的範本]下，依序展開 [Visual C#] 或 [Visual Basic]，然後在中間的資料行中選擇 [類別庫]。

2. 將下列參考加入您的專案。

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` – 您只有在要擴充圖層圖表時才需要此項。 如需詳細資訊，請參閱[擴充分層圖](../modeling/extend-layer-diagrams.md)。

3. 將類別檔案加入專案，並將其內容設定為下列程式碼。

   > [!NOTE]
   > 根據您的偏好設定變更命名空間和類別名稱。

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

       /// <summary>
       /// Retrieves UML IElements from drag arguments.
       /// Works for drags from UML diagrams.
       /// </summary>
       private IEnumerable<IElement> GetModelElementsFromDragEvent
               (DiagramDragEventArgs dragEvent)
       {
         //ElementGroupPrototype is the container for
         //dragged and copied elements and toolbox items.
         ElementGroupPrototype prototype =
            dragEvent.Data.
            GetData(typeof(ElementGroupPrototype))
                 as ElementGroupPrototype;
         // Locate the originals in the implementation store.
         IElementDirectory implementationDirectory =
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

         return prototype.ProtoElements.Select(
           prototypeElement =>
           {
             ModelElement element = implementationDirectory
               .FindElement(prototypeElement.ElementId);
             ShapeElement shapeElement = element as ShapeElement;
             if (shapeElement != null)
             {
               // Dragged from a diagram.
               return shapeElement.ModelElement as IElement;
             }
             else
             {
               // Dragged from UML Model Explorer.
               return element as IElement;
             }
           });
       }

     }
   }

   ```

    如需要在方法中放入什麼的詳細資訊，請參閱 [實作軌跡處理常式](#Implementing)。

   您必須將功能表命令加入 VSIX 專案，期將會做為安裝命令的容器。 如果您想要，可以在相同的 VSIX 中包含其他元件。

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>將個別的軌跡處理常式加入 VSIX 專案

1. 如果您已經建立具有自己的 VSIX 的軌跡處理常式，便不需要此程序。

2. 除非您的方案已經包含 VSIX 專案，否則請建立一個。

    1. 在 [方案總管]中，在方案的捷徑功能表上，選擇 [新增]和 [新增專案]。

    2. 在 [已安裝的範本]下，依序展開 [Visual C#] 或 [Visual Basic]，然後選取 [擴充性]。 在中間的資料行中，選擇 [VSIX 專案]。

3. 將 VSIX 專案設定為方案的啟始專案。

    - 在 [方案總管] 中，在 VSIX 專案的捷徑功能表上，選擇 [設定為啟始專案]。

4. 在 **source.extension.vsixmanifest**中，將軌跡處理常式類別庫專案加入做為 MEF 元件：

    1. 在 [中繼資料] 索引標籤上，設定 VSIX 的名稱。

    2. 在 [安裝目標] 索引標籤上，設定 Visual Studio 版本做為目標。

    3. 在 [資產] 索引標籤上，選擇 [新增]，然後在對話方塊中設定：

          = 

          = 

          = 

## <a name="Executing"></a>執行手勢處理常式
 基於測試目的，請在偵錯模式中執行軌跡處理常式。

#### <a name="to-test-the-gesture-handler"></a>測試軌跡處理常式

1. 按 **F5**，或在 [偵錯] 功能表上，按一下 [開始偵錯]。

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體隨即啟動。

    **疑難排解**：如果新的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 未啟動：

   - 如果您有多個專案，請確定 VSIX 專案已設定為方案的啟始專案。

   - 在 [方案總管] 中，在啟始專案或唯一專案的捷徑功能表上，選擇 [屬性]。 在 [專案屬性編輯器] 中，選擇 [**調試**程式] 索引標籤。請確定 [**啟動外部程式**] 欄位中的字串是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的完整路徑名稱，通常是：

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. 在實驗性 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中，開啟或建立模型專案，並開啟或建立模型圖表。 使用屬於軌跡處理常式類別的屬性中所列類型之一的圖表。

3. 按兩下圖表上的任何地方。 應該會呼叫您的按兩下處理常式。

4. 將項目從 UML 總管拖曳至圖表。 應該會呼叫您的拖曳處理常式。

   **疑難排解**：如果軌跡處理常式無法運作，請確定：

- 軌跡處理常式專案在 VSIX 專案 **source.extensions.manifest** 的 [資產] 索引標籤中列為 MEF 元件。

- 所有 `Import` 和 `Export` 屬性的參數都有效。

- `CanDragDrop` 方法不會傳回 `false`

- 您正在使用的模型圖表類型 (UML 類別、序列等等) 已列為其中一個軌跡處理常式類別屬性 [ClassDesignerExtension]、[SequenceDesignerExtension] 等等。

- 沒有任何已為此類型的目標和卸除項目定義的內建功能。

## <a name="Implementing"></a>執行手勢處理常式

### <a name="the-gesture-handler-methods"></a>軌跡處理常式方法
 軌跡處理常式類別會實作及匯出 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>。 您需要定義的方法如下所示：

|||
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|傳回 `true` 以允許 `dragEvent` 中參考的來源項目在此目標上卸除。<br /><br /> 這個方法不應該對模型進行變更。 它應該會運作很快，因為它用來判斷使用者移動滑鼠時的箭號狀態。|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|根據 `dragEvent`中所參考來源物件更新模型以及目標。<br /><br /> 當使用者拖曳之後釋放滑鼠按鈕時呼叫。|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` 是使用者按兩下的圖形。|

 您可以撰寫處理常式，不僅接受 UML，也接受各式各樣的其他項目，例如檔案、.NET 類別檢視中的節點等等。 使用者可以將這些項目拖曳至 UML 圖表中，假設您撰寫 `OnDragDrop` 方法，可以將序列化形式的項目解碼的話。 解碼方法會因項目類型而異。

 這些方法的參數如下：

- `ShapeElement target` 使用者已將項目拖曳至其上的圖形或圖表。

    `ShapeElement` 是實作中的一個類別，此實作是 UML 類別模型化工具的基礎。 若要降低使 UML 模型和圖表處於不一致狀態的風險，我們建議不要直接使用這個類別的方法。 相反地，將元素包裝在 `IShape` 中，然後使用在[圖表上顯示 UML 模型](../modeling/display-a-uml-model-on-diagrams.md)中所述的方法。

  - 取得 `IShape`：

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - 若要取得拖曳或按兩下作業的目標模型項目：

      ```
      IElement target = targetIShape.Element;
      ```

      您可以將此轉型為更特定類型的項目。

  - 若要取得包含 UML 模型的 UML 模型存放區：

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - 若要取得主機和服務提供者的存取權：

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs` 此參數會攜帶拖曳作業的序列化形式來源物件：

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     您可以將許多不同類型的項目拖曳到圖表中 - 從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的不同部分，或是從 Windows 桌面。 不同類型的項目在 `IDataObject`中會以不同方式編碼。 若要從其中擷取項目，請參閱適當物件類型的文件。

     如果您的來源物件是從 [UML 模型瀏覽器] 或另一個 UML 圖表拖曳的 UML 元素，請參閱[從 IDataObject 取得 uml 模型](../modeling/get-uml-model-elements-from-idataobject.md)專案。

### <a name="writing-the-code-of-the-methods"></a>撰寫方法的程式碼
 如需有關如何撰寫程式碼來讀取和更新模型的詳細資訊，請參閱 [Programming with the UML API](../modeling/programming-with-the-uml-api.md)。

 如需在拖曳作業中存取模型資訊的詳細資訊，請參閱[從 IDataObject 取得 UML 模型元素](../modeling/get-uml-model-elements-from-idataobject.md)。

 如果您正在處理順序圖表，另請參閱[使用 UML API 編輯 UML 順序圖表](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)。

 除了方法的參數，您也可以在您的類別中宣告匯入的屬性，提供目前圖表和模型的存取權。

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 宣告 `IDiagramContext` 可讓您在方法中撰寫程式碼，存取圖表、目前的選取範圍，以及模型：

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 如需詳細資訊，請參閱[導覽 UML 模型](../modeling/navigate-the-uml-model.md)。

## <a name="Installing"></a>安裝和卸載擴充功能
 您可以同時在自己的電腦和其他電腦上安裝 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充功能。

#### <a name="to-install-an-extension"></a>安裝擴充功能

1. 在您的電腦中，尋找 VSIX 專案所建置的 **.vsix** 檔案。

    1. 在方案總管中，於 VSIX 專案的捷徑功能表上，選擇 [在 Windows 檔案總管中開啟資料夾]。

    2. 找出 **\* \\** _yourproject。_ 的 bin \\

2. 將 **.vsix** 檔案複製到要安裝擴充功能的目標電腦。 這可以是您自己的電腦或另一部電腦。

     目的電腦必須有您在**extension.vsixmanifest**中指定的其中一種 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 版本。

3. 在目標電腦上開啟 **.vsix** 檔案。

     [Visual Studio 擴充功能安裝程式] 會隨即開啟並安裝擴充功能。

4. 啟動或重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。

#### <a name="to-uninstall-an-extension"></a>解除安裝擴充功能

1. 在 [工具] 功能表中選擇 [擴充功能和更新]。

2. 展開 [已安裝的擴充功能]。

3. 選取擴充功能，然後選擇 [解除安裝]。

   在很少見的情況下，故障的擴充功能無法載入並且會在錯誤視窗中建立報告，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：

   *% LocalAppData%* **\Local\Microsoft\VisualStudio \\ [version] \Extensions**

## <a name="DragExample"></a> 範例
 下列範例示範如何根據從元件圖表拖曳之元件的組件和連接埠，在循序圖中建立生命線。

 若要加以測試，請按 F5。 Visual Studio 的實驗執行個體隨即開啟。 在本例中，開啟 UML 模型，並在元件圖上建立元件。 將某些介面和內部元件組件加入此元件。 選取介面和組件。 然後將介面和組件拖曳到循序圖。 （從 [元件] 圖表拖曳至順序圖表的索引標籤，然後向下拖曳至 [順序] 圖表）。每個介面和元件都會出現一個生命線。

 如需將互動系結至順序圖表的詳細資訊，請參閱[使用 UML API 編輯 UML 順序圖表](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)。

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
          (DiagramDragEventArgs dragEvent)
  {
    //ElementGroupPrototype is the container for
    //dragged and copied elements and toolbox items.
    ElementGroupPrototype prototype =
       dragEvent.Data.
       GetData(typeof(ElementGroupPrototype))
            as ElementGroupPrototype;
    // Locate the originals in the implementation store.
    IElementDirectory implementationDirectory =
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

    return prototype.ProtoElements.Select(
      prototypeElement =>
      {
        ModelElement element = implementationDirectory
          .FindElement(prototypeElement.ElementId);
        ShapeElement shapeElement = element as ShapeElement;
        if (shapeElement != null)
        {
          // Dragged from a diagram.
          return shapeElement.ModelElement as IElement;
        }
        else
        {
          // Dragged from UML Model Explorer.
          return element as IElement;
        }
      });
  }

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 [從 IDataObject 取得 UML 模型](../modeling/get-uml-model-elements-from-idataobject.md)專案中會說明 `GetModelElementsFromDragEvent()` 的程式碼。

## <a name="see-also"></a>請參閱
 [定義和安裝模型擴充功能](../modeling/define-and-install-a-modeling-extension.md)[擴充 uml 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)[在模型圖表上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)[定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)[使用 uml API](../modeling/programming-with-the-uml-api.md)進行程式設計
