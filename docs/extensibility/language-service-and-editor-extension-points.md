---
title: 語言服務和編輯器擴展點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703050"
---
# <a name="language-service-and-editor-extension-points"></a>語言服務及編輯器擴充點
編輯器提供擴充點,您可以將擴充為託管擴展框架 (MEF) 元件,包括大多數語言服務功能。 這些是主要擴充點類別:

- 內容類型

- 類別型態與類別格式

- 邊距與捲動條

- Tags

- 裝飾品

- 滑鼠處理器

- 放置處理常式

- 選項。

- IntelliSense

## <a name="extend-content-types"></a>延伸內容類型
 內容類型是編輯器處理的文本類型的定義,例如"文字"、"代碼"或"CSharp"。 通過聲明類型的<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>變數並給新內容類型指定唯一名稱,可以定義新的內容類型。 要向編輯器註冊內容類型,請將其與以下屬性一起匯出:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>是內容類型的名稱。

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>是派生此內容類型的內容類型的名稱。 內容類型可能從多個其他內容類型繼承。

  由於類<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>是密封的,因此無需類型參數即可匯出它。

  下面的範例顯示內容類型定義上的匯出屬性。

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 內容類型可以基於零個或多個預先存在的內容類型。 這些是內建型態:

- 任何:基本內容類型。 所有其他內容類型的父級。

- 文本:非投影內容的基本類型。 從"任意"繼承。

- 純文字:用於非代碼文本。 從"文本"繼承。

- 代碼:用於各種代碼。 從"文本"繼承。

- 惰性:從任何類型的處理中排除文本。 此內容類型的文本永遠不會應用任何擴展。

- 投影:用於投影緩衝區的內容。 從"任意"繼承。

- 感知:對於IntelliSense的內容。 從"文本"繼承。

- Sighelp:簽名説明。 從"理智"繼承。

- Sighelp-doc:簽名幫助文檔。 從"理智"繼承。

  以下是由 Visual Studio 定義的一些內容類型,以及 Visual Studio 中託管的一些語言:

- 基本

- C/C++

- 主控台輸出

- CSharp

- CSS

- ENC

- 尋找結果

- F#

- HTML

- JScript

- XAML

- XML

  要探索可用內容類型的清單,匯入,<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>該清單維護編輯器的內容類型的集合。 以下代碼將此服務導入為屬性。

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 要將內容類型與檔案名副檔名相關聯,請<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>使用 。

> [!NOTE]
> 在 Visual Studio<xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>中,使用語言服務包註冊檔名副檔名。 將<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>MEF 內容類型與以這種方式註冊的檔名擴展名關聯。

 要將檔案名副檔名匯出到內容類型定義,必須包括以下屬性:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>:指定檔案名副檔名。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:指定內容類型。

  由於類<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>是密封的,因此無需類型參數即可匯出它。

  下面的範例顯示內容類型定義的檔名擴展名上的匯出屬性。

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 管理<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>檔案名副檔名和內容類型之間的關聯。

## <a name="extend-classification-types-and-classification-formats"></a>延伸類別型態與類別格式
 可以使用分類類型來定義要為其提供不同處理的文本類型(例如,將"關鍵字"文本著色為藍色和"註釋"文本為綠色)。 通過聲明類型的<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>變數並給它指定唯一名稱來定義新的分類類型。

 要向編輯器註冊分類類型,請將其與以下屬性一起匯出:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:分類類型的名稱。

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>:此分類類型繼承的分類類型的名稱。 所有分類類型都從"文本"繼承,分類類型可能從多個其他分類類型繼承。

  由於類<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>是密封的,因此無需類型參數即可匯出它。

  下面的範例在分類類型定義上顯示匯出屬性。

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 提供<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>對標準分類的訪問。 內建類別類型包括:

- "text"

- "自然語言"(源自"文字")

- 「正式語言」(源自"文字")

- 字串"(派生自"文字")

- 字元"(派生自"文字")

- "數位"(派生自"文字")

  從 繼承<xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>的一組不同的錯誤類型。 它們包括以下錯誤型態:

- 語法錯誤"

- "編譯器錯誤"

- "其他錯誤"

