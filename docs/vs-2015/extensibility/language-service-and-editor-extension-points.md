---
title: 語言服務及編輯器擴充點 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87701b2404ebb929d2a21fed6ddc22b075c1f186
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243265"
---
# <a name="language-service-and-editor-extension-points"></a>語言服務及編輯器擴充點
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

編輯器會提供您可以擴充為 Managed Extensibility Framework (MEF) 元件組件，其中包括大部分的語言服務功能的擴充點。 這些是主要擴充點類別：  
  
-   內容類型  
  
-   分類類型及分類格式  
  
-   邊界和捲軸  
  
-   Tags  
  
-   裝飾  
  
-   滑鼠處理器  
  
-   拖放處理常式  
  
-   選項  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>擴充的內容類型  
 內容類型是一種文字編輯器，例如處理、 「 文字 」、 「 程式碼 」 或"CSharp"的定義。 您可以定義新的內容類型所宣告之型別的變數<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>並提供新的內容類型的唯一名稱。 若要註冊的內容類型的編輯器，請將它匯出以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 是內容類型的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> 是這個內容類型衍生的內容類型名稱。 內容類型可能繼承自多個其他內容類型。  
  
 因為<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>類別已密封，您可以將它匯出不含型別參數。  
  
 下列範例會顯示匯出屬性上的內容類型定義。  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 內容類型可以根據零或多個預先存在的內容類型。 以下是內建的類型：  
  
-   任何： 基本的內容類型。 所有其他內容類型的父代。  
  
-   文字： 非投影內容的基本類型。 繼承自 「 任何 」。  
  
-   純文字： 用於非程式碼的文字。 繼承自 「 文字 」。  
  
-   程式碼： 針對所有類型的程式碼。 繼承自 「 文字 」。  
  
-   惰性： 排除任何一種處理文字。 此內容類型的文字會永遠不會有套用任何擴充功能。  
  
-   投影： 的投影緩衝區的內容。 繼承自 「 任何 」。  
  
-   Intellisense： 針對 IntelliSense 的內容。 繼承自 「 文字 」。  
  
-   Sighelp： 簽章說明。 繼承自 [intellisense]。  
  
-   Sighelp 文件： 簽章說明文件。 繼承自 [intellisense]。  
  
 以下是一些 Visual Studio 所定義的內容類型和裝載在 Visual Studio 中的語言：  
  
-   基本  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   裡  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 若要探索可用的內容類型清單，匯入<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>，可維護的內容型別集合編輯器。 下列程式碼中，會匯入這項服務做為屬性。  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 若要將內容類型與副檔名產生關聯，請使用<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>。  
  
> [!NOTE]
>  在 Visual Studio 中，檔案名稱副檔名會註冊使用<xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>的語言服務套件。 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF 的內容類型關聯這種方式中已註冊的副檔名。  
  
 若要匯出內容的型別定義的檔案名稱的副檔名，您必須包含下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>： 指定檔案名稱的副檔名。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 指定的內容類型。  
  
 因為<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>類別已密封，您可以將它匯出不含型別參數。  
  
 下列範例會顯示匯出屬性至內容類型定義的檔案名稱副檔名。  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>管理副檔名的檔案與內容類型之間的關聯。  
  
## <a name="extending-classification-types-and-classification-formats"></a>擴充分類類型與分類格式  
 您可以使用分類類型來定義您想要提供不同的處理 （例如，藍色的"關鍵字 「 文字和 「 註解 」 文字著色綠色） 文字的類型。 定義新的分類類型所宣告的型別變數<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>並提供唯一的名稱。  
  
 若要向編輯器的分類類型，請將它匯出以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 分類類型的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>： 這個分類的型別所繼承的分類類型的名稱。 所有的分類類型繼承自"text"，而且分類類型可以繼承自多個其他分類類型。  
  
 因為<xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>類別已密封，您可以將它匯出不含型別參數。  
  
 下列範例會顯示匯出屬性分類的類型定義。  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>提供存取標準分類。 內建的分類類型包括：  
  
