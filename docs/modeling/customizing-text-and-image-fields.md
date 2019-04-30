---
title: 自訂文字和影像欄位
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607809b05688931b139b27fec1803719b928dfea
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445824"
---
# <a name="customizing-text-and-image-fields"></a>自訂文字和影像欄位
當您在圖形中定義的文字裝飾項目時，它被以文字欄位。 例如 TextFields 和其他 ShapeFields 初始化的詳細資訊，請在您的 DSL 方案中檢查 Dsl\GeneratedCode\Shapes.cs。

 文字欄位是物件，該圖形，例如指派給標籤的空間內的區域物件。 其中一個文字欄位的執行個體共用相同類別的許多圖形之間。 文字欄位的執行個體不會儲存每個執行個體，分別為標籤的文字： 反而`GetDisplayText(ShapeElement)`方法會做為參數，圖形，並可以查閱相依於目前的圖形與模型項目狀態的文字。

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>如何判斷文字欄位的外觀
 `DoPaint()`呼叫方法來顯示欄位在螢幕上。 您可以覆寫預設`DoPaint(),`或者您可以覆寫其所呼叫的方法。 以下的簡化的版本的預設方法可協助您了解如何覆寫預設行為：

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

 有數個其他組`Get`方法和`Default`屬性，例如`DefaultMultipleLine/GetMultipleLine()`。 您可以將值指派給預設屬性，變更形狀欄位的所有執行個體的值。 若要讓另一個，或依賴的圖形或其模型項目狀態會因一個圖形的執行個體的值，覆寫`Get`方法。

## <a name="static-customizations"></a>靜態的自訂項目
 如果您想要變更此形狀欄位的每個執行個體，請先找出是否設定屬性，以及在 DSL 定義中。 例如，您可以在 [屬性] 視窗中設定字型的大小和樣式。

 如果沒有，則覆寫`InitializeShapeFields`shape 類別，以及指派值給適當的方法`Default...`文字欄位的屬性。

> [!WARNING]
> 若要覆寫`InitializeShapeFields()`，您必須設定**產生雙衍生**屬性的圖形類別`true`DSL 定義中。

 在此範例中，圖形會有將用於使用者註解的文字欄位。 我們想要使用標準的註解的字型。 由於這是標準的字型樣式集中，我們可以設定預設字型 id:

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

## <a name="dynamic-customizations"></a>動態的自訂項目
 若要讓不同的外觀取決於狀態的圖形或其模型項目，衍生您自己的子類別的`TextField`，並覆寫一個或多個`Get...`方法。 您也必須覆寫您的形狀 InitializeShapeFields 方法，並取代您自己的類別的執行個體中的文字欄位的執行個體。

 下列範例會讓文字欄位的文字取決於圖形的模型項目的布林值的網域屬性的狀態。

 若要執行此程式碼範例，建立新的 DSL 方案，使用 [最小語言] 範本。 將布林值的網域屬性加入`AlternateState`ExampleElement 網域類別。 將圖示裝飾項目加入 ExampleShape 類別，並設定其影像點陣圖檔案。 按一下 **轉換所有範本**。 在 DSL 專案中，加入新的程式碼檔案，並插入下列程式碼。

 若要測試的程式碼，按下 f5 鍵，並在偵錯方案中，開啟範例圖表。 圖示的預設狀態應該會出現。 選取圖形，然後在 [屬性] 視窗中，將值變更**AlternateState**屬性。 應變更的項目名稱的字型。

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

## <a name="style-sets"></a>樣式設定
 上述範例顯示如何變更的文字欄位，以及在任何可用的字型。 不過，較佳的方法是將它變更為其中一組與圖形或應用程式相關聯的樣式。 若要這樣做，您覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A>或 GetTextBrushId()。

 或者，請考慮變更您的形狀的樣式集，藉由覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>。 這有變更字型和筆刷形狀欄位之所有的效果。

## <a name="customizing-image-fields"></a>自訂映像欄位
 當您在圖形中，定義影像裝飾項目，而且當您定義了影像圖形，其中會顯示在圖形區域都會受到 ImageField。 例如 ImageFields 和其他 ShapeFields 初始化的詳細資訊，請在您的 DSL 方案中檢查 Dsl\GeneratedCode\Shapes.cs。

 ImageField 是物件，該圖形，例如指派給裝飾項的空間內的區域物件。 許多相同的圖形類別的形狀之間共用一個 ImageField 執行個體。 ImageField 執行個體不會儲存每個圖形的個別映像： 反而`GetDisplayImage(ShapeElement)`方法會做為參數，圖形，並相依於目前的圖形與模型項目狀態的映像可以查閱。

 如果您想特殊的行為，例如變數的映像，您可以建立您自己的類別衍生自 ImageField。

#### <a name="to-create-a-subclass-of-imagefield"></a>若要建立的 ImageField 子類別

1. 設定**產生雙衍生**DSL 定義中的父圖形類別的屬性。

2. 覆寫`InitializeShapeFields`圖形類別的方法。

    - 在 DSL 專案中，建立新的程式碼檔案並寫入 shape 類別的部分類別定義。 覆寫的方法定義。

3. 檢查的程式碼`InitializeShapeFields`DSL\GeneratedCode\Shapes.cs 中。

     在您覆寫的方法，呼叫基底方法，然後建立您自己的映像欄位類別的執行個體。 使用此選項可將一般的映像 欄位中取代`shapeFields`清單。

## <a name="dynamic-icons"></a>動態圖示
 此範例會將取決於圖形的模型項目的狀態變更的圖示。

> [!WARNING]
> 此範例示範如何進行動態影像的裝飾項目。 但如果您只想要根據的模型變數狀態的一或兩個映像之間切換，很容易建立數個影像的裝飾項目，在圖形上，相同的位置找到這些服務，然後設定取決於模型的特定值的可見性篩選變數。 若要設定此篩選器，選取圖形對應 DSL 定義中，開啟 [DSL 詳細資料] 視窗中，然後按一下 [裝飾項目] 索引標籤。

 若要執行此程式碼範例，建立新的 DSL 方案，使用 [最小語言] 範本。 將布林值的網域屬性加入`AlternateState`ExampleElement 網域類別。 將圖示裝飾項目加入 ExampleShape 類別，並設定其影像點陣圖檔案。 按一下 **轉換所有範本**。 在 DSL 專案中，加入新的程式碼檔案，並插入下列程式碼。

 若要測試的程式碼，按下 f5 鍵，並在偵錯方案中，開啟範例圖表。 圖示的預設狀態應該會出現。 選取圖形，然後在 [屬性] 視窗中，將值變更**AlternateState**屬性。 應該再出現旋轉 90 度，該圖形上透過圖示。

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

- [定義圖案和接點](../modeling/defining-shapes-and-connectors.md)
- [設定圖表上的背景影像](../modeling/setting-a-background-image-on-a-diagram.md)
- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)