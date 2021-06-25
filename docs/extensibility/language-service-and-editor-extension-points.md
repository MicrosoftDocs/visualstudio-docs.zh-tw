---
title: 語言服務及編輯器擴充點 |Microsoft Docs
description: 瞭解您可以擴充的 Visual Studio 程式碼編輯器中的擴充點，包括大部分的語言服務功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 293851f1f3e72508a9bc119fb7551b0118ab2a9b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903143"
---
# <a name="language-service-and-editor-extension-points"></a>語言服務及編輯器擴充點
編輯器會提供擴充點，讓您可以擴充為 Managed Extensibility Framework (MEF) 元件元件，包括大部分的語言服務功能。 以下是主要的延伸點類別：

- 內容類型

- 分類類型和分類格式

- 邊界和捲軸

- 標籤

- 裝飾品

- 滑鼠處理器

- 捨棄處理常式

- 選項

- IntelliSense

## <a name="extend-content-types"></a>擴充內容類型
 內容類型是編輯器所處理的文字種類的定義，例如 "text"、"code" 或 "CSharp"。 您可以宣告類型的變數 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> ，並提供新的內容類型為唯一名稱，藉此定義新的內容類型。 若要使用編輯器註冊內容類型，請將它與下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 這是內容類型的名稱。

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> 這是衍生這個內容類型的內容類型名稱。 內容類型可以繼承自多個其他內容類型。

  因為 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 類別是密封的，所以您可以將它匯出為沒有類型參數。

  下列範例會顯示內容類型定義的匯出屬性。

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 內容類型可以是以零或多個預先存在的內容類型為基礎。 以下是內建類型：

- 任何：基本內容類型。 所有其他內容類型的父系。

- Text：非投射內容的基本類型。 繼承自「任何」。

- 純文字：適用于非程式碼文字。 繼承自 "text"。

- 程式碼：適用于所有種類的程式碼。 繼承自 "text"。

- 惰性：從任何類型的處理中排除文字。 此內容類型的文字將不會套用任何副檔名。

- 投射：適用于投射緩衝區的內容。 繼承自「任何」。

- Intellisense：適用于 IntelliSense 的內容。 繼承自 "text"。

- Sighelp： signature help。 繼承自 "intellisense"。

- Sighelp-doc： signature 說明文件。 繼承自 "intellisense"。

  這些是 Visual Studio 所定義的部分內容類型，以及 Visual Studio 中裝載的部分語言：

- 基本

- C/C++

- ConsoleOutput

- CSharp

- CSS

- ENC

- 裡

- F#

- HTML

- JScript

- XAML

- XML

  若要探索可用內容類型的清單，請匯入 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> ，以維護編輯器的內容類型集合。 下列程式碼會將此服務匯入為屬性。

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 若要將內容類型與副檔名產生關聯，請使用 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 。

> [!NOTE]
> 在 Visual Studio 中，會使用 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> 語言服務封裝上的來註冊副檔名。 會將 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF 內容類型與以這種方式註冊的副檔名產生關聯。

 若要將副檔名匯出至內容類型定義，您必須包含下列屬性：

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>：指定副檔名。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>：指定內容類型。

  因為 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 類別是密封的，所以您可以將它匯出為沒有類型參數。

  下列範例會示範如何將副檔名的屬性匯出至內容類型定義。

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 會 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> 管理副檔名和內容類型之間的關聯。

## <a name="extend-classification-types-and-classification-formats"></a>擴充分類類型和分類格式
 您可以使用分類類型來定義要提供不同處理 (的文字類型，例如，將 "關鍵字" 文字標示為藍色，並將 "comment" 文字標示為綠色) 。 宣告類型的變數 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> ，並提供唯一的名稱，以定義新的分類類型。

 若要使用編輯器註冊分類類型，請將它與下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：分類類型的名稱。

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>：此分類型別所繼承的分類型別名稱。 所有分類類型都繼承自「文字」，而分類類型可以繼承自多個其他分類類型。

  因為 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 類別是密封的，所以您可以將它匯出為沒有類型參數。

  下列範例會顯示分類類型定義上的匯出屬性。

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>提供對標準分類的存取。 內建分類類型包括：

