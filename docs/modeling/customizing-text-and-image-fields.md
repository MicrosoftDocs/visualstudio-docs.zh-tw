---
title: "自訂文字和影像欄位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: c551b368ba695f4d78fbe7a885f3896160fa93ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-text-and-image-fields"></a>自訂文字和影像欄位
當您在圖形中定義的文字裝飾項目時，則為代表 TextField。 有關 TextFields 和其他 ShapeFields 初始化的詳細資訊，請檢查 Dsl\GeneratedCode\Shapes.cs DSL 方案中。  
  
 TextField 是管理圖形，例如指派給標籤的空間內的區域的物件。 其中一個 TextField 執行個體共用相同類別的許多圖形之間。 TextField 執行個體不會儲存每個執行個體，分別為標籤的文字： 反而`GetDisplayText(ShapeElement)`方法會採用圖形做為參數，並可以查詢的文字取決於目前的圖形和其模型項目狀態。  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>如何判斷文字欄位的外觀  
 `DoPaint()`呼叫方法來顯示欄位在螢幕上。 您可以覆寫預設`DoPaint(),`或者您可以覆寫其所呼叫的方法。 下列的簡化的版本的預設方法，可協助您了解如何覆寫預設行為：  
  
```  
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
  
 有數個其他成對的`Get`方法和`Default`屬性，例如`DefaultMultipleLine/GetMultipleLine()`。 您可以將值指派給預設屬性，來變更形狀欄位的所有執行個體的值。 若要讓另一個，或依賴的圖形或其模型項目狀態而異一個圖形的執行個體的值，覆寫`Get`方法。  
  
## <a name="static-customizations"></a>靜態的自訂項目  
 如果您想要變更這個圖形欄位的每個執行個體，請先找出是否可以設定屬性，DSL 定義中。 例如，您可以在 [屬性] 視窗中設定字型的大小和樣式。  
  
 如果沒有，則覆寫`InitializeShapeFields`圖形類別和指派到適當的值的方法`Default...`文字欄位的屬性。  
  
> [!WARNING]
>  若要覆寫`InitializeShapeFields()`，您必須設定**會產生兩個衍生**圖形類別的屬性`true`DSL 定義中。  
  
 在此範例中，圖形會有將用於使用者註解的文字欄位。 我們想要使用標準註解的字型。 因為標準的字型樣式集中，所以我們可以設定預設字型 id:  
  
```  
  
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
  
## <a name="dynamic-customizations"></a>動態自訂項目  
 若要讓不同的外觀取決於其模型項目的圖形的狀態，衍生您自己的子類別`TextField`並覆寫一個或多個`Get...`方法。 您也必須覆寫您的形狀 InitializeShapeFields 方法，並且 TextField 的執行個體取代您自己的類別的執行個體。  
  
 下列範例會使相依於圖形的模型項目的布林值的網域屬性的狀態文字欄位的字型。  
  
 若要執行此程式碼範例，建立新 DSL 的方案使用最少的語言的範本。 加入布林網域屬性`AlternateState`ExampleElement 網域類別。 新增圖示 decorator ExampleShape 類別，並設定其影像點陣圖檔案。 按一下**轉換所有範本**。 在 DSL 專案中，加入新的程式碼檔案，然後插入下列程式碼。  
  
 若要測試的程式碼，按下 F5，並在偵錯方案中，開啟範例圖表。 圖示的預設狀態應該會出現。 選取圖形，然後在 [屬性] 視窗中將值變更**AlternateState**屬性。 應該變更的項目名稱的字型。  
  
```  
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
 上述範例顯示如何變更的文字欄位，以及在任何可用的字型。 不過，較佳的方法是將它變更為一組樣式圖案或應用程式相關聯的其中一個。 若要這樣做，您覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A>或 GetTextBrushId()。  
  
 或者，請考慮變更您的形狀的樣式設定，藉由覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>。 這有的字型和筆刷形狀欄位之所有變更的效果。  
  
## <a name="customizing-image-fields"></a>自訂影像欄位  
 當您在圖形中，定義影像裝飾項目時，並定義影像圖形時，由 ImageField 管理圖形中的顯示區域。 有關 ImageFields 和其他 ShapeFields 初始化的詳細資訊，請檢查 Dsl\GeneratedCode\Shapes.cs DSL 方案中。  
  
 ImageField 是管理圖形，例如指派給裝飾項目的空間內的區域的物件。 一個 ImageField 執行個體共用相同的圖形類別的許多圖形之間。 ImageField 執行個體不會儲存每個圖形的個別映像： 反而`GetDisplayImage(ShapeElement)`方法會採用圖形做為參數，並可以查詢圖形和其模型項目的目前狀態而定的映像。  
  
 如果您想特殊的行為，例如變數的映像，您可以建立您自己的類別衍生自 ImageField。  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>若要建立的 ImageField 子類別  
  
1.  設定**會產生兩個衍生**DSL 定義中的父圖案類別的屬性。  
  
2.  覆寫`InitializeShapeFields`圖形類別的方法。  
  
    -   在 DSL 專案中，建立新的程式碼檔案，並將寫入圖形類別的部分類別定義。 覆寫的方法定義。  
  
3.  檢查使用的程式碼`InitializeShapeFields`DSL\GeneratedCode\Shapes.cs 中。  
  
     在您覆寫的方法會呼叫基底方法，然後建立您自己的映像欄位類別的執行個體。 使用此選項可取代中的規則的影像欄位`shapeFields`清單。  
  
## <a name="dynamic-icons"></a>動態圖示  
 此範例會將相依於圖形的模型項目的狀態變更的圖示。  
  
> [!WARNING]
>  這個範例示範如何進行動態影像的裝飾項目。 但如果您只想要根據的模型變數狀態的一或兩個映像之間切換，很容易建立數個影像的裝飾項目，在圖形上的相同位置中找到它們，然後設定 要取決於模型的特定值的可見性篩選變數。 若要設定此篩選器，選取圖形地圖 DSL 定義中，開啟 DSL 詳細資料 視窗中，然後按一下 裝飾項目 索引標籤。  
  
 若要執行此程式碼範例，建立新 DSL 的方案使用最少的語言的範本。 加入布林網域屬性`AlternateState`ExampleElement 網域類別。 新增圖示 decorator ExampleShape 類別，並設定其影像點陣圖檔案。 按一下**轉換所有範本**。 在 DSL 專案中，加入新的程式碼檔案，然後插入下列程式碼。  
  
 若要測試的程式碼，按下 F5，並在偵錯方案中，開啟範例圖表。 圖示的預設狀態應該會出現。 選取圖形，然後在 [屬性] 視窗中將值變更**AlternateState**屬性。 應該再出現旋轉 90 度，該圖形上透過圖示。  
  
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
 [定義圖形和連接器](../modeling/defining-shapes-and-connectors.md)   
 [在圖表上設定的背景影像](../modeling/setting-a-background-image-on-a-diagram.md)   
 [巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)