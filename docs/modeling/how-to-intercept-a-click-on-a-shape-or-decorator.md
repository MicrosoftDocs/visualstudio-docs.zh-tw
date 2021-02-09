---
title: 如何：攔截圖案或 Decorator 上的點選
description: 瞭解如何攔截圖形或圖示裝飾專案的點擊，以及如何攔截點擊、按兩下、拖曳和其他筆勢。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2697e3d17e289297bcad57155c1c9ea6f1880acc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922709"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>如何：攔截圖案或 Decorator 上的點選
下列程式示範如何攔截圖形或圖示裝飾專案的點擊。 您可以攔截點擊、按兩下、拖曳和其他手勢，然後讓元素回應。

## <a name="to-intercept-clicks-on-shapes"></a>若要攔截圖形上的按一下
 在 Dsl 專案中，在與產生的程式碼檔案不同的程式碼檔案中，撰寫 shape 類別的部分類別定義。 覆寫 `OnDoubleClick()` 或其中一個名稱開頭為的其他方法 `On...` 。 例如：

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
> `e.Handled` `true` 除非您想要將事件傳遞至包含的圖形或圖表，否則請將設定為。

## <a name="to-intercept-clicks-on-decorators"></a>若要攔截裝飾專案的按一下
 影像裝飾專案會在具有 OnDoubleClick 方法的 ImageField 類別實例上執行。 如果您撰寫 ImageField 子類別，就可以攔截點擊。 這些欄位會在 InitializeShapeFields 方法中設定。 因此，您必須變更該方法來具現化子類別，而不是一般 ImageField。 InitializeShapeFields 方法位於圖形類別的產生程式碼中。 您可以覆寫 shape 類別， `Generates Double Derived` 如下列程式所述設定其屬性。

 雖然 InitializeShapeFields 是實例方法，但每個類別只會呼叫一次。 因此，每個類別中的每個欄位都只會有一個 ClickableImageField 實例，但圖表中的每個圖形都不會有一個實例。 當使用者按兩下實例時，您必須識別已遇到的實例，如範例中的程式碼所示。

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>若要攔截按一下圖示裝飾專案

1. 開啟或建立 DSL 解決方案。

2. 選擇或建立具有圖示裝飾專案的圖形，並將其對應至網域類別。

3. 在與資料夾中檔案不同的程式碼檔案中 `GeneratedCode` ，建立 ImageField 的新子類別：

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

     如果您不想要將事件傳遞至包含的圖形，則應該將 [已處理] 設定為 [true]。

4. 藉由新增下列部分類別定義，覆寫您圖形類別中的 InitializeShapeFields 方法。

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

1. 建置並執行解決方案。

2. 按兩下圖形實例上的圖示。 應該會出現您的測試訊息。

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>攔截 CompartmentShape 清單的點擊和拖曳
 下列範例可讓使用者藉由拖曳來重新排序區間圖形中的專案。 若要執行此程式碼：

1. 使用 **類別圖表** 方案範本建立新的 DSL 解決方案。

    您也可以使用自己的解決方案，其中包含區間圖形。 這段程式碼假設圖形所代表的模型專案和區間清單專案中表示的元素之間有內嵌關聯性。

2. 設定 [產生區間] 圖形的 [ **產生雙重衍生** ] 屬性。

3. 將此程式碼新增至 **Dsl** 專案中的檔案。

4. 調整此程式碼中的網域類別和圖形名稱，以符合您自己的 DSL。

   總而言之，程式碼的運作方式如下。 在此範例中， `ClassShape` 是區間圖形的名稱。

- 建立時，會將一組滑鼠事件處理常式附加至每個區間實例。

- 此 `ClassShape.MouseDown` 事件會儲存目前的專案。

- 當滑鼠移出目前的專案時，就會建立 MouseAction 的實例，這會設定游標並捕捉滑鼠，直到釋放它為止。

     為了避免干擾其他滑鼠動作，例如選取專案的文字，在滑鼠離開原始專案之前，不會建立 MouseAction。

     建立 MouseAction 的替代方法就是接聽 MouseUp。 不過，如果使用者在將滑鼠拖曳至區間以外的地方放開滑鼠，這項作業就無法正常運作。 MouseAction 可以執行適當的動作，不論是在哪裡放開滑鼠。

- 當您放開滑鼠時，MouseAction 會重新排列模型專案之間的連結順序。

- 角色順序的變更會引發更新顯示的規則。 此行為已定義，不需要其他程式碼。

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