- "警告"

  要發現可用分類類型的清單,匯入,<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>該清單維護編輯器的分類類型的集合。 以下代碼將此服務導入為屬性。

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 您可以為新分類類型定義分類格式定義。 從<xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition>派生類,並匯出它與<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>類型 ,以及以下屬性:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:格式的名稱。

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>:格式的顯示名稱。

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>:指定格式是否顯示在 **「選項**」對話框的「**字型和顏色**」 頁上。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>:格式的優先順序。 合法值是<xref:Microsoft.VisualStudio.Text.Classification.Priority>。

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>:映射此格式的分類類型的名稱。

  下面的範例在分類格式定義上顯示匯出屬性。

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 要探索可用格式的清單,匯入,<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>此清單維護編輯器的格式集合。 以下代碼將此服務導入為屬性。

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>擴充邊界與捲動條
 邊距和滾動條是編輯器的主要視圖元素,除了文本檢視本身。 除了文本視圖周圍顯示的標準邊距之外,還可以提供任意數量的邊距。

 實現介面<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin>以定義邊距。 還必須實現<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>介面以創建邊距。

 要向編輯器註冊邊距提供程式,必須匯出提供者以及以下屬性:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:邊距的名稱。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>:相對於其他邊距,邊距的顯示順序。

   這些是內建邊距:

  - "Wpf 水平滾動條"

  - "Wpf 垂直滾動條"

  - "Wpf 行號邊距"

    具有 order`After="Wpf Horizontal Scrollbar"`屬性的水平邊距顯示在內置邊距下方,`Before ="Wpf Horizontal Scrollbar"`具有訂單 屬性的水平邊距顯示在內置邊距上方。 具有 順序`After="Wpf Vertical Scrollbar"`屬性的右垂直邊距顯示在滾動條的右側。 具有 order`After="Wpf Line Number Margin"`屬性的 左側垂直邊距顯示在行號邊距的左側(如果可見)。

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>:邊距類型(左、右、上或下)。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:您的邊距有效的內容類型(例如,"文本"或"代碼")。

  下面的範例顯示行號邊距右側的邊距供應商上的匯出屬性。

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>延伸標記
 標記是將數據與不同類型的文本關聯的一種方式。 在許多情況下,關聯的數據顯示為視覺效果,但並非所有標記都有可視表示。 您可以通過<xref:Microsoft.VisualStudio.Text.Tagging.ITag>實現 來定義自己的標記類型。 還必須實現<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>為給定的文本範圍集提供標記,並<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>為 提供標記器。 您必須匯出標記提供者以及以下屬性:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:標記有效的內容類型(例如,"文本"或"代碼")。

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>:標記的種類。

  下面的範例顯示標記提供程式上的匯出屬性。

\<代碼內容霍爾德></CodeContentPlaceHolder>8 以下類型的標記是內置的:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>:<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>與 關聯。

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>:與錯誤類型關聯。

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>:與修飾相關聯。

  > [!NOTE]
  > 有關的範例<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>,請參閱演練中的高光字標籤定義[:突出顯示文字](../extensibility/walkthrough-highlighting-text.md)。

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>:與可在大綱中展開或摺疊的區域關聯。

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>:定義修飾在文本視圖中佔用的空間。 有關空間協商裝飾的詳細資訊,請參閱以下部分。

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>:為裝飾提供自動間距和大小調整。

  要尋找與使用緩衝區與檢視的標記,請匯入 提供<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>要求類型的<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>或<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>。 以下代碼將此服務導入為屬性。

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>標記與標記格式定義
 可以擴展類<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>以定義標記的外觀。 您必須使用以下屬性匯出類別<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>( 作為 ):

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:用於參考此格式的名稱

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>:這將導致格式顯示在 UI 中

  在構造函數中,定義標記的顯示名稱和外觀。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>定義填充顏色,並<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A>定義邊框顏色。 是<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>格式定義的可本地化名稱。

  下面是格式定義的範例:

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

 要將此格式定義應用於標記,請引用在類的名稱屬性(而不是顯示名稱)中設置的名稱。

> [!NOTE]
> 有關的範例<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>,請參閱演練中的高光字格式定義類別[:突出顯示文字](../extensibility/walkthrough-highlighting-text.md)。

