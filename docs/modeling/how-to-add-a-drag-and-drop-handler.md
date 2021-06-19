---
title: 如何：加入拖放處理常式
description: 瞭解如何將拖放事件的處理常式加入至您的 DSL，讓使用者可以從其他圖表將專案拖曳到圖表上。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79b58ee6ebd4db3ee9727bf59b260f281ba00275
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390407"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>如何：加入拖放處理常式

您可以將拖放事件的處理常式加入至您的 DSL，讓使用者可以從其他圖表或 Visual Studio 的其他部分，將專案拖曳到您的圖表上。 您也可以加入按兩下等事件的處理常式。 拖放和按兩下處理常式稱為軌跡 *處理* 程式。

本主題討論源自其他圖表的拖放軌跡。 若為單一圖表內的移動和複製事件，請考慮改為定義 `ElementOperations` 的子類別。 如需詳細資訊，請參閱 [自訂複製行為](../modeling/customizing-copy-behavior.md)。 您也可以自訂 DSL 定義。

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>覆寫 ShapeElement 方法來定義軌跡處理常式

`OnDragDrop`可以覆寫、、 `OnDoubleClick` `OnDragOver` 和其他方法。

將新的程式碼檔案加入至您的 DSL 專案。 對於軌跡處理常式，您通常至少必須有下列指示詞 `using` ：

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

在新檔案中，針對應該回應拖曳作業的圖形或圖表類別定義部分類別。 覆寫下列方法：

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>-當滑鼠指標在拖曳作業期間進入圖形時，會呼叫這個方法。 您的方法應該會檢查使用者拖曳的項目，並設定 Effect 屬性，指出使用者是否可將項目放在此圖形上。 Effect 屬性決定游標移至此圖形上的外觀，並決定當使用者放開滑鼠按鈕時，是否呼叫 `OnDragDrop()`。

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> -當滑鼠指標停留在這個圖形或圖表上時，如果使用者放開滑鼠按鍵，就會呼叫這個方法（如果 `OnDragOver(DiagramDragEventArgs e)` 先前設定 `e.Effect` 為以外的值） `None` 。

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> -當使用者按兩下圖形或圖表時，會呼叫這個方法。

     如需詳細資訊，請參閱 [如何：攔截圖形或裝飾專案的點擊](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)。

