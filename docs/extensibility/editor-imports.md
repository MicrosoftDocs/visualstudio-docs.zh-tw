---
title: 編輯器匯入 |Microsoft Docs
description: 瞭解如何匯入編輯器服務、factory 和訊息代理程式，以提供您的擴充功能與核心編輯器的不同存取類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898340"
---
# <a name="editor-imports"></a>編輯器匯入
您可以匯入一些編輯器服務、factory 和訊息代理程式，以提供您的擴充功能與核心編輯器的不同存取類型。 例如，您可以匯入， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 以提供 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> 指定之內容類型的。  (此導覽器可讓您在文字緩衝區上執行不同種類的搜尋。 ) 

 若要使用編輯器匯入，請將它匯入為類別的欄位或屬性，以匯出 Managed Extensibility Framework 元件部分。

> [!NOTE]
> 如需 Managed Extensibility Framework 的詳細資訊，請參閱 [Managed Extensibility Framework (MEF) ](/dotnet/framework/mef/index)。

## <a name="import-syntax"></a>匯入語法
 下列範例示範如何匯入編輯器 options factory 服務。

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 如果您想要將服務匯入為欄位，而不是屬性，您應該在宣告中將其設定為， `null` 以避免編譯器警告，而不會指派給變數：

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 如需使用匯入的更多範例，請參閱下列逐步解說：

- [逐步解說：建立邊界字元](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [逐步解說：自訂文字視圖](../extensibility/walkthrough-customizing-the-text-view.md)

- [逐步解說：反白顯示文字](../extensibility/walkthrough-highlighting-text.md)

- [逐步解說：顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [逐步解說：顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)

- [逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)

- [逐步解說：顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>匯入服務提供者
 您也可以 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 使用相同的方式來匯入) VisualStudio 中找到的 (，以取得 Visual Studio 服務的存取權：

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 如需詳細資訊，請參閱 [逐步解說：從編輯器延伸模組存取 DTE 物件](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) 。

## <a name="services"></a>服務
 編輯器服務通常是單一實體，可提供服務並跨多個元件共用。

|匯入|提供|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|副檔名和物件之間的關聯性 <xref:Microsoft.VisualStudio.Utilities.IContentType> 。|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 物件的集合。|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> 物件。|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|許多編輯器介面卡物件：<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>給定文字視圖的物件。|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>。|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>差異的。|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>差異的。|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>或 <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> 。|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>物件集合的 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|的 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.ITextBuffer> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|的 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|的 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|的 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|維護物件的集合 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 。|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>文字緩衝區的。|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>文字視圖的。|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>指定範圍的。|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>文字視圖的。|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|的 <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|取得透過物件的自動縮排 <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> 。|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|管理的 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 。|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>。|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|從一組快照集範圍產生 RTF 格式的文字。|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>的 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>，用於在視圖中格式化文字行。|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|的 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> 物件 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|搜尋文字快照集。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|的 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> 。|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>文字視圖的。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|一組標準的圖像。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|的 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|追蹤鍵盤處理。|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|標準 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 物件。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|維護文字緩衝區和物件之間的關聯性  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> 。|

## <a name="other-imports"></a>其他匯入
 提供者 factory 和訊息代理程式通常是在多個元件中可以有多個實例的實體。

|匯入|提供|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 給定緩衝區之類型) 的。|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>| (類型) 的文字標記標記 <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 。|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>給定的 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>。|

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
