---
title: 更新圖案和接點來反映模型
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b4c0c88e9e096836e32ce427ff78cc94f5d1f72
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927085"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>更新圖形和接點來反映模型

在 Visual Studio 中的特定領域語言，就能夠反映基礎模型的狀態圖形的外觀。

本主題中的程式碼範例應新增至`.cs`檔案中您`Dsl`專案。 您需要在每個檔案中的這些陳述式：

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>設定圖形地圖屬性來控制的裝飾項目可見性

您可以控制裝飾項目可見的性，而不需要撰寫程式碼中，藉由設定 DSL 定義中的圖形與領域類別之間的對應。 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>將公開為屬性的色彩和樣式的圖形

在 DSL 定義中，以滑鼠右鍵按一下圖形類別，指向**加入已公開**，然後按一下其中一個項目這類**填滿色彩**。

圖形現在具有程式碼中，或以使用者身分，您可以設定的網域屬性。 例如，若要設定它的命令或規則的程式碼中，您可以撰寫：

`shape.FillColor = System.Drawing.Color.Red;`

如果您想要將屬性有更多的變數只在程式控制下，而不是由使用者，選取新的網域屬性這類**填滿色彩**DSL 定義圖表中。 然後，在 [屬性] 視窗中，將**Is Browsable**要`false`或設定**是 UI Readonly**至`true`。

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>定義變更的規則，才能使色彩、 樣式或位置取決於模型項目屬性
 您可以定義規則，以更新的外觀取決於模型的其他部分的圖形。 例如，您可以定義變更規則上模型項目，以更新相依於模型項目的屬性及其圖案的色彩。 如需變更規則的詳細資訊，請參閱[規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

 您應該使用規則來更新屬性，在存放區 內進行維護，因為規則不會叫用執行 復原 命令時。 這不包括一些圖形化的功能，例如大小和形狀的可見性。 若要更新圖形的這些功能，請參閱[圖形化更新非存放區功能](#OnAssociatedProperty)。

 下列範例假設您有公開`FillColor`做為網域屬性，如上一節所述。

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>使用 OnChildConfigured 初始化圖形的屬性

若要設定圖案的屬性，第一次時，建立覆寫`OnChildConfigured()`圖表類別的部分定義中。 在 DSL 定義中，指定圖表類別與產生的程式碼位於**Dsl\Generated Code\Diagram.cs**。 例如: 

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

針對網域屬性和非存放區功能，例如圖形的大小，可以使用這個方法。

## <a name="OnAssociatedProperty"></a> 若要更新圖形的其他功能使用 Associatevaluewith

圖形，例如是否有陰影或連接器的箭頭樣式的某些功能沒有任何內建的方法，公開為網域屬性的功能。  這類功能的變更不在交易系統的控制之下。 因此，不適當更新這些使用規則，因為規則不會叫用使用者執行 [復原] 命令時。

相反地，您可以更新這類功能，使用<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>。 在下列範例中，連接器的箭頭樣式會受到網域屬性的連接器顯示在關係性中的值：

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` 應該呼叫一次，針對每個您想要註冊的網域屬性。 已呼叫之後，會呼叫指定之屬性的任何變更`OnAssociatedPropertyChanged()`中呈現該屬性的模型項目中的任何圖形。

您不需要呼叫`AssociateValueWith()`每個執行個體。 雖然 InitializeResources 是執行個體方法，它會叫用一次，針對每個圖形類別。