- "text"

- 「自然語言」 (衍生自「文字」 ) 

- 「正式語言」 (衍生自「文字」 ) 

- "string" (衍生自 "literal" ) 

- 「字元」 (衍生自「常值」 ) 

- 「數值」 (衍生自「常值」 ) 

  一組不同的錯誤類型會繼承自 <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> 。 其中包括下列錯誤類型：

- 「語法錯誤」

- 「編譯器錯誤」

- 「其他錯誤」

- 條

  若要探索可用分類類型的清單，請匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> ，以維護編輯器的分類類型集合。 下列程式碼會將此服務匯入為屬性。

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 您可以為新的分類類型定義分類格式定義。 從衍生類別 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> ，並將它與類型 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> 一起匯出，以及下列屬性：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：格式的名稱。

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>：格式的顯示名稱。

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>：指定格式是否出現在 [**選項**] 對話方塊的 [字型 **和色彩**] 頁面上。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>：格式的優先順序。 有效的值來自 <xref:Microsoft.VisualStudio.Text.Classification.Priority> 。

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>：此格式所對應之分類類型的名稱。

  下列範例顯示分類格式定義的匯出屬性。

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 若要探索可用格式的清單，請匯入 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> ，它會維護編輯器的格式集合。 下列程式碼會將此服務匯入為屬性。

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>擴充邊界和捲軸
 除了文字視圖本身之外，邊界和捲軸也是編輯器的主要 view 元素。 除了出現在文字視圖周圍的標準邊界之外，您還可以提供任何數目的邊界。

 執行 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> 介面來定義邊界。 您也必須執行 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 介面來建立邊界。

 若要向編輯器註冊邊界提供者，您必須連同下列屬性一起匯出提供者：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：邊界的名稱。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>：邊際出現的順序（相對於其他邊界）。

   以下是內建的邊界：

  - 「Wpf 水準捲軸」

  - 「Wpf 垂直捲動條」

  - 「Wpf 行號邊界」

    具有 order 屬性的水準邊界 `After="Wpf Horizontal Scrollbar"` 會顯示在內建邊界下方，而具有 order 屬性的水準邊界 `Before ="Wpf Horizontal Scrollbar"` 會顯示在內建邊界的上方。 具有 order 屬性的右垂直邊界 `After="Wpf Vertical Scrollbar"` 會顯示在捲軸的右邊。 具有 order 屬性的左方垂直邊界 `After="Wpf Line Number Margin"` 會顯示在行號邊界 (的左邊，如果看得到) 則為。

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>：邊界的種類 (左、右、上或下) 。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： (的內容類型，例如，「文字」或「程式碼」 ) ，其邊界有效。

  下列範例會針對出現在行號邊界右邊的邊界，顯示邊界提供者上的匯出屬性。

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>擴充標記
 標記是一種將資料與不同類型的文字產生關聯的方式。 在許多情況下，相關聯的資料會顯示為視覺效果，但並非所有標記都有視覺效果呈現。 您可以藉由實作為定義自己的標記類型 <xref:Microsoft.VisualStudio.Text.Tagging.ITag> 。 您也必須執行 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 以提供指定之文字範圍集的標記，以及提供標記的 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 。 您必須將標記提供者與下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： (的內容類型，例如，「文字」或「程式碼」 ) ，您的標記有效。

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>：標記的種類。

  下列範例示範如何在標記提供者上匯出屬性。

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> 下列為內建的標記種類：

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>：與相關聯 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 。

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>：與錯誤類型相關聯。

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>：與裝飾相關聯。

  > [!NOTE]
  > 如需的範例 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ，請參閱逐步解說：反白 [顯示文字](../extensibility/walkthrough-highlighting-text.md)中的 HighlightWordTag 定義。

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>：與可在大綱中展開或折迭的區域相關聯。

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>：定義裝飾在文字視圖中佔用的空間。 如需空間協調裝飾的詳細資訊，請參閱下一節。

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>：提供裝飾的自動間距和調整大小。

  若要尋找並使用標籤的緩衝區和視圖，請匯入 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> 或 <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> ，以提供所 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 要求型別的。 下列程式碼會將此服務匯入為屬性。

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>標記和 MarkerFormatDefinitions
 您可以擴充 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 類別來定義標記的外觀。 您必須將類別 (匯出為 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> 具有下列屬性的) ：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：用來參考此格式的名稱

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>：這會使格式顯示在 UI 中

  在此函數中，您可以定義標記的顯示名稱和外觀。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 定義填滿色彩，並 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> 定義框線色彩。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>是格式定義的可當地語系化名稱。

  以下是格式定義的範例：

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 若要將此格式定義套用至標記，請參考您在類別的 name 屬性中所設定的名稱， (不是顯示名稱) 。