定義 `IsAcceptableDropItem(e)` 以決定是否可接受拖曳的項目，並定義 ProcessDragDropItem(e) 以在放置項目時更新模型。 這些方法必須先從事件引數擷取項目。 如需如何進行這項操作的詳細資訊，請參閱 [如何取得拖曳專案的參考](#to-send-an-object-from-a-source-dsl)。

## <a name="define-gesture-handlers-by-using-mef"></a>使用 MEF 來定義軌跡處理常式

如果您想讓協力廠商的開發人員能夠自行定義要加入至您的 DSL 的處理常式，請使用這個方法。 使用者可以在安裝您的 DSL 之後，選擇安裝協力廠商擴充功能。

MEF (Managed Extensibility Framework) 可讓您定義使用最小組態安裝的元件。 如需詳細資訊，請參閱 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。

### <a name="to-define-a-mef-gesture-handler"></a>定義 MEF 軌跡處理常式

1. 新增至您的 **dsl** 和 **DslPackage** 專案：[使用 MEF 擴充您的 Dsl](../modeling/extend-your-dsl-by-using-mef.md)中所述的 **MefExtension** 檔案。

2. 您現在可以將軌跡處理常式定義為 MEF 元件：

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     您可以建立多個軌跡處理常式元件，例如當您有不同類型的拖曳物件時。

3. 加入目標圖形、連接線或圖表類別的部分類別定義，並定義 `IsAcceptableDropItem()` 和 `ProcessDragDropItem()` 方法。 這些方法一開始必須先從事件引數擷取拖曳的項目。 如需詳細資訊，請參閱 [如何取得拖曳專案的參考](#to-send-an-object-from-a-source-dsl)。

## <a name="how-to-decode-the-dragged-item"></a>如何解碼拖曳的項目

您可以從任何視窗或從桌面拖曳項目，也可以從 DSL 拖曳項目。

當使用者將項目拖曳到您的圖表上，或從圖表的某個部分拖曳到另一個部分時，`DiagramDragEventArgs` 中會提供拖曳項目的相關資訊。 由於拖曳作業可能在畫面上的任何物件上啟動，因此提供的資料可以是任何一種格式。 您的程式碼必須辨識這些格式，並且能夠處理這些格式。

若要探索拖曳來源資訊的可用格式，請在偵錯模式中執行程式碼，並在 `OnDragOver()` 或 `CanDragDrop()` 的進入點設定中斷點。 檢查 `DiagramDragEventArgs` 參數的值。 這項資訊提供下列兩種格式：

- <xref:System.Windows.Forms.IDataObject>  `Data` -此屬性會攜帶來源物件的序列化版本，通常是以一種以上的格式來執行。 其最有用的函式包括：

  - diagramEventArgs. GetDataFormats () -列出您可以用來解碼拖曳物件的格式。 例如，如果使用者從桌面拖曳檔案，可用的格式包括檔案名稱 ("`FileNameW`")。

  - `diagramEventArgs.Data.GetData(format)` -以指定的格式解碼拖曳的物件。 將物件轉換成適當的類型。 例如：

    `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

    您也可以從使用您的自訂格式的來源傳輸模型匯流排參考等物件。 如需詳細資訊，請參閱 [如何在拖放中傳送模型匯流排參考](#to-send-an-object-from-a-source-dsl)。

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>`Prototype`-如果您想要讓使用者從 DSL 或 UML 模型拖曳專案，請使用此屬性。 項目群組原型包含一個或多個物件、連結及其屬性值。 這個屬性也可用於貼上作業及加入工具箱中的項目時。 在原型中，物件及其類型會由 GUID 識別。 例如，下列程式碼允許使用者從 UML 圖表或 [UML 模型總管] 拖曳類別項目：

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     若要接受 UML 圖形，請依實驗判斷 UML 圖形類別的 Guid。 請記住，任一圖表上通常有多種項目類型。 另請記住，從 DSL 或 UML 圖表拖曳的物件是圖形，而不是模型項目。

`DiagramDragEventArgs` 也具有指出目前滑鼠指標位置的屬性，以及使用者是否按下 CTRL、ALT 或 SHIFT 鍵。

## <a name="how-to-get-the-original-of-a-dragged-element"></a>如何取得原始的拖曳項目

如果拖曳的項目是 DSL 項目，您可以開啟來源模型並存取此項目。

事件引數的 `Data` 和 `Prototype` 屬性只包含拖曳圖形的參考。 通常，如果您要在衍生自原型的目標 DSL 中以特定方式建立物件，您需要取得原始拖曳項目的存取權，例如讀取檔案內容，或巡覽至圖形所表示的模型項目。 您可以使用 Visual Studio 模型匯流排來協助達成此目標。

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>為模型匯流排準備 DSL 專案

Visual Studio 模型匯流排，使來源 DSL 可供存取：

1. 在 [DSL 設計工具] 中，開啟來源 DSL 的 DSL 定義檔。 以滑鼠右鍵按一下設計介面，然後按一下 [ **啟用 Modelbus**]。 在對話方塊中，選擇其中一個或兩個選項。  按一下 [確定]  。 新專案 "ModelBus" 會隨即加入至 DSL 方案。

2. 按一下 [ **轉換所有範本** ]，然後重建方案。

### <a name="to-send-an-object-from-a-source-dsl"></a>從來源 DSL 傳送物件

1. 在您的 ElementOperations 子類別中，覆寫 `Copy()`，將模型匯流排參考 (MBR) 編碼成 IDataObject。 當使用者從來源圖表開始拖曳時，會呼叫這個方法。 接著在使用者放入目標圖表中時，IDataObject 中會提供編碼的 MBR。

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>從目標 DSL 或 UML 專案中的 DSL 接收模型匯流排參考

1. 在目標 DSL 專案中，將專案參考加入至：

    - 來源 DSL 專案。

    - 來源 ModelBus 專案。

2. 在軌跡處理常式的程式碼檔案中，加入下列命名空間參考：

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3. 下列範例說明如何取得來源模型項目的存取權：

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>接受源自 UML 模型的項目

- 下列程式碼範例接受從 UML 圖表放置的物件。

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>使用滑鼠動作：拖曳區間項目

您可以撰寫處理常式來攔截圖形欄位上的滑鼠動作。 下列範例可讓使用者使用滑鼠拖曳，來重新排序區間中的專案。

若要建立此範例，請使用 **類別圖表** 方案範本建立方案。 加入程式碼檔案並加入下列程式碼。 將命名空間調整成與您自己的程式碼相同的命名空間。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape. Yuk.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>另請參閱

- [自訂複製行為](../modeling/customizing-copy-behavior.md)
- [部署網域指定的語言方案](msi-and-vsix-deployment-of-a-dsl.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
