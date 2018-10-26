---
title: 如何：攔截圖案或 Decorator 上的點選
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0a8af35d9edbb28c6b357149586fe7015858f4f0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876525"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>如何：攔截圖案或 Decorator 上的點選
下列程序示範如何攔截圖案或 decorator 上的圖示。 您可以攔截按一下、 按兩下、 拖曳，及其他筆勢，並讓回應項目。

## <a name="to-intercept-clicks-on-shapes"></a>若要攔截在圖形上的點選
 在 Dsl 專案中產生的程式碼檔案中，從不同的程式碼檔案寫入 shape 類別的部分類別定義。 覆寫`OnDoubleClick()`或其中一個名稱開頭的方法`On...`。 例如: 

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
>  設定`e.Handled`至`true`，除非您想要傳遞至包含的圖形或圖表的事件。

## <a name="to-intercept-clicks-on-decorators"></a>若要攔截的裝飾項目上按下
 OnDoubleClick 方法的 ImageField 類別的執行個體上執行映像的裝飾項目。 您可以攔截按下滑鼠，如果您要撰寫 ImageField 子類別。 欄位為 InitializeShapeFields 方法中。 因此，您必須變更您的子類別，而不是一般 ImageField 具現化該方法。 InitializeShapeFields 方法是在產生的程式碼的圖形類別。 如果您設定，您可以覆寫 shape 類別其`Generates Double Derived`屬性，如下列程序中所述。

 雖然 InitializeShapeFields 是執行個體方法，它會呼叫一次只能針對每個類別。 因此，只有一個執行個體 ClickableImageField 存在每個類別，而不在圖表中的每個圖形的一個執行個體中每個欄位。 當使用者按兩下執行個體時，您必須識別哪一個執行個體已叫用，如範例中的程式碼所示。

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>若要攔截上的圖示裝飾項目

1.  開啟或建立的 DSL 方案。

2.  選擇或建立圖案具有圖示裝飾項目，並將它對應至網域類別。

3.  在程式碼檔案中的檔案不同`GeneratedCode`資料夾中，建立新的子類別的 ImageField:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     您應該設定為 true，如果您不想要傳遞給包含的圖形事件的處理。

4.  加入下列的部分類別定義來覆寫在圖形 classs InitializeShapeFields 方法。

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1.  建置並執行方案。

2.  按兩下圖形的執行個體上的圖示。 測試訊息應該會出現。

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>攔截按一下和拖曳 CompartmentShape list
 下列範例可讓使用者藉由拖曳它們重新排序區間圖形中的項目。 若要執行此程式碼：

1. 使用建立新的 DSL 方案**類別圖表**解決方案範本。

    您也可以使用您自己的方案中，含有區間圖形。 此程式碼會假設是圖形時，所代表的模型項目，以及表示區間清單項目中的元素之間內嵌關聯性。

2. 設定**產生雙衍生**區間圖形的屬性。

3. 在檔案中加入下列程式碼**Dsl**專案。

4. 調整以符合您自己的 DSL 的這段程式碼中的網域類別和圖形名稱。

   總而言之，程式碼的運作方式，如下所示。 在此範例中，`ClassShape`區間圖形的名稱。

-   一組的滑鼠事件處理常式會附加至每個區間的執行個體建立時。

-   `ClassShape.MouseDown`事件會儲存目前的項目。

-   當滑鼠移出目前的項目，建立 MouseAction 的執行個體，其設定資料指標，並擷取滑鼠，直到釋放它為止。

     若要避免干擾其他的滑鼠動作，例如選取文字的項目，直到滑鼠離開原始項目，才會建立 MouseAction。

     建立 MouseAction 的替代方式是只接聽 MouseUp。 不過，這會無法正常運作如果使用者放開滑鼠之後將它拖曳區間之外。 MouseAction 就能夠執行適當的動作，不論其中放開滑鼠。

-   當已釋放滑鼠時，MouseAction.MouseUp 重新排列模型項目之間連結的順序。

-   角色順序的變更就會引發更新顯示的規則。 已經定義此行為，並不需要任何額外的程式碼。

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
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
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
  /// click somewhere else in the source shape.
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
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
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

- [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
- [Decorator 的屬性](../modeling/properties-of-decorators.md)