> [!NOTE]
> 如需的範例 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> ，請參閱逐步解說：反白 [顯示文字](../extensibility/walkthrough-highlighting-text.md)中的 HighlightWordFormatDefinition 類別。

## <a name="extend-adornments"></a>擴充裝飾
 裝飾定義了視覺效果，可將其新增至文字視圖或文字視圖本身所顯示的文字。 您可以將自己的裝飾定義為任何類型 <xref:System.Windows.UIElement> 。

 在您的裝飾類別中，您必須宣告 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> 。 若要註冊您的裝飾層，請將它與下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：裝飾的名稱。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>：相對於其他裝飾層的裝飾順序。 類別會 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 定義四個預設圖層：選取範圍、大綱、插入號和文字。

  下列範例顯示裝飾層定義上的匯出屬性。

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 您必須建立第二個類別，透過具現 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 化裝飾來執行和處理其 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 事件。 您必須將此類別與下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： (的內容類型，例如，「文字」或「程式碼」 ) ，裝飾是有效的。

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>：此裝飾有效的文字視圖種類。 類別 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 具有預先定義的文字視圖角色集合。 例如， <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 主要用於檔案的文字視圖。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 用於使用者可以使用滑鼠和鍵盤編輯或流覽的文字視圖。 視圖的範例 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 包括編輯器文字視圖和 **輸出** 視窗。

  下列範例會顯示裝飾提供者的匯出屬性。

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 空間協調裝飾是指在與文字相同層級的空間。 若要建立這種類型的裝飾，您必須定義繼承自的標記類別 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> ，以定義裝飾所佔用的空間量。

 如同所有裝飾，您必須匯出裝飾層定義。

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 若要具現化空間協調裝飾，您必須建立一個實作為的類別，該類別 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 除了可執行 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (與其他種類的裝飾) 一樣。

 若要註冊標記提供者，您必須將它與下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>：您的裝飾 (的內容類型，例如「文字」或「程式碼」 ) 。

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>：此標記或裝飾有效的文字視圖種類。 類別 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 具有預先定義的文字視圖角色集合。 例如， <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 主要用於檔案的文字視圖。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 用於使用者可以使用滑鼠和鍵盤編輯或流覽的文字視圖。 視圖的範例 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 包括編輯器文字視圖和 **輸出** 視窗。

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>：您已定義的標記或裝飾種類。 您必須為加入第二個 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> 。

  下列範例會針對空間協調裝飾標記，顯示標記提供者的匯出屬性。

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>擴充滑鼠處理器
 您可以新增滑鼠輸入的特殊處理。 建立繼承自的類別， <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> 並覆寫您想要處理之輸入的滑鼠事件。 您也必須 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> 在第二個類別中執行，並將它與 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 指定 (內容類型的一起匯出，例如，「文字」或「程式碼」 ) ，您的滑鼠處理常式是有效的。

 下列範例顯示滑鼠處理器提供者上的匯出屬性。

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>擴充 drop 處理常式
 您可以藉由建立可執行檔類別和第二個執行的類別，來自訂特定種類的文字之卸載處理常式的行為 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> ， <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> 以建立 drop 處理常式。 您必須將 drop 處理常式連同下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>：此捨棄處理常式有效的文字格式。 下列格式會依優先順序從最高到最低進行處理：

  1. 任何自訂格式

  2. Filedrop]

  3. EnhancedMetafile

  4. WaveAudio

  5. Riff

  6. Dif

  7. Locale

  8. 調色盤

  9. PenData

  10. 可序列化

  11. >symboliclink

  12. Xaml

  13. XamlPackage

  14. Tiff

  15. 點陣圖

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. HTML 格式

  21. UnicodeText

  22. OEMText

  23. Text

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： drop 處理常式的名稱。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>：在預設卸載處理常式之前或之後的放置處理常式順序。 Visual Studio 的預設 drop 處理常式名為 "DefaultFileDropHandler"。

  下列範例顯示 drop handler provider 的 export 屬性。

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>擴充編輯器選項
 您可以將選項定義為只在特定範圍（例如，在文字視圖中）有效。 編輯器提供這組預先定義的選項： [編輯器選項]、[視圖選項] 和 [Windows Presentation Foundation] (WPF) 視圖選項。 您可以在、和中找到這些選項 <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> 。

 若要加入新的選項，請從下列其中一個選項定義類別衍生類別：

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  下列範例顯示如何匯出具有布林值的選項定義。

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>擴充 IntelliSense
 IntelliSense 是一組功能的一般詞彙，可提供結構化文字的相關資訊，以及它的語句完成。 這些功能包括語句完成、簽章說明、快速諮詢和 light 燈泡。 語句完成可協助使用者正確地輸入語言關鍵字或成員名稱。 簽章說明會顯示使用者剛剛輸入之方法的簽章或簽章。 當滑鼠停留在類型或成員名稱時，[快速諮詢] 會顯示其完整簽章。 燈泡會針對特定內容中的特定識別碼提供額外的動作，例如，在重新命名一次之後，重新命名所有出現的變數。

 在所有情況下，IntelliSense 功能的設計都很相同：

