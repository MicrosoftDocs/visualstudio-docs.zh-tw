---
title: 逐步解說：Displaying Light Bulb Suggestions |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2a5c938d5a79cbdb69eb256d1e625e0e35c375
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312515"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>逐步解說：顯示燈泡建議
燈泡是 Visual Studio 編輯器中，展開以顯示一組動作，例如，內建的程式碼分析器或重構程式碼所識別的問題的修正程式的圖示。

 在 Visual C# 和 Visual Basic 編輯器中，您也可以撰寫和封裝您自己的程式碼分析器會自動顯示燈泡動作，以使用.NET 編譯器平台 ("Roslyn")。 如需詳細資訊，請參閱:

- [如何：寫入C#診斷和程式碼修正](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [如何：撰寫 Visual Basic 診斷和程式碼修正](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  其他語言，例如C++也提供一些快速動作，例如，若要建立該函式的虛設常式實作建議的燈泡。

  以下是燈泡的樣貌。 在 Visual Basic 或 Visual C# 專案中，紅色波浪線會出現在變數名稱無效時。 如果您將滑鼠移無效的識別項，則會在資料指標附近出現燈泡。

  ![燈泡](../extensibility/media/lightbulb.png "燈泡")

  如果您按一下燈泡向下箭號，則一組建議的動作會出現，以及所選動作的預覽。 在此情況下，它會顯示如果您執行此動作，對您的程式碼所做的變更。

  ![燈泡預覽](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  您可以使用燈泡，提供您自己的建議的動作。 比方說，您可以提供要移動開啟至新的一行的大括號，或將它們移至前一行結尾的動作。 下列逐步解說將示範如何建立燈泡出現在目前的字組，並有兩個建議的動作：**轉換為大寫**並**轉換為小寫**。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從下載中心取得。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立 Managed Extensibility Framework (MEF) 專案

1. 建立 C# VSIX 專案。 (在**新的專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名為 `LightBulbTest`。

2. 新增**編輯器分類器**項目範本加入專案。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

4. 新增下列參考加入專案，並將**複製到本機**到`False`:

     *Microsoft.VisualStudio.Language.Intellisense*

5. 加入新的類別檔案並將它命名**LightBulbTest**。

6. 新增下列 using 陳述式：

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

## <a name="implement-the-light-bulb-source-provider"></a>實作燈泡來源提供者

1. 在  *LightBulbTest.cs*類別檔案中，刪除 LightBulbTest 類別。 新增名為類別**TestSuggestedActionsSourceProvider**實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>。 匯出名稱為**測試建議的動作**和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text"。

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. 內部來源提供者類別中，匯入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>並將它新增為屬性。

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>方法來傳回<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>物件。 來源會在下一節中討論。

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

## <a name="implement-the-isuggestedactionsource"></a>實作 ISuggestedActionSource
 建議的動作來源負責收集一組建議的動作，然後將它們加入正確的內容中。 在此情況下，內容是目前的字，而且是建議的動作**UpperCaseSuggestedAction**並**LowerCaseSuggestedAction**下, 一節已討論過。

1. 加入類別**TestSuggestedActionsSource**實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>。

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. 加入私用、 唯讀欄位的建議的動作的來源提供者、 文字緩衝區，而且 [文字] 檢視。

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. 新增設定私用欄位的建構函式。

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. 加入私用的方法會傳回目前正在進行的資料指標的文字。 下列方法會查看目前的游標位置，並要求的文字範圍的文字結構導覽器。 如果游標位於上一個字，請<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>在 out 參數中傳回，否則`out`參數是`null`且方法會傳回`false`。

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

5. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 方法。 編輯器會呼叫這個方法，以了解是否要顯示燈泡。 此呼叫通常，比方說，只要將游標從一行移到另一個，或當滑鼠停留在錯誤波浪線。 這是為了讓其他的 UI 作業執行，而這個方法使用非同步的。 在大部分情況下，這個方法只需要執行某些剖析和分析目前的行，以便處理可能需要一些時間。

     在此實作中，它以非同步方式取得<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>並判斷是否有意義的如所示，是否有一些非空白字元的文字範圍。

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

6. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>方法，以傳回的陣列<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>物件都包含不同<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>物件。 展開燈泡時，會呼叫這個方法。

    > [!WARNING]
    > 您應該確定的實作`HasSuggestedActionsAsync()`並`GetSuggestedActions()`是一致的; 也就是說，如果`HasSuggestedActionsAsync()`會傳回`true`，然後`GetSuggestedActions()`應該有一些動作，才能顯示。 在許多情況下，`HasSuggestedActionsAsync()`之前呼叫`GetSuggestedActions()`，但不一定如此。 例如，如果使用者叫用燈泡動作，藉由按下 (**CTRL +** 。) 只`GetSuggestedActions()`呼叫。

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

7. 定義`SuggestedActionsChanged`事件。

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. 若要完成實作，將新增實作`Dispose()`和`TryGetTelemetryId()`方法。 您不想要的遙測，因此僅傳回`false`並將 GUID 設定為`Empty`。

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

## <a name="implement-light-bulb-actions"></a>實作燈泡動作

1. 在專案中，新增指向*Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*並設定**複製到本機**到`False`。

2. 建立兩個類別：第一個命名為 `UpperCaseSuggestedAction` ，第二個則命名為 `LowerCaseSuggestedAction`。 這兩個類別都會實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>。

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     這兩個類別相同，差別在於其中一個會呼叫 <xref:System.String.ToUpper%2A>，另一個會呼叫 <xref:System.String.ToLower%2A>。 下列步驟僅涵蓋大寫動作類別，但您必須實作這兩個類別。 使用實作大寫動作的步驟，作為實作小寫動作的模式。

3. 新增下列 using 陳述式，這些類別：

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
    private string m_upper;
    private string m_display;
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

6. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>方法，因此它會顯示動作預覽。

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>方法，讓它傳回空<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>列舉型別。

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
    public string DisplayText
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
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > 燈泡動作**Invoke**方法不應該顯示 UI。 如果您的動作會啟動新的使用者介面 （例如預覽 或 選取項目 對話方塊），不會顯示直接從 UI **Invoke**方法，但改為排程後傳回從顯示您的 UI **Invoke**.

10. 若要完成實作，新增`Dispose()`和`TryGetTelemetryId()`方法。

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

11. 別忘了進行相同的動作`LowerCaseSuggestedAction`變更的顯示文字 「 轉換 '{0}' 為小寫"和呼叫<xref:System.String.ToUpper%2A>至<xref:System.String.ToLower%2A>。

## <a name="build-and-test-the-code"></a>建置和測試程式碼
 若要測試此程式碼，建置 LightBulbTest 方案，並在實驗執行個體中執行它。

1. 建置方案。

2. 當您執行此專案的偵錯工具時，會啟動 Visual Studio 的第二個執行個體。

3. 建立文字檔，並輸入一些文字。 您應該會看到文字的左邊的燈泡。

     ![測試燈泡](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. 指向燈泡。 您應該會看到向下箭號。

5. 當您按一下燈泡時，兩個建議的動作應該會顯示，以及所選動作的預覽。

     ![測試燈泡，已展開](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. 如果您按一下第一個動作，將目前的文字中的所有文字應該都轉換成大寫。 如果您按一下第二個動作時，所有的文字應該轉換成小寫。
