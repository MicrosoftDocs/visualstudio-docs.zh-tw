---
title: 逐步解說： 顯示燈泡建議 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 750e3b0915478b4249ce8db1ac294c1f2a3006f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148697"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>逐步解說： 顯示燈泡建議
燈泡是 Visual Studio 編輯器中使用的圖示會展開以顯示一組動作，例如內建的程式碼分析器或重構程式碼來識別問題的修正。  
  
 在 Visual C# 和 Visual Basic 編輯器中，您也可以使用.NET 編譯器平台 ("Roslyn") 來撰寫和封裝您自己的程式碼分析器會自動顯示燈泡的動作。 如需詳細資訊，請參閱:  
  
-   [如何： 撰寫 C# 診斷和程式碼修正](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [如何： 寫入的診斷 Visual Basic 和程式碼修正](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 C + + 等其他語言也提供一些快速動作，例如，若要建立該函式的虛設常式實作的建議燈泡。  
  
 以下是燈泡的外觀。 在 Visual Basic 或 Visual C# 專案中，紅色波浪線會出現在變數名稱無效時。 當您將滑鼠移無效的識別項時，燈泡顯示游標附近。  
  
 ![燈泡](../extensibility/media/lightbulb.png "LightBulb")  
  
 如果您透過燈泡按一下向下箭號，一組建議的動作會顯示，並預覽選取的動作。 在此情況下，它會顯示如果您執行此動作會對您的程式碼的變更。  
  
 ![燈泡預覽](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 您可以使用燈泡來提供建議的動作。 例如，您可以提供動作移動左大括號到下一行，或將它們移至前一行的結尾。 下列逐步解說將示範如何建立燈泡出現在目前字組，而且有兩個建議的動作：**轉換為大寫**和**轉換為小寫**。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF)  
  
1.  建立 C# VSIX 專案。 (在**新專案**對話方塊中，選取**Visual C# / 擴充性**，然後**VSIX 專案**。)將方案命名`LightBulbTest`。  
  
2.  新增**編輯器分類器**項目範本加入專案。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
4.  加入下列參考加入專案，並將設定**複製到本機**至`False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  加入新的類別檔案並將其命名**LightBulbTest**。  
  
6.  加入下列 using 陳述式：  
  
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
  
## <a name="implementing-the-light-bulb-source-provider"></a>實作燈泡來源提供者  
  
1.  LightBulbTest.cs 類別檔案中刪除 LightBulbTest 類別。 將類別命名為**TestSuggestedActionsSourceProvider**實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>。 匯出名稱為**測試建議動作**和<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>為"text"。  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  在來源提供者類別中，匯入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>並將它加入做為屬性。  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>方法以傳回<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>物件。 我們將討論下一節中的來源。  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>實作 ISuggestedActionSource  
 建議的動作來源負責收集組建議的動作，並將它們加入正確的內容中。 在此情況下是目前的文字及建議的動作是**UpperCaseSuggestedAction**和**LowerCaseSuggestedAction**，會在下一節中討論。  
  
1.  將類別加入**TestSuggestedActionsSource**實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>。  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  加入私用的唯讀欄位的建議的動作的來源提供者、 文字緩衝區和文字檢視。  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  新增設定私用欄位的建構函式。  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  加入私用的方法會傳回目前正在進行資料指標的字組。 下列方法會查看目前游標位置，並要求為文字範圍的文字結構導覽。 如果游標位於一個單字，<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>會以 out 參數傳回，否則`out`參數是`null`而且方法會傳回`false`。  
  
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
  
5.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> 方法。 編輯器會呼叫這個方法，以了解是否要顯示燈泡。 進行此呼叫通常，例如每次您將游標從一行移到另一個，或當滑鼠停留在錯誤波浪線。 它是為了讓其他 UI 的作業繼續執行時使用這個方法非同步。 在大部分情況下這個方法只需要執行一些剖析和分析目前的行，因此處理可能需要一些時間。  
  
     在我們實作它以非同步方式取得<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>並判斷範圍是否有意義的亦即，不論有一些非空白字元的文字。  
  
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
  
6.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>方法，傳回的陣列<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>物件，其中包含不同<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>物件。 燈泡展開時，會呼叫這個方法。  
  
    > [!WARNING]
    >  您應該確定實作`HasSuggestedActionsAsync()`和`GetSuggestedActions()`都是一致的; 也就是說，如果`HasSuggestedActionsAsync()`傳回`true`，然後`GetSuggestedActions()`應該要顯示的某些動作。 在許多情況下`HasSuggestedActionsAsync()`之前呼叫`GetSuggestedActions()`，但不一定是這樣。 例如，如果使用者的按下，叫用燈泡動作 (CTRL +。) 只`GetSuggestedActions()`呼叫。  
  
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
  
7.  定義`SuggestedActionsChanged`事件。  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  若要完成實作，將實作`Dispose()`和`TryGetTelemetryId()`方法。 我們不想進行遙測，請直接傳回 false 並將 GUID 設定為空白。  
  
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
  
## <a name="implementing-light-bulb-actions"></a>實作燈泡動作  
  
1.  在專案中，加入至 Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll，並將參考**複製到本機**至`False`。  
  
2.  建立兩個類別，第一個名為`UpperCaseSuggestedAction`和第二個名為`LowerCaseSuggestedAction`。 這兩個類別都會實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>。  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     這兩個類別是相同的不同之處在於其中一個會呼叫<xref:System.String.ToUpper%2A>和其他呼叫<xref:System.String.ToLower%2A>。 下列步驟僅涵蓋大寫動作類別，但您必須實作這兩個類別。 使用實作大寫動作的步驟，作為實作小寫動作的模式。  
  
3.  加入下列 using 陳述式，這些類別：  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  宣告一組私用欄位。  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  加入可設定欄位的建構函式。  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>方法，使它顯示動作預覽。  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>方法，使它傳回空白<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>列舉型別。  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  依照下列所示來實作屬性。  
  
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
  
9. 實作<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>其大寫對等項目以取代範圍中的文字的方法。  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  燈泡動作**Invoke**方法不會顯示 UI。  如果您的動作並帶出新的使用者介面 （例如的預覽或選取範圍對話方塊），不會顯示直接從 UI **Invoke**方法，但改為排程，以從傳回之後顯示您的 UI **Invoke**.  
  
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
  
11. 別忘了執行相同的動作，`LowerCaseSuggestedAction`變更顯示文字 「 轉換 '{0}' 為小寫 」 並呼叫<xref:System.String.ToUpper%2A>至<xref:System.String.ToLower%2A>。  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試這段程式碼，建置 LightBulbTest 方案，並在實驗執行個體中執行。  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔，並輸入一些文字。 您應該會看到燈泡文字的左邊。  
  
     ![測試燈泡](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  指向燈泡。 您應該會看到向下箭號。  
  
5.  當您按一下燈泡時，兩個建議的動作應該會顯示，以及所選取動作的預覽。  
  
     ![測試燈泡，已展開](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  如果您按一下第一個動作，則應該會將目前字組中的所有文字都轉換為大寫。 如果您按一下第二個動作，則應該會將所有文字都轉換為小寫。  
  