- IntelliSense 訊息 *代理* 程式負責整體的進程。

- IntelliSense *會話* 代表觸發者和選取範圍的順序或取消之間的事件順序。 會話通常會由某些使用者手勢觸發。

- IntelliSense *控制器* 負責決定會話的開始和結束時間。 它也會決定何時應認可資訊，以及何時應取消會話。

- IntelliSense *來源* 提供內容，並決定最符合的結果。

- IntelliSense 展示 *者* 負責顯示內容。

  在大部分情況下，我們建議您至少提供來源和控制器。 如果您想要自訂顯示，也可以提供簡報者。

### <a name="implement-an-intellisense-source"></a>執行 IntelliSense 來源
 若要自訂來源，您必須執行下列其中一個 (或多個) 下列來源介面：

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 已取代為 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> 。

 此外，您必須執行相同類型的提供者：

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 已取代為 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> 。

 您必須將提供者與下列屬性一起匯出：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：來源的名稱。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： (的內容類型，例如，要套用來源的「文字」或「程式碼」 ) 。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>：來源的出現順序 (與其他來源) 相關。

- 下列範例會顯示完成來源提供者的匯出屬性。

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 如需有關如何執行 IntelliSense 來源的詳細資訊，請參閱下列逐步解說：

- [逐步解說：顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [逐步解說：顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)

- [逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>執行 IntelliSense 控制器
 若要自訂控制器，您必須執行 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> 介面。 此外，您必須搭配下列屬性來執行控制器提供者：

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：控制器的名稱。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： (的內容類型，例如，要套用控制器的「文字」或「程式碼」 ) 。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>：控制器 (與其他控制器) 的出現順序相關聯的順序。

  下列範例會顯示完成控制器提供者上的匯出屬性。

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 如需使用 IntelliSense 控制器的詳細資訊，請參閱下列逐步解說：

- [逐步解說：顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
