---
title: 編輯器匯入 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b11ef172cdd8fb4b1c72b72b43198ad7ad8f74e5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417349"
---
# <a name="editor-imports"></a>編輯器匯入
您可以匯入幾個的編輯器服務、 處理站和代理程式，為您的擴充功能提供核心編輯器的不同類型的存取。 例如，您可以匯入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>提供您<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>指定的內容類型。 （這個巡覽可讓您執行不同種類的搜尋文字的緩衝區上）。

 若要使用的編輯器匯入，您它匯入為欄位或屬性的匯出 Managed Extensibility Framework 元件組件的類別。

> [!NOTE]
> 如需有關 Managed Extensibility Framework 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。

## <a name="import-syntax"></a>匯入語法
 下列範例顯示如何匯入編輯器選項 factory 服務。

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 如果您想要匯入做為欄位並不是屬性的服務，您就應該將它設定為`null`以避免編譯器發出警告不會指派給變數宣告中：

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 如需使用 匯入的範例，請參閱下列逐步解說：

- [逐步解說：建立邊界字符](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [逐步解說：自訂文字檢視](../extensibility/walkthrough-customizing-the-text-view.md)

- [逐步解說：反白顯示文字](../extensibility/walkthrough-highlighting-text.md)

- [逐步解說：顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [逐步解說：顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)

- [逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)

- [逐步解說：顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>匯入服務提供者
 您也可以匯入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>（Microsoft.VisualStudio.Shell.Immutable.10.0 的組件中找到） 相同的方式，以取得 Visual Studio 服務的存取權：

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 請參閱[逐步解說：從編輯器擴充功能存取 DTE 物件](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)如需詳細資訊。

## <a name="services"></a>服務
 編輯器服務是提供服務和多個元件之間共用的通常單一實體。

|匯入|提供|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|檔案副檔名之間的關聯性和<xref:Microsoft.VisualStudio.Utilities.IContentType>物件。|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 物件的集合。|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> 物件。|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|許多編輯器介面卡物件：<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>給定的文字檢視物件。|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>。|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>的差異。|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>的差異。|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>或<xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>。|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>的一組<xref:Microsoft.VisualStudio.Text.ITextBuffer>物件。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>針對<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>針對<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>針對<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>針對<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|會維護的集合<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>物件。|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>文字緩衝。|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>文字檢視。|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>針對指定的範圍。|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>文字檢視。|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>針對<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|取得自動縮排<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>物件。|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|管理<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>針對<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>。|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|從快照集範圍的一組產生 RTF 格式的文字。|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>針對<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>格式化在檢視中的文字行。|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>物件<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|搜尋文字的快照集。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> For<xref:Microsoft.VisualStudio.Text.ITextBuffer>由<xref:Microsoft.VisualStudio.Utilities.IContentType>。|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>文字檢視。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|一組標準的圖像 （glyph）。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>針對<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|追蹤鍵盤處理。|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|標準<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>物件。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|會維護文字緩衝區之間的關聯性和<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>物件。|

## <a name="other-imports"></a>其他匯入
 提供者處理站和代理程式通常是在多個元件中可以有多個執行個體的實體。

|匯入|提供|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>型別的<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) 指定的緩衝區。|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|文字標記的標記者 (<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>型別的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>)。|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>的指定<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>。|

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