-   文字  
  
-   「 自然語言 」 （衍生自"text"）  
  
-   （衍生自 「 文字 」） 「 正式語言 」  
  
-   「 字串 」 （衍生自 「 常值 」）  
  
-   "character"（衍生自 「 常值 」）  
  
-   「 數值 」 （衍生自 「 常值 」）  
  
 一組不同的錯誤類型繼承自<xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>。 其中包括下列的錯誤類型：  
  
-   「 語法錯誤 」  
  
-   「 編譯器錯誤 」  
  
-   「 其他錯誤 」  
  
-   「 警告 」  
  
 若要探索可用的分類類型的清單，匯入<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>，可維護之編輯器的分類類型集合。 下列程式碼中，會匯入這項服務做為屬性。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 您可以定義分類格式定義新的分類類型。 衍生的類別<xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition>並將它匯出的類型<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>，以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 格式的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>： 格式的顯示名稱。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>： 指定是否在顯示的格式**字型和色彩**頁**選項** 對話方塊。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 格式的優先順序。 有效值為從<xref:Microsoft.VisualStudio.Text.Classification.Priority>。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>： 此格式對應類型分類的名稱。  
  
 下列範例會顯示匯出屬性分類格式定義。  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 若要探索可用的格式清單，匯入<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>，可維護的編輯器格式的集合。 下列程式碼中，會匯入這項服務做為屬性。  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>擴充的邊界和捲軸  
 邊界和捲軸是除了本身的 [文字] 檢視編輯器的主要檢視項目。 您可以提供任意數目的邊界，除了標準的邊界，以顯示 [文字] 檢視。  
  
 實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin>介面來定義邊界。 您也必須實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>介面來建立邊界。  
  
 若要向 「 編輯器邊界提供者，您必須將匯出的提供者，以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 邊界的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 在此邊界會出現，相對於其他邊界的順序。  
  
     以下是內建的邊界：  
  
    -   「 Wpf 的水平捲軸 」  
  
    -   「 Wpf 的垂直捲軸 」  
  
    -   「 Wpf 的列數字邊界 」  
  
     有的順序屬性的水平邊界`After="Wpf Horizontal Scrollbar"`下方的內建的邊界和水平的邊界，有的順序顯示`Before ="Wpf Horizontal Scrollbar"`的內建的邊界上方顯示。 以滑鼠右鍵的順序屬性的垂直邊界`After="Wpf Vertical Scrollbar"`右邊的捲軸會顯示。 保留的順序屬性的垂直邊界`After="Wpf Line Number Margin"`（如果可見） 的列數字邊界的左邊會出現。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>： 邊界 （左、 右、 top 或 bottom） 的類型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 您邊界為有效的內容 （例如，"text"或"code"） 類型。  
  
 下列範例會顯示匯出屬性右邊的列數字邊界的邊界的邊界提供者上。  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>延伸標記  
 標籤是文字的一種關聯不同種類中的資料。 在許多情況下，相關聯的資料會顯示為視覺效果，但並非所有標籤都有視覺化的呈現方式。 您可以藉由實作定義您自己的標記類型<xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 您也必須實作<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>提供一組指定的文字範圍的標記和<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>提供標記者。 您必須將匯出的標記者提供者，以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 您的標籤是有效的內容 （例如，"text"或"code"） 類型。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>： 標記的類型。  
  
 下列範例會顯示標記者提供者匯出屬性。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TagType(typeof(TestTag))]  
