---
title: 逐步解說：反白顯示文字 |Microsoft Docs
description: 瞭解如何在此逐步解說中將視覺效果新增至編輯器，以反白顯示文字檔中每個出現的單字。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a500d63eb497ce6d2b23860cd3793cbc2632b819
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078457"
---
# <a name="walkthrough-highlight-text"></a>逐步解說：反白顯示文字
您可以藉由建立 Managed Extensibility Framework (MEF) 元件部分，將不同的視覺效果加入編輯器中。 本逐步解說示範如何在文字檔中醒目提示目前單字的每個出現專案。 如果單字在文字檔中出現一次以上，而且您將插入點放在一次，則會反白顯示每個出現的專案。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `HighlightWordTest` 。

2. 將編輯器分類專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

## <a name="define-a-textmarkertag"></a>定義 TextMarkerTag
 反白顯示文字的第一個步驟是子類別 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ，並定義其外觀。

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>定義 TextMarkerTag 和 MarkerFormatDefinition

1. 新增類別檔案，並將它命名為 **HighlightWordTag**。

2. 加入下列參考：

    1. VisualStudio. CoreUtility

    2. VisualStudio 資料

    3. VisualStudio。

    4. VisualStudio。

    5. VisualStudio （Wpf）

    6. System.ComponentModel.Composition

    7. Presentation Core

    8. Presentation. 架構

3. 匯入下列命名空間。

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

4. 建立繼承自的類別 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ，並為其命名 `HighlightWordTag` 。

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. 建立繼承自的第二個類別 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> ，並將它命名為 `HighlightWordFormatDefinition` 。 若要將此格式定義用於您的標記，您必須使用下列屬性匯出它：

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>：標記使用此格式參考此格式

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>：這會使格式顯示在 UI 中

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. 在 HighlightWordFormatDefinition 的函式中，定義其顯示名稱和外觀。 背景屬性會定義填滿色彩，而前景屬性則會定義框線色彩。

    ```csharp
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. 在 HighlightWordTag 的函式中，傳遞您所建立之格式定義的名稱。

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>執行 ITagger
 下一步是執行 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 介面。 此介面會指派給指定的文字緩衝區、提供文字醒目提示和其他視覺效果的標記。

### <a name="to-implement-a-tagger"></a>若要執行標記

1. 建立實作為 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 型別的類別 `HighlightWordTag` ，並將它命名為 `HighlightWordTagger` 。

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. 將下列私用欄位和屬性新增至類別：

    - <xref:Microsoft.VisualStudio.Text.Editor.ITextView>，對應至目前的文字視圖。

    - <xref:Microsoft.VisualStudio.Text.ITextBuffer>，對應至文字視圖的基礎文字緩衝區。

    - <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>，用來尋找文字。

    - <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>，具有在文字範圍內流覽的方法。

    - <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>，其中包含要醒目提示的文字集。

    - <xref:Microsoft.VisualStudio.Text.SnapshotSpan>，對應至目前的單字。

    - <xref:Microsoft.VisualStudio.Text.SnapshotPoint>，對應至插入號的目前位置。

    - 鎖定物件。

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. 加入可初始化稍早所列屬性的函式，並加入 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 和 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 事件處理常式。

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

4. 事件處理常式會呼叫 `UpdateAtCaretPosition` 方法。

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

5. 您也必須加入 `TagsChanged` 由 update 方法呼叫的事件。

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. `UpdateAtCaretPosition()`方法會在文字緩衝區中尋找與游標所在的單字相同的每個單字，並建立 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 對應至文字出現位置的物件清單。 接著會呼叫 `SynchronousUpdate` ，這會引發 `TagsChanged` 事件。

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
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
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
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. 會對 `SynchronousUpdate` 和屬性執行同步更新 `WordSpans` `CurrentWord` ，並引發 `TagsChanged` 事件。

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

8. 您必須執行 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 方法。 這個方法會取得物件的集合 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> ，並傳回標記範圍的列舉。

     在 c # 中，將此方法實作為 yield 反覆運算器，它會啟用延遲評估 (也就是只有在存取個別專案) 標記時，才會評估集合。 在 Visual Basic 中，將標記新增至清單，並傳回清單。

     在這裡，方法 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 會傳回具有 "blue" 的物件 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ，它會提供藍色背景。

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

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
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>建立標記提供者
 若要建立您的標記，您必須執行 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> 。 這個類別是 MEF 元件的一部分，因此您必須設定正確的屬性，才能辨識此延伸模組。

> [!NOTE]
> 如需 MEF 的詳細資訊，請參閱 [Managed Extensibility Framework (mef) ](/dotnet/framework/mef/index)。

### <a name="to-create-a-tagger-provider"></a>若要建立標記提供者

1. 建立一個名為的類別，這個類別會 `HighlightWordTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> 執行，並使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 和 of 的來匯出 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 。

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. 您必須匯入兩個編輯器服務（ <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> 和 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ），以具現化標記。

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. 執行 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 方法，以傳回的實例 `HighlightWordTagger` 。

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 HighlightWordTest 方案，並在實驗實例中執行它。

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>若要建立及測試 HighlightWordTest 方案

1. 建置方案。

2. 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

3. 建立文字檔，並輸入文字，其中會重複文字，例如 "hello hello hello"。

4. 將游標放在其中一個出現的 "hello" 中。 每次出現時，都應該以藍色反白顯示。

## <a name="see-also"></a>另請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
