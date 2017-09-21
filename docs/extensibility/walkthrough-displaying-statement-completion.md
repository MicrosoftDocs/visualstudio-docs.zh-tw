---
title: "逐步解說: 顯示陳述式完成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的陳述式完成"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# 逐步解說: 顯示陳述式完成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以定義您要提供完成的識別項，然後觸發完成的工作階段，以實作語言為基礎的陳述式完成。 您可以語言服務內容中定義陳述式完成、 定義您自己的檔案名稱副檔名和內容類型，然後顯示完成只是該型別，或者完成現有的內容類型的觸發程序 — 例如，「 純文字 」。 本逐步解說示範如何觸發陳述式完成 「 純文字 」 內容類型，也就是文字檔案的內容類型。 「 文字 」 內容類型是所有其他內容類型，包括程式碼和 XML 檔案的上階。  
  
 陳述式完成通常會觸發輸入特定的字元 — 例如，藉由輸入的識別碼，例如 「 使用 」 的開頭。 它通常被按下空格鍵、 Tab 或 Enter 鍵，確認選取項目。 您可以實作 IntelliSense 功能所觸發的輸入字元的按鍵輸入使用的命令處理常式 \( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面\) 和處理常式提供者實作 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 介面。 若要建立完成來源時，這是參與完成的識別項的清單，實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 介面和完成來源提供者 \( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 介面\)。 提供者是 Managed Extensibility Framework \(MEF\) 元件組件。 他們要負責匯出的來源和控制器類別和匯入服務和代理程式 — 例如， <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, ，可讓文字緩衝區中，瀏覽和 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, ，而觸發完成的工作階段。  
  
 本逐步解說示範如何實作硬式編碼的組的識別項的陳述式完成。 在完整的實作中，語言服務和語言文件有責任提供該內容。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立 MEF 專案  
  
#### 建立 MEF 專案  
  
1.  建立 C\# VSIX 專案。 \(在 **新的專案** 對話方塊中，選取 **Visual C\# \/ 擴充性**, ，然後 **VSIX 專案**。\) 將方案命名為 `CompletionTest`。  
  
2.  將編輯器分類項目範本加入至專案。 如需詳細資訊，請參閱[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3.  刪除現有類別檔案。  
  
4.  下列參考加入至專案，並確定 **CopyLocal** 設為 `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## 實作完成來源  
 完成來源負責收集組的識別項，並將內容加入至完成視窗中，當使用者輸入完成觸發程序，例如識別項的第一個字母。 在此範例中，識別項和其描述是硬式編碼 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 方法。 在大部分的實際用途，您會使用您的語言剖析器取得的權杖來擴展完成清單。  
  
#### 若要實作完成來源  
  
1.  將類別檔案，並將它 `TestCompletionSource`。  
  
2.  新增這些匯入:  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  修改的類別宣告 `TestCompletionSource` ，使其實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  加入私用欄位的來源提供者、 文字緩衝區，以及一份 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 物件 \(對應至要參與完成的工作階段識別項\):  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  新增設定的來源提供者和緩衝區的建構函式。`TestCompletionSourceProvider` 類別定義於稍後的步驟:  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 您想要提供的內容中加入一個完成集合，包含所完成的方法。 每個完成集包含一組 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 完成項數目，而對應的索引標籤的 \[完成\] 視窗。 \(在 Visual Basic 專案完成視窗索引標籤會命名為 **常見** 和 **所有**。\) FindTokenSpanAtPosition 方法被定義在下一個步驟。  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  若要尋找目前的文字從游標的位置使用下列方法:  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  實作 `Dispose()` 方法:  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## 實作完成來源提供者  
 完成來源提供者已具現化完成來源 MEF 元件組件。  
  
#### 若要實作完成來源提供者  
  
1.  新增名為 `TestCompletionSourceProvider` 實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>。 匯出與這個類別 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「 純文字 」 和 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 的 「 測試完成 」。  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  匯入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, ，用來尋找目前的文字完成來源中。  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  實作 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 方法具現化完成來源。  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## 實作完成命令處理常式提供者  
 完成命令處理常式提供者衍生自 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, ，其文字檢視建立事件接聽，並將從檢視轉換 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— 可讓 Visual Studio shell 的命令鏈結的命令加入 — 至 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 因為這個類別是 MEF 匯出，您也可以使用它來匯入命令處理常式本身所需的服務。  
  
#### 若要實作完成命令處理常式提供者  
  
1.  新增名為 `TestCompletionCommandHandler`。  
  
2.  加入下列 using 陳述式:  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  新增名為 `TestCompletionHandlerProvider` 實作 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>。 匯出與這個類別 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「 語彙基元的完成處理常式 」 的 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「 純文字 」 和 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 的 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>。  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, ，可讓從 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 到 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, 、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, ，和 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> ，可讓您存取標準的 Visual Studio 服務。  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  實作 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 方法具現化的命令處理常式。  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## 實作完成命令處理常式  
 因為按鍵動作所觸發陳述式完成時，您必須實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面來接收及處理觸發程序、 認可和關閉完成的工作階段的按鍵。  
  
#### 若要實作完成命令處理常式  
  
1.  新增名為 `TestCompletionCommandHandler` 實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  加入私用欄位 \(要您傳遞的命令\) 的下一個命令處理常式、 文字檢視、 命令處理常式提供者 \(這可讓您存取各種服務\)，並完成工作階段:  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  新增的建構函式，設定文字檢視和 \[提供者\] 欄位中，並將命令加到命令鏈結:  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法傳遞沿著命令:  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 當這個方法會接收按鍵動作時，它必須執行這些動作的其中一個動作:  
  
    -   允許寫入緩衝區，並接著觸發程序或篩選完成的字元。 \(列印的字元進行。\)  
  
    -   認可完成，但不是允許寫入緩衝區的字元。 \(空格、 定位及 Enter 時執行此動作會顯示完成的工作階段。\)  
  
    -   允許命令傳遞至下一個處理常式。 \(所有其他命令\)。  
  
     因為這個方法可能會顯示 UI，所以呼叫 <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> 確保不會呼叫內容中的自動化:  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  此程式碼是觸發程序完成的工作階段的私用方法:  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  下一個範例會從取消訂閱的私用方法 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> 事件:  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## 建置和測試程式碼  
 若要測試這段程式碼，CompletionTest 方案中建置並執行它的實驗執行個體。  
  
#### 若要建置和測試 CompletionTest 方案  
  
1.  建置方案。  
  
2.  當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3.  建立文字檔案，並輸入一些文字，其中包含單字"add"。  
  
4.  當您第一次輸入"a"，然後 「 d 的"，應該會顯示包含 「 加法 」 和 「 調整 」 的清單。 請注意已選取 \[新增。 當您輸入另一個"d"時，此清單應包含只有 「 加法 」，其中已選取。 您可以按下空格鍵、 Tab 或 Enter 鍵，以認可 「 加法 」，或輸入其他索引鍵或 Esc 來關閉清單。  
  
## 請參閱  
 [逐步解說: 將內容類型連結至檔案名稱副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)