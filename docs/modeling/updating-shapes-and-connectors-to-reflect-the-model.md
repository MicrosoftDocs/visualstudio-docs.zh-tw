---
title: 更新圖案和接點來反映模型
description: 瞭解 Visual Studio 中的特定領域語言，您可以讓圖形的外觀反映基礎模型的狀態。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 57f3785fe232b20123475bd85be2be7148e5b87e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924349"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>更新圖形和接點來反映模型

在 Visual Studio 的特定領域語言中，您可以讓圖形的外觀反映基礎模型的狀態。

本主題中的程式碼範例應該加入至 `.cs` 專案中的檔案 `Dsl` 。 您在每個檔案中都需要下列指示詞：

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>設定圖形地圖屬性以控制裝飾專案的可見度

您可以在 DSL 定義中設定圖形與網域類別之間的對應，而不需撰寫程式碼，即可控制裝飾專案的可見度。 如需詳細資訊，請參閱 [如何定義 Domain-Specific 語言](../modeling/how-to-define-a-domain-specific-language.md)。

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>將圖形的色彩和樣式公開為屬性

在 DSL 定義中，以滑鼠右鍵按一下圖形類別，指向 [ **加入公開**]，然後按一下其中一個專案，例如 [ **填滿色彩**]。

圖形現在具有可在程式碼或使用者中設定的網域屬性。 例如，若要在命令或規則的程式碼中設定它，您可以撰寫：

`shape.FillColor = System.Drawing.Color.Red;`

如果您只想要在 [程式控制] （而不是由使用者）下建立屬性變數，請在 [DSL 定義] 圖表中選取新的網域屬性，例如 **填滿色彩** 。 然後，在屬性視窗中，set 可 **流覽** 至， `false` 或設定 **為的 UI Readonly** `true` 。

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>定義變更規則以使色彩、樣式或位置相依于模型元素屬性
 您可以定義規則，以根據模型的其他部分來更新圖形的外觀。 例如，您可以在模型專案上定義變更規則，以根據模型專案的屬性來更新其圖形的色彩。 如需變更規則的詳細資訊，請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

 您應該只使用規則來更新存放區內維護的屬性，因為執行 Undo 命令時不會叫用規則。 這不包含某些圖形功能，例如圖形的大小和可見度。 若要更新圖形的這些功能，請參閱 [更新非存放區圖形化功能](#OnAssociatedProperty)。

 下列範例假設您已公開 `FillColor` 為網域屬性，如上一節所述。

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

若要在第一次建立圖形時設定其屬性，請 `OnChildConfigured()` 在圖表類別的部分定義中覆寫。 圖類別是在您的 DSL 定義中指定，而產生的程式碼則是在 **Dsl\Generated Code\Diagram.cs** 中。 例如：

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

這個方法可以用於定義域屬性和非存放區功能，例如圖形的大小。

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> 使用 AssociateValueWith ( # A1 來更新圖形的其他功能

針對圖形的某些功能（例如它是否有陰影或接點的箭號樣式），沒有任何內建方法可將功能公開為網域屬性。  這類功能的變更不在交易系統的控制之下。 因此，使用規則來更新它們並不適合，因為當使用者執行復原命令時，不會叫用規則。

相反地，您可以使用來更新這類功能 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> 。 在下列範例中，連接器的箭號樣式是由連接器顯示的關聯性中的網域屬性值所控制：

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

`AssociateValueWith()` 應針對您想要註冊的每個網域屬性呼叫一次。 在呼叫之後，對指定屬性所做的任何變更，都會 `OnAssociatedPropertyChanged()` 在呈現屬性模型專案的任何圖形中呼叫。

不需要為 `AssociateValueWith()` 每個實例呼叫。 雖然 InitializeResources 是實例方法，但每個圖形類別只會叫用一次。
