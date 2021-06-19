---
title: 自訂文字和影像欄位
description: 瞭解如何自訂文字和影像檔案。 此外，也請瞭解當您在圖形中定義文字裝飾專案時，它是以欄位表示。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52c4deda5b934a9b55c5ecfeec95ca633edf15e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389263"
---
# <a name="customizing-text-and-image-fields"></a>自訂文字和影像欄位
當您在圖形中定義文字裝飾專案時，它會以文字欄位表示。 如需 TextFields 和其他 ShapeFields 初始化的範例，請檢查 DSL 解決方案中的 Dsl\GeneratedCode\Shapes.cs。

 「欄位」是一種物件，可管理圖形內的區域，例如指派給標籤的空間。 在相同類別的許多圖形之間共用一個多欄位實例。 「欄位」實例不會為每個實例個別儲存標籤的文字：相反地， `GetDisplayText(ShapeElement)` 方法會採用圖形作為參數，而且可以查詢與圖形目前狀態和其模型專案相依的文字。

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>如何判斷文字欄位的外觀
 `DoPaint()`呼叫方法以在螢幕上顯示欄位。 您可以覆寫預設值，也可以覆 `DoPaint(),` 寫它所呼叫的部分方法。 下列預設方法的簡化版本可協助您瞭解如何覆寫預設行為：

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 還有其他幾組 `Get` 方法和 `Default` 屬性，例如 `DefaultMultipleLine/GetMultipleLine()` 。 您可以將值指派給 Default 屬性，以變更圖形欄位之所有實例的值。 若要讓此值從某個圖形實例變更為另一個，或相依于圖形或其模型專案的狀態，請覆寫 `Get` 方法。

## <a name="static-customizations"></a>靜態自訂
 如果您想要變更這個圖形欄位的每個實例，請先找出您是否可以在 DSL 定義中設定屬性。 例如，您可以在屬性視窗中設定字型大小和樣式。

 如果沒有，則覆寫 `InitializeShapeFields` shape 類別的方法，並將值指派給 `Default...` 文字欄位的適當屬性。

> [!WARNING]
> 若要覆寫 `InitializeShapeFields()` ，您必須在 DSL 定義中，將 shape 類別的 [ **產生雙重衍生** ] 屬性設定為 `true` 。

 在此範例中，圖形具有將用於使用者批註的文字欄位。 我們想要使用標準批註字型。 因為這是來自樣式集的標準字型，所以可以設定預設的字型識別碼：

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>動態自訂
 若要讓外觀因圖形或其模型專案的狀態而異，請衍生您自己的子類別， `TextField` 並覆寫一個或多個 `Get...` 方法。 您也必須覆寫圖形的 InitializeShapeFields 方法，並以您自己類別的實例來取代該欄位的實例。

 下列範例會使文字欄位的字型相依于圖形模型專案的布林值網域屬性的狀態。

 若要執行此範例程式碼，請使用最基本的語言範本建立新的 DSL 解決方案。 將布林值網域屬性加入 `AlternateState` 至 ExampleElement 網域類別。 將圖示裝飾專案加入至 ExampleShape 類別，並將其影像設定為點陣圖檔案。 按一下 [ **轉換所有範本**]。 在 DSL 專案中加入新的程式碼檔案，然後插入下列程式碼。

 若要測試程式碼，請按 F5，並在偵錯工具中開啟範例圖表。 圖示的預設狀態應該會顯示。 選取圖形，然後在屬性視窗中，變更 **AlternateState** 屬性的值。 元素名稱的字型應該會變更。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>樣式集
 上述範例顯示如何將文字欄位變更為任何可用的字型。 不過，最好的方法是將其變更為與圖形或應用程式相關聯之一組樣式的其中一組。 若要這樣做，請覆寫 <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> 或 GetTextBrushId () 。

 或者，請考慮藉由覆寫來變更圖形的樣式集 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> 。 這會影響變更所有圖形欄位的字型和筆刷。

## <a name="customizing-image-fields"></a>自訂影像欄位
 當您在圖形中定義影像裝飾專案時，以及當您定義影像圖形時，顯示圖形的區域是由 ImageField 所管理。 如需 ImageFields 和其他 ShapeFields 初始化的範例，請檢查 DSL 解決方案中的 Dsl\GeneratedCode\Shapes.cs。

 ImageField 是管理圖形內區域的物件，例如指派給裝飾專案的空間。 同一個圖形類別的許多圖形之間共用一個 ImageField 實例。 ImageField 實例不會為每個圖形儲存個別的影像：相反地，此 `GetDisplayImage(ShapeElement)` 方法會採用圖形作為參數，而且可以查詢與圖形目前狀態和其模型專案相關的影像。

 如果您想要特殊行為（例如變數影像），您可以建立自己的類別，該類別衍生自 ImageField。

#### <a name="to-create-a-subclass-of-imagefield"></a>若要建立 ImageField 的子類別

1. 在 DSL 定義中，將父圖形類別的 [ **產生雙重衍生** ] 屬性設定為。

2. 覆寫 `InitializeShapeFields` 您的 shape 類別的方法。

    - 在 DSL 專案中建立新的程式碼檔案，並撰寫 shape 類別的部分類別定義。 在該處覆寫方法定義。

3. 檢查 DSL\GeneratedCode\Shapes.cs. 中的程式碼 `InitializeShapeFields`

     在您的覆寫方法中，呼叫基底方法，然後建立您自己的影像欄位類別的實例。 使用此項來取代清單中的一般影像欄位 `shapeFields` 。

## <a name="dynamic-icons"></a>動態圖示
 此範例會根據圖形模型專案的狀態來變更圖示。

> [!WARNING]
> 這個範例示範如何建立動態影像裝飾專案。 但是，如果您只想要根據模型變數的狀態，在一個或兩個影像之間切換，則建立多個影像裝飾專案會比較簡單，請在圖形上的相同位置找到它們，然後再將可見度篩選器設定為相依于模型變數的特定值。 若要設定此篩選器，請選取 DSL 定義中的圖形地圖，開啟 [DSL 詳細資料] 視窗，然後按一下 [裝飾專案] 索引標籤。

 若要執行此範例程式碼，請使用最基本的語言範本建立新的 DSL 解決方案。 將布林值網域屬性加入 `AlternateState` 至 ExampleElement 網域類別。 將圖示裝飾專案加入至 ExampleShape 類別，並將其影像設定為點陣圖檔案。 按一下 [ **轉換所有範本**]。 在 DSL 專案中加入新的程式碼檔案，然後插入下列程式碼。

 若要測試程式碼，請按 F5，並在偵錯工具中開啟範例圖表。 圖示的預設狀態應該會顯示。 選取圖形，然後在屬性視窗中，變更 **AlternateState** 屬性的值。 然後，圖示就會顯示在該圖形上，以90度旋轉。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>另請參閱

- [定義圖案和連接器](../modeling/defining-shapes-and-connectors.md)
- [設定圖表上的背景影像](../modeling/setting-a-background-image-on-a-diagram.md)
- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)