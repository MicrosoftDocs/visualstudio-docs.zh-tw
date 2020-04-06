---
title: 編輯器匯入 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712005"
---
# <a name="editor-imports"></a>編輯器匯入
您可以導入許多編輯器服務、工廠和代理,這些服務、工廠和代理為您的擴展提供對核心編輯器的不同類型的訪問許可權。 例如,可以匯入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>以您提供給定內容類型的<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>。 (此導航器允許您在文字緩衝區上執行不同類型的搜索。

 要使用編輯器導入,可以將其導入為匯出託管擴展框架元件部分的類的欄位或屬性。

> [!NOTE]
> 有關託管擴充性框架的詳細資訊,請參閱[託管擴展性框架 (MEF)。](/dotnet/framework/mef/index)

## <a name="import-syntax"></a>匯入語法
 下面的範例展示如何導入編輯器選項工廠服務。

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 如果要將服務導入為欄位而不是屬性,則應`null`在聲明中將其設置為,以避免編譯器警告不要分配給變數:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 有關使用導入的更多範例,請參閱以下演練:

- [演練:建立邊距字形](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [演練:自訂文字檢視](../extensibility/walkthrough-customizing-the-text-view.md)

- [演練:突顯文字](../extensibility/walkthrough-highlighting-text.md)

- [演練:顯示快速資訊工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [演練:顯示簽名說明](../extensibility/walkthrough-displaying-signature-help.md)

- [逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)

- [演練:顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>匯入服務提供者
 您還可以以相同的方式匯入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>(在程式集 Microsoft.VisualStudio.Shell.Immutable.10.0) 存取 Visual Studio 服務:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 關於詳細資訊[,請參閱演練:從編輯器延伸存取 DTE 物件](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)。

## <a name="services"></a>服務
 編輯器服務通常是單個實體,提供服務並在多個元件之間共用。

|匯入|提供|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|文件副檔名<xref:Microsoft.VisualStudio.Utilities.IContentType>和 物件之間的關係。|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> 物件的集合。|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>物件。|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|許多編輯器配接器物件:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|給定<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>文字檢視的物件。|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>。|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>。|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|一<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>種差異。|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|一<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>種差異。|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|或<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer><xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>。|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|一<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>組物件。 <xref:Microsoft.VisualStudio.Text.ITextBuffer>|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|的<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.ITextBuffer> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|的<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|的<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|的<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|維護<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>物件的集合。|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|文字<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>緩衝區的 。|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|文字<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>檢視的 。|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|指定<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>範圍的欄位的 。|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|文字<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>檢視的 。|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|的<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|通過<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>對象獲取自動縮進。|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|管理<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>的<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>。|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|從一組快照範圍生成 RTF 格式的文本。|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|的<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|用於<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>設定檢視中的文字行的格式。|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>的物件<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|搜索文本快照。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>for by 。|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|文字<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>檢視的 。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|一組標準的字形。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|的<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|跟蹤鍵盤處理。|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|標準<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>物件。|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|維護文本緩衝區和<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>對象之間的關係。|

## <a name="other-imports"></a>其他進口
 提供程式工廠和代理通常是多個元件中可以有多個實例的實體。

|匯入|提供|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>給定緩衝區的類型<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>。|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|文字標記標記器(類型一<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601><xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>個 )。|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|給定<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider><xref:Microsoft.VisualStudio.Text.Editor.ITextView>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>。|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>。|

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
