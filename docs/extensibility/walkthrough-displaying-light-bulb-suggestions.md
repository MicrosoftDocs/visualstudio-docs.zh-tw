---
title: 演練:顯示燈泡建議 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697478"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>演練:顯示燈泡建議
燈泡是 Visual Studio 編輯器中的圖示,可展開以顯示一組操作,例如,修復內置代碼分析器或代碼重構辨識的問題。

 Visual C++ 和 Visual Basic 編輯器中,您還可以使用 .NET 編譯器平臺("Roslyn")編寫和打包您自己的代碼分析器,並自動顯示燈泡。 如需詳細資訊，請參閱

- [如何:編寫 C# 診斷與代碼修復](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [如何:編寫視覺化基本診斷和代碼修復](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  其他語言(如C++)也為一些快速操作提供燈泡,例如,建議創建該函數的存根實現。

  燈泡是什麼樣子的。 在可視化基本或視覺 C++ 專案中,紅色波浪形在變數名稱下顯示無效。 如果滑鼠懸停在無效標識符上,游標附近將顯示一個燈泡。

  ![燈泡](../extensibility/media/lightbulb.png "燈泡")

  如果按燈泡按下向下箭頭,將顯示一組建議的操作以及所選操作的預覽。 在這種情況下,它會顯示執行操作時對代碼所做的更改。

  ![燈泡預覽](../extensibility/media/lightbulbpreview.png "燈泡預覽")

  您可以使用燈泡提供您自己的建議操作。 例如,可以提供操作,將左大括弧移動到新行或將它們移動到上一行的末尾。 下面的演練示範如何建立一個出現在目前的單字上的燈泡,並且有兩個建議的操作:**轉換為大寫**,**轉換為小寫**, 199 。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-managed-extensibility-framework-mef-project"></a>建立系統延伸架構 (MEF) 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`LightBulbTest`。

2. 加入專案加入**編輯器分類器**項目範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

4. 新增對項目的以下引用,並將 **「本地複本」**`False`設定為 :

     *Microsoft.VisualStudio.Language.Intellisense*

5. 新增類別檔案,並命名為**燈泡測試**。

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

## <a name="implement-the-light-bulb-source-provider"></a>實現燈泡源提供者

1. 在*LightBulbTest.cs*類檔中,刪除燈泡測試類。 新增名為**Test 建議操作來源提供者**的類別<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>,該提供程式實現 。 使用**測試建議操作**的名稱和"文本"匯<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>出 它。

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. 在源提供程式類中,導入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>並將其添加為屬性。

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. 實現返回<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A><xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>物件的方法。 下一節將討論源。

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

## <a name="implement-the-isuggestedactionsource"></a>執行 I 建議作業來源
 建議的操作源負責收集建議的操作集,並在正確的上下文中添加它們。 在這種情況下,上下文是當前單詞,建議的操作是 **「大寫建議操作」** 和 **「下Case建議操作」 ,** 下一節將對此進行討論。

1. 新增實<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>作的**Test 建議操作來源**。

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. 為建議的操作源提供程式、文本緩衝區和文本檢視添加專用的唯讀欄位。

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. 添加設置私有欄位的構造函數。

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. 添加一個私有方法,用於返回當前位於游標下的單詞。 以下方法查看游標的當前位置,並詢問文本結構導航器單詞的範圍。 如果游標位於單字上,<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>則在 out 參數中傳回 。否則,`out`參數`null`為 ,該`false`方法傳回 。

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

5. 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 方法。 編輯器呼叫此方法以找出是否顯示燈泡。 例如,每當游標從一行移動到另一行,或者當滑鼠懸停在錯誤擺動上時,都會進行此調用。 它是非同步的,以便允許在此方法工作時執行其他 UI 操作。 在大多數情況下,此方法需要對當前行執行一些分析和分析,因此處理可能需要一些時間。

     在此實現中,它異步獲取<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>並確定範圍是否重要,如空格之外是否有文本。

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

6. 實現<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>方法,該方法返回包含不同<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet><xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>物件的物件陣組。 當燈泡展開時,將調用此方法。

    > [!WARNING]
    > 應確保`HasSuggestedActionsAsync()``GetSuggestedActions()`和的實現是一致的;也就是說,如果`HasSuggestedActionsAsync()`返回`true`,`GetSuggestedActions()`則 應該有一些要顯示的操作。 在許多情況下,`HasSuggestedActionsAsync()`在之前調`GetSuggestedActions()`用 ,但情況並非總是如此。 例如,如果使用者僅按 **(CTRL+** )`GetSuggestedActions()`調用燈泡操作。

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

7. 定義事件`SuggestedActionsChanged`。

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. 要完成實現,為`Dispose()``TryGetTelemetryId()`和添加實現。 您不想執行遙測,因此只需傳`false`回 並將 GUID 設定為`Empty`。

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

## <a name="implement-light-bulb-actions"></a>實施燈泡操作

1. 在專案中,新增對*Microsoft.VisualStudio.映像.Interop.14.0.DesignTime.dll 的*引用,並將 **「本地副本」** 設定為`False`。

2. 建立兩個類別：第一個命名為 `UpperCaseSuggestedAction` ，第二個則命名為 `LowerCaseSuggestedAction`。 這兩個類別都會實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>。

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     這兩個類別相同，差別在於其中一個會呼叫 <xref:System.String.ToUpper%2A>，另一個會呼叫 <xref:System.String.ToLower%2A>。 下列步驟僅涵蓋大寫動作類別，但您必須實作這兩個類別。 使用實作大寫動作的步驟，作為實作小寫動作的模式。

3. 新增以下使用指令:

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

6. 實現該方法<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>,以便顯示操作預覽。

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. 實現該方法<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>,以便返回<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>空 枚舉。

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
    > 燈泡操作 **「調用**」方法不應顯示 UI。 如果操作確實帶來了新的 UI(例如預覽或選擇對話方塊),請不要直接從**Invoke**方法中顯示 UI,而是計畫從**Invoke**返回後顯示 UI。

10. 要完成實現,添加和`Dispose()``TryGetTelemetryId()`方法。

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

11. 不要忘記`LowerCaseSuggestedAction`做同樣的事情,將顯示文字更改為"轉換{0}' 到小寫",並<xref:System.String.ToUpper%2A><xref:System.String.ToLower%2A>呼叫 。

## <a name="build-and-test-the-code"></a>組建及測試代碼
 要測試此代碼,請構建燈泡測試解決方案並在實驗實例中運行它。

1. 建置方案。

2. 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

3. 建立文字檔，並輸入一些文字。 您應該看到文字左側的燈泡。

     ![測試燈泡](../extensibility/media/testlightbulb.png "測試LIghtBulb")

4. 指向燈泡。 您應該會看到一個向下箭頭。

5. 單擊燈泡時,應顯示兩個建議的操作以及所選操作的預覽。

     ![測試燈泡，已展開](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulb 擴展")

6. 如果按一個操作,則當前單詞中的所有文本都應轉換為大寫。 如果按一下第二個操作,則所有文本都應轉換為小寫。