## <a name="extend-adornments"></a>擴充裝飾
 裝飾定義可以添加到文字檢視中顯示的文本或文本視圖本身的視覺效果。 您可以將自己的修飾定義為任何類型的<xref:System.Windows.UIElement>。

 在修飾類中,必須聲明<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>。 要註冊修飾圖層,請將其與以下屬性一起匯出:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:修飾的名稱。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>:相對於其他裝飾層的修飾順序。 該類<xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers>定義四個預設圖層:選擇、大綱、Caret 和文本。

  下面的範例顯示修飾圖層定義上的匯出屬性。

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 您必須創建第二個類,通過<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>實例化修<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>飾 實現和處理其事件。 您必須將此類與以下屬性一起匯出:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:修飾有效的內容類型(例如,"文本"或"代碼")。

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>:此修飾有效的文本視圖類型。 類<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>具有預定義的文本視圖角色集。 例如,<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>主要用於檔的文本檢視。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>用於使用者可以使用滑鼠和鍵盤編輯或導航的文本檢視。 檢視的範例<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>包括編輯器文字檢視和 **「輸出」** 視窗。

  下面的範例顯示修飾提供程式上的匯出屬性。

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 空間協商修飾是指佔用與文本相同的空間的修飾。 要創建此類修飾,必須定義從<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>繼承的標記類,該類定義修飾佔用的空間量。

 與所有修飾一樣,必須匯出修飾圖層定義。

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 要實例化空間協商修飾,除了實現<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider><xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>的類(與其他類型的修飾一樣),還必須創建實現的類。

 要註冊標記提供程式,必須將其與以下屬性一起匯出:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:裝飾有效的內容類型(例如,"文本"或"代碼")。

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>:此標記或修飾有效的文本視圖類型。 類<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>具有預定義的文本視圖角色集。 例如,<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>主要用於檔的文本檢視。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>用於使用者可以使用滑鼠和鍵盤編輯或導航的文本檢視。 檢視的範例<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>包括編輯器文字檢視和 **「輸出」** 視窗。

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>:您定義的標記或修飾類型。 必須為<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>添加<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>第二秒。

  下面的範例顯示標記器提供程式上的空間協商修飾標記的匯出屬性。

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>延伸滑鼠處理器
 您可以為滑鼠輸入添加特殊處理。 建立從繼承<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>和覆蓋要處理的輸入的滑鼠事件的類。 還必須在第二個<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>類中實現,並將其<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>與 指定滑鼠處理程式有效的內容類型(例如,"文本"或"代碼")一起匯出。

 下面的範例顯示滑鼠處理器提供程式上的匯出屬性。

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>延伸式程式
 可以通過創建<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler>實現的類和第二個<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider>實現 以創建放置處理程式的類來自定義特定文本類型的放置處理程序的行為。 您必須匯出放置處理程式以及以下屬性:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>:此放置處理程式有效的文本格式。 以下格式按優先權順序從最高到最低的順序處理:

  1. 任何自訂格式

  2. 檔案丟棄

  3. 增強中繼檔

  4. 波迪奧

  5. 裡夫

  6. 迪夫

  7. Locale

  8. 調色盤

  9. 筆資料

  10. 可序列化

  11. 符號連結

  12. Xaml

  13. Xaml 包裝

  14. Tiff

  15. 點陣圖

  16. 迪布

  17. 中繼圖片

  18. CSV

  19. System.String

  20. HTML 格式

  21. Unicode文字

  22. OEM 文字

  23. Text

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:放置處理程式的名稱。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>:在預設放置處理程式之前或之後放置處理程序的順序。 Visual Studio 的預設放置處理程式名為"預設檔刪除處理程式"。

  下面的範例顯示放置處理程式提供程式上的匯出屬性。

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>延伸編輯器選項
 可以將選項定義為僅在特定作用域中有效,例如,在文本視圖中。 編輯器提供這組預定義選項:編輯器選項、檢視選項和 Windows 簡報文稿基礎 (WPF) 檢視選項。 可以<xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>找到這些選項 ,<xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions><xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>與 。

 要新增新選項,可以從以下選項定義類別之一派生類:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  下面的範例展示如何匯出具有布林值的選項定義。

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>擴充感知
 IntelliSense 是一組功能的通用術語,提供有關結構化文本的資訊併為其完成語句。 這些功能包括語句完成、簽名説明、快速資訊和燈泡。 語句完成可幫助使用者正確鍵入語言關鍵字或成員名稱。 簽名幫助顯示用戶剛剛鍵入的方法的簽名或簽名。 當滑鼠停留在該類型或成員名稱上時,快速資訊將顯示類型或成員名稱的完整簽名。 燈泡為某些上下文中的某些標識符提供其他操作,例如,重新命名變數的所有匹配項後重新命名一個發生情況。

 在所有情況下,IntelliSense 功能的設計都大致相同:

- IntelliSense*經紀商*負責整個流程。

- IntelliSense*工作階段*表示演示者觸發與提交或取消所選內容之間的事件序列。 會話通常由某些用戶手勢觸發。

- IntelliSense*控制器*負責決定會話何時開始和結束。 它還決定何時提交資訊以及何時取消會話。

- IntelliSense*源*提供內容並決定最佳匹配項。

- IntelliSense*演示者*負責顯示內容。

  在大多數情況下,我們建議您至少提供源和控制器。 如果要自定義顯示,還可以提供演示者。

### <a name="implement-an-intellisense-source"></a>實現感知來源
 要自訂源,必須實現以下源介面的一個或多個:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>已棄用,<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>以贊成 。

 此外,您必須實現同一類型的提供者:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>已棄用,<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>以贊成 。

 您必須將提供者與以下屬性一起匯出:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:源的名稱。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:源應用於的內容類型(例如,"文本"或"代碼")。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>:源應顯示的順序(相對於其他源)。

- 下面的範例顯示完成源提供程式上的匯出屬性。

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 有關實現 IntelliSense 源的詳細資訊,請參閱以下演練:

- [演練:顯示快速資訊工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [演練:顯示簽名說明](../extensibility/walkthrough-displaying-signature-help.md)

- [逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>實作 IntelliSense 控制器
 要自定義控制器,必須實現<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>介面。 此外,必須實現控制器提供者以及以下屬性:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>:控制器的名稱。

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:控制器應用的內容類型(例如,"文本"或"代碼")。

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>:控制器的顯示順序(相對於其他控制器)。

  下面的範例顯示完成控制器提供程式上的匯出屬性。

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 有關使用 IntelliSense 控制器的詳細資訊,請參閱以下演練:

- [演練:顯示快速資訊工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