internal class TestTaggerProvider : ITaggerProvider  
```  
  
 下列類型是標記的內建項目：  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>： 與相關聯<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>： 錯誤類型相關聯。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>： 與透過裝飾相關聯。  
  
    > [!NOTE]
    >  如需範例<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>，請參閱 HighlightWordTag 定義[逐步解說： 反白顯示的文字](../extensibility/walkthrough-highlighting-text.md)。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>： 可以展開或摺疊大綱區域相關聯。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>： 文字檢視中定義的裝飾佔用的空間。 如需有關空間交涉裝飾的詳細資訊，請參閱下一節。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>： 提供自動的間距和裝飾的調整大小。  
  
 若要尋找和使用緩衝區和檢視表的標籤，匯入<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>或<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>，可讓您<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>的要求的型別。 下列程式碼中，會匯入這項服務做為屬性。  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>標記和 MarkerFormatDefinitions  
 您可以擴充<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>類別，定義標籤的外觀。 您必須匯出您的類別 (為<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) 具有下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 用來參考此格式的名稱  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>： 這會導致要出現在 UI 中的格式  
  
 在建構函式，您會定義顯示名稱和標記的外觀。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 定義填滿色彩，以及<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A>定義的框線色彩。 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>格式定義的可當地語系化的名稱。  
  
 格式定義的範例如下：  
  
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
  
 若要將此格式定義套用至標記中，參考您設定的名稱屬性中的類別 （而不是顯示名稱） 的名稱。  
  
> [!NOTE]
>  如需<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>，請參閱中的 HighlightWordFormatDefinition 類別[逐步解說： 反白顯示的文字](../extensibility/walkthrough-highlighting-text.md)。  
  
## <a name="extending-adornments"></a>擴充裝飾  
 裝飾定義視覺效果，可以新增在文字檢視中顯示的文字或文字檢視本身。 您可以為任何類型的定義您自己的裝飾<xref:System.Windows.UIElement>。  
  
 在裝飾類別中，您必須宣告<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>。 若要註冊您的 adornment 層，請將它匯出以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 裝飾的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 相對於其他 adornment 層級裝飾的順序。 此類別<xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers>定義四個預設層級： 選取範圍、 大綱、 插入號和文字。  
  
 下列範例會顯示匯出屬性裝飾層定義。  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 您必須建立第二個類別可實作<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>，並處理其<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>事件具現化的裝飾。 您必須匯出此類別，以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 裝飾為有效的內容 （例如，"text"或"code"） 類型。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>： 此裝飾為有效的文字檢視的類型。 此類別<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>具有一組預先定義的文字檢視角色。 比方說，<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>主要用於文字檢視的檔案。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 用於文字檢視，使用者可以編輯，或使用滑鼠和鍵盤瀏覽。 範例<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>檢視是編輯器文字檢視和**輸出**視窗。  
  
 下列範例會顯示匯出屬性裝飾的提供者。  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 空間交涉的裝飾會佔用空間，做為文字相同層級的其中一個。 若要建立這種裝飾，您必須定義標記類別繼承自<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>，其定義 adornment 所佔用的空間量。  
  
 如同所有裝飾，您必須匯出裝飾層定義。  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 具現化空間交涉的裝飾，您必須建立可實作類別<xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>，除了可實作類別<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>（就像其他種類的裝飾）。  
  
 若要註冊的標記者提供者，您必須將它匯出以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 您 adornment 是有效的內容 （例如，"text"或"code"） 類型。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: 一種文字檢視，這個標記或 adornment 是否有效。 此類別<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>具有一組預先定義的文字檢視角色。 比方說，<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>主要用於文字檢視的檔案。 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 用於文字檢視，使用者可以編輯，或使用滑鼠和鍵盤瀏覽。 範例<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>檢視是編輯器文字檢視和**輸出**視窗。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>： 的標籤或您已定義的裝飾。 您必須新增第二個<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>針對<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>。  
  
 下列範例會顯示匯出屬性上的空間交涉裝飾標記的標記者提供者。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>延伸的滑鼠處理器  
 您可以將滑鼠輸入的特殊處理。 建立繼承自一個類別<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>並覆寫的輸入您想要處理的滑鼠事件。 您也必須實作<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>中的第二個類別並將它連同匯出<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>，指定您的滑鼠處理常式是有效的內容 （例如，"text"或"code"） 類型。  
  
 下列範例會顯示匯出屬性上的滑鼠處理器提供者。  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>擴充拖放處理常式  
 您可以藉由建立類別來實作自訂行為的特定種類的文字的拖放處理常式<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler>和第二個類別可實作<xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider>建立拖放處理常式。 您必須匯出拖放處理常式，以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>： 這個拖放處理常式是有效的文字格式。 依優先順序從最高到最低，會處理下列格式：  
  
    1.  任何自訂的格式  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  Riff  
  
    6.  差異  
  
    7.  地區設定  
  
    8.  調色盤  
  
    9. PenData  
  
    10. 可序列化  
  
    11. SymbolicLink  
  
    12. Xaml  
  
    13. XamlPackage  
  
    14. Tiff  
  
    15. Bitmap  
  
    16. Dib  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. HTML 格式  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. 文字  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 拖放處理常式的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 的順序拖放處理常式之前或之後的預設拖放處理常式。 Visual Studio 的預設拖放處理常式是名為"DefaultFileDropHandler 」。  
  
 下列範例會顯示匯出屬性拖放處理常式提供者。  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>擴充編輯器選項  
 您可以定義為只在特定範圍內，比方說，在文字檢視中有效的選項。 編輯器會提供這組預先定義的選項： 編輯器選項，檢視選項，以及 Windows Presentation Foundation (WPF) 檢視選項。 這些選項可在<xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>， <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>，和<xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>。  
  
 若要加入新的選項，請從這些選項定義類別的其中一個衍生類別：  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 下列範例示範如何匯出選項定義具有布林值。  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>擴充 IntelliSense  
 IntelliSense 是一組提供結構化文字的相關資訊的功能的一般詞彙和它的陳述式完成。 這些功能包括陳述式完成、 簽章說明、 快速諮詢和燈泡。 陳述式完成可幫助使用者正確地輸入語言關鍵字或成員名稱。 簽章說明會顯示與使用者只輸入方法的簽章的簽章。 快速諮詢會在滑鼠停留在其上時顯示的型別或成員名稱的完整簽章。 燈泡會提供一個相符項目已重新命名之後，重新命名所有出現的變數中某些內容，例如，特定識別碼的其他的動作。  
  
 IntelliSense 功能的設計是在所有情況下非常類似：  
  
-   IntelliSense *broker*負責整體程序。  
  
-   IntelliSense*工作階段*表示之間的展示者的順序或取消選取範圍的觸發事件的順序。 工作階段通常會觸發某些使用者筆勢。  
  
-   IntelliSense*控制器*負責決定工作階段應該在何時開始和結束。 此外，它也會決定當的資訊應該認可和工作階段應該已取消。  
  
-   IntelliSense*來源*提供內容，並決定最符合項目。  
  
-   IntelliSense*主持人*負責顯示內容。  
  
 在大部分情況下，我們建議您提供最少的來源和控制站。 如果您想要自訂顯示，您也可以提供一個展示者。  
  
### <a name="implementing-an-intellisense-source"></a>實作 IntelliSense 的來源  
 若要自訂來源，您必須實作其中一個 （或以上） 的下列來源介面：  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 已被取代的益處<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>。  
  
 此外，您必須實作相同類型的提供者：  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 已被取代的益處<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>。  
  
 您必須將匯出的提供者，以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>： 來源的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>： 要套用的來源內容 （例如，"text"或"code"） 的類型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>： 來源 （相對於其他來源） 應該出現的順序。  
  
-   下列範例會顯示匯出屬性，完成來源提供者。  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 如需有關如何實作 IntelliSense 的來源的詳細資訊，請參閱下列逐步解說：  
  
 [逐步解說︰顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [逐步解說︰顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>實作 IntelliSense 控制器  
 若要自訂的控制站，您必須實作<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>介面。 此外，您必須實作的控制站提供者，以及下列屬性：  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 控制站的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 控制站會套用內容 （例如，"text"或"code"） 的類型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 控制站 （相對於其他控制站） 應該出現的順序。  
  
 下列範例會顯示匯出屬性完成控制站提供者。  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 如需使用 IntelliSense 控制器的詳細資訊，請參閱下列逐步解說：  
  
 [逐步解說︰顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

