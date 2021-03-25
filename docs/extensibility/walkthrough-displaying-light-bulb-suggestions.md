---
title: 逐步解說：顯示燈泡建議 |Microsoft Docs
description: 瞭解如何在 Visual Studio 編輯器中建立出現在目前字組上的燈泡，並使用本逐步解說有兩項建議的動作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad000d486b0808ea4ddc3311daa7178c6eda1231
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080316"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>逐步解說：顯示燈泡建議
Light 燈泡是 Visual Studio 編輯器中的圖示，會展開以顯示一組動作，例如修正內建程式碼分析器或程式碼重構所識別的問題。

 在 Visual c # 和 Visual Basic 編輯器中，您也可以使用 .NET Compiler Platform ( "Roslyn" ) 撰寫和封裝您自己的程式碼分析器，並顯示自動顯示燈泡的動作。 如需詳細資訊，請參閱

- [如何：撰寫 c # 診斷和程式碼修正](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)

- [How To：撰寫 Visual Basic 診斷和程式碼修正](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)

  其他語言（例如 c + +）也會提供一些快速動作的燈光燈泡，例如，建立該函式的存根執行的建議。

  燈泡如下所示。 在 Visual Basic 或 Visual c # 專案中，如果變數名稱無效，則會出現紅色波浪線。 如果您將滑鼠指標移到不正確識別碼，游標附近會出現燈泡。

  ![燈泡](../extensibility/media/lightbulb.png "燈泡")

  如果您按一下燈泡的向下箭號，則會出現一組建議的動作，以及所選動作的預覽。 在此情況下，如果您執行此動作，則會顯示對程式碼所做的變更。

  ![燈泡預覽](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  您可以使用 light 燈泡來提供您自己的建議動作。 例如，您可以提供動作將左大括弧移至新行，或將它們移至上一行的結尾。 下列逐步解說示範如何建立顯示在目前單字上的燈泡，並有兩個建議的動作： [ **轉換為大寫** ] 和 [ **轉換為小寫**]。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立 Managed Extensibility Framework (MEF) 專案

1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `LightBulbTest` 。

2. 將 **編輯器分類** 專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

4. 將下列參考加入至專案，並將 [ **複製到本機** ] 設定為 `False` ：

     *Microsoft.VisualStudio.Language.Intellisense*

5. 加入新的類別檔案，並將它命名為 **LightBulbTest**。

6. 加入以下 using 指示詞：

    ```csharp
    using System;
    using System.Linq;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    using Microsoft.VisualStudio.Language.Intellisense;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;
    using System.Threading;

    ```

## <a name="implement-the-light-bulb-source-provider"></a>執行燈泡來源提供者

1. 在 *LightBulbTest .cs* 類別檔案中，刪除 LightBulbTest 類別。 加入一個名為 **TestSuggestedActionsSourceProvider** 的類別，它會執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> 。 將其匯出為 **測試建議的動作** 名稱和 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"。

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. 在來源提供者類別中，匯入， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 並將它加入做為屬性。

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> 方法以傳回 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> 物件。 下一節將討論來源。

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>執行 ISuggestedActionSource
 建議的動作來源負責收集建議的動作集合，並將其新增至正確的內容。 在此情況下，內容就是目前的文字，而建議的動作是 **UpperCaseSuggestedAction** 和 **LowerCaseSuggestedAction**，在下一節中將會討論。

1. 加入執行的類別 **TestSuggestedActionsSource** <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> 。

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. 為建議的動作來源提供者、文字緩衝區和文字視圖新增私用、唯讀欄位。

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. 加入設定私用欄位的函式。

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. 加入私用方法，這個方法會傳回目前在游標下的文字。 下列方法會查看游標的目前位置，並要求文字結構導覽器提供單字的範圍。 如果游標在單字上，則 <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> 會在 out 參數中傳回，否則， `out` 參數為， `null` 而且方法會傳回 `false` 。

    ```csharp
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)
    {
        ITextCaret caret = m_textView.Caret;
        SnapshotPoint point;

        if (caret.Position.BufferPosition > 0)
        {
            point = caret.Position.BufferPosition - 1;
        }
        else
        {
            wordExtent = default(TextExtent);
            return false;
        }

        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);

        wordExtent = navigator.GetExtentOfWord(point);
        return true;
    }
    ```

5. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 方法。 編輯器會呼叫這個方法，以找出是否要顯示燈泡。 這項呼叫通常是在每次游標移至另一行時，或是當滑鼠停留在錯誤波浪線上時進行。 它是非同步，可讓其他 UI 作業在此方法運作時繼續執行。 在大部分的情況下，此方法需要對目前的行執行一些剖析和分析，因此處理可能需要一些時間。

     在此實作為中，它會以非同步方式取得， <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> 並判斷範圍是否重要，如同在中是否有一些文字以外的文字。

    ```csharp
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        return Task.Factory.StartNew(() =>
        {
            TextExtent extent;
            if (TryGetWordUnderCaret(out extent))
            {
                // don't display the action if the extent has whitespace
                return extent.IsSignificant;
              }
            return false;
        });
    }
    ```

6. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> 方法，這個方法 <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> 會傳回包含不同物件的物件陣列 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> 。 展開燈泡時，會呼叫這個方法。

    > [!WARNING]
    > 您應確定和的實 `HasSuggestedActionsAsync()` `GetSuggestedActions()` 作為一致; 也就是說，如果傳回 `HasSuggestedActionsAsync()` `true` ，則 `GetSuggestedActions()` 應該有一些要顯示的動作。 在許多情況下， `HasSuggestedActionsAsync()` 只會在之前呼叫 `GetSuggestedActions()` ，但不一定都是如此。 例如，如果使用者按 (**CTRL +** 叫用燈泡動作， `GetSuggestedActions()` 則只會呼叫 ) 。

    ```csharp
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        TextExtent extent;
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)
        {
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };
        }
        return Enumerable.Empty<SuggestedActionSet>();
    }
    ```

7. 定義 `SuggestedActionsChanged` 事件。

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. 若要完成此程式，請加入 `Dispose()` 和方法的執行 `TryGetTelemetryId()` 。 您不想要進行遙測，因此只要傳回 `false` 並將 GUID 設為 `Empty` 。

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample provider and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

## <a name="implement-light-bulb-actions"></a>執行燈泡動作

1. 在專案中加入 *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* 的參考，並將 [ **複製到本機** ] 設定為 `False` 。

2. 建立兩個類別：第一個命名為 `UpperCaseSuggestedAction` ，第二個則命名為 `LowerCaseSuggestedAction`。 這兩個類別都會實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>。

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     這兩個類別相同，差別在於其中一個會呼叫 <xref:System.String.ToUpper%2A>，另一個會呼叫 <xref:System.String.ToLower%2A>。 下列步驟僅涵蓋大寫動作類別，但您必須實作這兩個類別。 使用實作大寫動作的步驟，作為實作小寫動作的模式。

3. 針對這些類別新增下列 using 指示詞：

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. 宣告一組私用欄位。

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. 加入可設定欄位的建構函式。

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> 方法，讓它顯示動作預覽。

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> 方法，讓它傳回空 <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> 列舉。

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. 依照下列所示來實作屬性。

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
    {
        get { return m_display; }
    }
    public ImageMoniker IconMoniker
    {
       get { return default(ImageMoniker); }
    }
    public string IconAutomationText
    {
        get
        {
            return null;
        }
    }
    public string InputGestureText
    {
        get
        {
            return null;
        }
    }
    public bool HasPreview
    {
        get { return true; }
    }
    ```

9. 將範圍中的文字取代為其大寫對等項目，以實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> 方法。

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > 燈泡 **動作叫** 用方法不應該顯示 UI。 如果您的動作會顯示新的 UI (例如預覽或選取對話方塊) ，請勿直接從叫 **用方法內** 顯示 ui，而是在從 **invoke** 傳回之後，改為顯示您的 ui。

10. 若要完成此執行，請新增 `Dispose()` 和 `TryGetTelemetryId()` 方法。

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample action and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

11. 別忘了將 `LowerCaseSuggestedAction` 顯示文字變更為「將 ' 轉換成 {0} 小寫」以及呼叫 <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A> 。

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 LightBulbTest 方案，並在實驗實例中執行它。

1. 建置方案。

2. 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

3. 建立文字檔，並輸入一些文字。 您應該會在文字左方看到燈泡。

     ![測試燈泡](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. 指向燈泡。 您應該會看到向下箭號。

5. 當您按一下燈泡時，應該會顯示兩個建議的動作，以及所選動作的預覽。

     ![測試燈泡，已展開](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. 如果您按一下第一個動作，則應該將目前單字中的所有文字轉換成大寫。 如果您按一下第二個動作，則應該將所有文字轉換為小寫。
