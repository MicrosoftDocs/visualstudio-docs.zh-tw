---
title: 演練:突出顯示文本 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697395"
---
# <a name="walkthrough-highlight-text"></a>演練:突顯文字
您可以透過建立託管擴展框架 (MEF) 元件部件向編輯器添加不同的視覺效果。 這個演練展示如何突出顯示文本檔中當前單詞的每個匹配項。 如果一個單詞在文本檔中發生不止一次,並且將 caret 定位在一個匹配項中,則每個匹配項都會突出顯示。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`HighlightWordTest`。

2. 加入專案加入編輯器分類器項範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="define-a-textmarkertag"></a>定義文字標記
 突出顯示文本的第一步是子類<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>並定義其外觀。

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>定義文字標記與標記格式定義

1. 添加類檔並將其命名為 **「高光WordTag」。。**

2. 加入下列參考：

    1. 微軟.VisualStudio.核心實用程式

    2. 微軟.VisualStudio.文本.資料

    3. 微軟.VisualStudio.文本.邏輯

    4. 微軟.VisualStudio.文字.UI

    5. 微軟.VisualStudio.文本.UI.Wpf

    6. System.ComponentModel.Composition

    7. 簡報簡報

    8. 範例.框架

3. 匯入以下命名空間。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. 創建繼承<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>並命名它的`HighlightWordTag`類。

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. 建立從<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>繼承的第二個類別並命名`HighlightWordFormatDefinition`它 。 為了對標記使用此格式定義,必須使用以下屬性匯出它:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>標記用它來參考此格式

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>:這將導致格式顯示在 UI 中

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. 在高光字格式定義的建構函數中,定義其顯示名稱和外觀。 "背景"屬性定義填充顏色,而"前景"屬性定義邊框顏色。

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. 在高光WordTag的建構函數中,以您創建的格式定義的名稱傳遞。

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>實施 ITagger
 下一步是實現介面<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>。 此介面為給定的文本緩衝區分配提供文本突出顯示和其他視覺效果的標記。

### <a name="to-implement-a-tagger"></a>實作標記

1. 建立實用型<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>`HighlightWordTag`態的類別,並`HighlightWordTagger`命名它 。

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. 將以下私有欄位和屬性加入:

    - 對應目前<xref:Microsoft.VisualStudio.Text.Editor.ITextView>文字檢視的 。

    - 對應於<xref:Microsoft.VisualStudio.Text.ITextBuffer>文本檢視的基礎的文本緩衝區。

    - 尋找<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>文字的 。

    - 具有<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>在文本範圍內導航的方法。

    - 包含<xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>要突出顯示的單詞集。

    - 對應目前<xref:Microsoft.VisualStudio.Text.SnapshotSpan>單字的 。

    - 對應於<xref:Microsoft.VisualStudio.Text.SnapshotPoint>caret 的當前位置。

    - 鎖定物件。

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. 添加一個建構函數,用於初始化前面列出的屬性,並<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>添加<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>和事件處理程式。

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. 事件處理常式都呼叫`UpdateAtCaretPosition`方法 。

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. 還必須添加更新方法調用`TagsChanged`的事件。

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. 該方法`UpdateAtCaretPosition()`查找文本緩衝區中與游標定位的單詞相同的每個單詞,並構造對應於該單詞<xref:Microsoft.VisualStudio.Text.SnapshotSpan>出現的物件清單。 然後呼叫`SynchronousUpdate`,引發`TagsChanged`事件 。

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. `SynchronousUpdate`對`WordSpans`與`CurrentWord`屬性執行同步更新,並引發`TagsChanged`事件 。

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. 您必須實作該<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>方法 。 此方法獲取<xref:Microsoft.VisualStudio.Text.SnapshotSpan>物件的集合,並返回標記範圍的枚舉。

     在 C# 中,將此方法實現為屈服反覆運算器,該反覆運算器支援標記的延遲計算(即僅在存取單個項時評估集)。 在「視覺基本」中,將標記添加到清單中並返回清單。

     在這裡,該方法返回具有<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>「藍色<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>」 的物件,該物件提供藍色背景。

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>建立標記提供者
 要建立標記器,必須實現<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>。 此類是 MEF 元件部分,因此必須設置正確的屬性,以便識別此擴展。

> [!NOTE]
> 有關 MEF 的詳細資訊,請參閱[託管擴展性框架 (MEF)。](/dotnet/framework/mef/index)

### <a name="to-create-a-tagger-provider"></a>建立標記提供者

1. 建立名為的`HighlightWordTaggerProvider`類別<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, 實現 ,並<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>匯出它與<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>的<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>文字與 a

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. 您必須導入兩個編輯器服務,和<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService><xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>,以實例化標記。

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. 實現方法<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>以返回`HighlightWordTagger`的 實例。

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>組建及測試代碼
 要測試此代碼,請構建高光WordTest解決方案並在實驗實例中運行它。

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>建置和測試高光字測試解決方案

1. 建置方案。

2. 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

3. 創建文本檔並鍵入一些重複單詞的文本,例如"你好你好"。

4. 將游標放置在"hello"的一個事件中。 每個事件都應以藍色突出顯示。

## <a name="see-also"></a>另請參閱
- [演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
