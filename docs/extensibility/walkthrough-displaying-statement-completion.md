---
title: 演練:顯示語句完成 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697406"
---
# <a name="walkthrough-display-statement-completion"></a>逐步解說：顯示陳述式完成
可以通過定義要為其提供完成的標識符,然後觸發完成會話來實現基於語言的語句完成。 您可以在語言服務的上下文中定義語句完成,定義自己的檔名副檔名和內容類型,然後僅顯示該類型的完成情況。 或者,您可以觸發現有內容類型的完成,例如"純文字"。 本演練演示如何為「純文字」內容類型(即文字檔的內容類型)觸發語句完成。 "文字"內容類型是所有其他內容類型(包括代碼和 XML 檔)的祖先。

 語句完成通常是通過鍵入某些字元觸發的,例如,通過鍵入標識符的開頭(如"使用")。 它通常透過按**空格鍵**、**選項卡**或**Enter**鍵來提交選擇來消除。 通過使用擊鍵(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面)的命令處理程式和實現介面的處理程式提供者,可以實現在鍵入字元時觸發的<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>IntelliSense 功能。 要建立完成來源(即參與完成的識別符清單),請實現<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>介面和完成來源提供者(<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>介面)。 提供程式是託管擴展框架 (MEF) 元件部件。 他們負責匯出來源類別及控制器類別及匯入服務及代理(例如,<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>啟用文字緩衝區中的導航的與 觸發完成工作階段<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>的 。

 本演練演示如何實現硬編碼標識符集的語句完成。 在完全實現中,語言服務和語言文件負責提供該內容。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

#### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 創建 C# VSIX 專案。 ( 在 **'新增項目'** 對話框中,選擇**視覺化 C# / 可擴充性**,然後選擇**VSIX 專案**。命名解決方案`CompletionTest`。

2. 加入專案加入編輯器分類器項範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

3. 刪除現有類別檔案。

4. 新增對專案的以下參考,並確保**CopyLocal**`false`設定為 :

     微軟.VisualStudio.編輯器

     Microsoft.VisualStudio.Language.Intellisense

     微軟.VisualStudio.OLE.Interop

     微軟.VisualStudio.shell.15.0

     微軟.VisualStudio.shell.不可改變.10.0

     微軟.VisualStudio.文字管理員.互通

## <a name="implement-the-completion-source"></a>實作完成來源
 當用戶鍵入完成觸發器(如標識符的第一個字母)時,完成源負責收集標識符集並將內容添加到完成視窗。 在此示例中,標識符及其描述在<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>方法中硬編碼。 在大多數實際使用中,您將使用語言的解析器來獲取權杖來填充完成清單。

### <a name="to-implement-the-completion-source"></a>實作完成來源

1. 加入類別檔案，並將它命名為 `TestCompletionSource`。

2. 新增以下匯入:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. 變更類別聲明,`TestCompletionSource`以便<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>實作 :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. 為來源提供者、文字緩衝區和<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>物件清單新增私有欄位(對應於將參與完成工作階段的識別碼):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. 添加設置源提供程式和緩衝區的構造函數。 類別`TestCompletionSourceProvider`在後續步驟中定義:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. 通過添加<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>包含要在上下文中提供的完成完成的完成集來實現該方法。 每個完成集包含一組<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>完成,並對應於完成視窗的選項卡。 (在可視化基本專案中,完成視窗選項卡名為 **"通用****"和"全部**"。"該方法`FindTokenSpanAtPosition`在下一步中定義。

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. 以下方法用於從游標的位置尋找目前單詞:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. 實作`Dispose()`方法 :

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>實現完成來源提供者
 完成源提供程式是實例化完成源的 MEF 元件部分。

### <a name="to-implement-the-completion-source-provider"></a>實現完成來源提供者

1. 新增名為`TestCompletionSourceProvider`的類別<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>,實現 。 使用<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>「純文字」和「測試完成」匯<xref:Microsoft.VisualStudio.Utilities.NameAttribute>出 此類。

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. 匯入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>,在完成源中查找當前單詞。

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. 實現實例<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>化完成源的方法。

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>執行完成指令處理者提供者
 完成指令處理程式提供者的手態,<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>會偵聽文字檢視建立事件,並將檢視從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>- 啟用將指令加入到 Visual Studio shell<xref:Microsoft.VisualStudio.Text.Editor.ITextView>的指令鏈 , 到 。 由於此類是 MEF 匯出,因此還可以使用它導入命令處理程式本身所需的服務。

#### <a name="to-implement-the-completion-command-handler-provider"></a>執行完成指令處理者提供者

1. 新增名為的檔案`TestCompletionCommandHandler`。

2. 使用指令新增這些指令:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. 新增名為`TestCompletionHandlerProvider`的類別<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>,實現 。 使用<xref:Microsoft.VisualStudio.Utilities.NameAttribute>「權杖完成處理程式」、「<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>純文字」和<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>a 匯<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>出此類。

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. 匯入<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, 啟用從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView><xref:Microsoft.VisualStudio.Text.Editor.ITextView>轉換<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>到<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>, 並允許存取標準 Visual Studio 服務。

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. 實現該方法<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>以實例化命令處理程式。

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>執行完成指令處理程式
 由於語句完成是由擊鍵觸發的,因此必須實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面來接收和處理觸發、提交和關閉完成會話的擊鍵。

#### <a name="to-implement-the-completion-command-handler"></a>執行完成指令處理程式

1. 新增名為的`TestCompletionCommandHandler`類別,<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>該類別 :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. 為下一個指令處理程式 (將指令傳遞給該指令)、文字檢視、命令處理程式提供者(允許存取各種服務)和完成工作階段新增私有欄位:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. 新增一個建構函數,用於設定文字檢視和提供者欄位,並將指令加入到命令鏈:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. 通過傳遞<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>指令來實現方法:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. 實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 當此方法收到擊鍵時,它必須執行以下操作之一:

   - 允許將字元寫入緩衝區,然後觸發或篩選完成。 (列印字元執行此操作。

   - 提交完成,但不允許將字元寫入緩衝區。 (顯示完成工作階段時,將執行此操作,為"空格 **"、"選項卡**"和"**輸入**"。

   - 允許將命令傳遞給下一個處理程式。 (所有其他命令。

     由於此方法可能會顯示 UI,<xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>因此呼叫以確保在自動化上下文中不呼叫它:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. 此代碼是觸發完成工作階段的私有方法:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. 下一個範例是取消訂閱事件的<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>私有方法:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>組建及測試代碼
 要測試此代碼,請生成完成測試解決方案並在實驗實例中運行它。

#### <a name="to-build-and-test-the-completiontest-solution"></a>建置和測試測試解決方案

1. 建置方案。

2. 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

3. 建立文字檔案並鍵入一些包含"添加"字的文字。

4. 當您先鍵入「a」,然後鍵入「d」時,應顯示包含「添加」和「適應」的清單。 請注意,已選擇添加。 當您鍵入另一個"d"時,清單應僅包含"添加",現在已選中。 您可以通過按**空格鍵**、**選項卡**或**Enter**鍵提交「新增」,或者透過鍵入 Esc 或任何其他鍵來關閉清單。

## <a name="see-also"></a>另請參閱
- [演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
