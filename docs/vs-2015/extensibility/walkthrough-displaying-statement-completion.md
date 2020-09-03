---
title: 逐步解說：顯示語句完成 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202016"
---
# <a name="walkthrough-displaying-statement-completion"></a>逐步解說：顯示陳述式完成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由定義要提供完成的識別碼，然後觸發完成會話，來執行以語言為基礎的語句完成。 您可以在語言服務的內容中定義語句完成、定義您自己的副檔名和內容類型，然後只顯示該類型的完成，或者您可以觸發現有內容類型的完成，例如「純文字」。 本逐步解說會示範如何針對 "純文字" 內容類型（也就是文字檔的內容類型）觸發語句完成。 "Text" 內容類型是所有其他內容類型（包括程式碼和 XML 檔案）的上階。  
  
 語句完成通常是藉由輸入特定字元來觸發，例如，輸入識別碼的開頭，例如「使用」。 通常會藉由按空格鍵、Tab 或 Enter 鍵來認可選取專案來關閉。 您可以使用命令處理常式 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面) 的按鍵，以及處理介面的處理常式提供者，藉以執行觸發的 IntelliSense 功能 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 。 若要建立完成來源（即參與完成的識別碼清單），請將 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 介面和完成來源提供者 (<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 介面) 。 提供者 Managed Extensibility Framework (MEF) 元件部分。 它們負責匯出來源和控制器類別，以及匯入服務和訊息代理程式（例如，可 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 啟用文字緩衝區中的導覽），以及 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> 觸發完成會話的。  
  
 本逐步解說會示範如何針對硬式編碼的識別碼集來執行語句完成。 在完整的執行中，語言服務和語言檔會負責提供該內容。  
  
## <a name="prerequisites"></a>Prerequisites  
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>建立 MEF 專案  
  
#### <a name="to-create-a-mef-project"></a>建立 MEF 專案  
  
1. 建立 c # VSIX 專案。  (在 [ **新增專案** ] 對話方塊中，選取 [ **Visual c #/** 擴充性]，然後選取 [ **VSIX 專案**]。 ) 為方案命名 `CompletionTest` 。  
  
2. 將編輯器分類專案範本加入至專案。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
3. 刪除現有類別檔案。  
  
4. 將下列參考加入至專案，並確定 **CopyLocal** 設定為 `false` ：  
  
     VisualStudio 編輯器  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     VisualStudio： Interop  
  
     VisualStudio. 14。0  
  
     VisualStudio，不變的10。0  
  
     VisualStudio. TextManager. Interop  
  
## <a name="implementing-the-completion-source"></a>執行完成來源  
 完成來源負責收集識別碼集，並在使用者輸入完成觸發程式（例如識別碼的第一個字母）時，將內容新增至完成視窗。 在此範例中，識別碼和其描述在方法中是硬式編碼 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 。 在大部分的真實世界中，您會使用語言的剖析器來取得權杖，以填入完成清單。  
  
#### <a name="to-implement-the-completion-source"></a>若要執行完成來源  
  
1. 加入類別檔案，並將它命名為 `TestCompletionSource`。  
  
2. 新增這些匯入：  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. 修改的類別宣告 `TestCompletionSource` ，使其實作為 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> ：  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. 新增來源提供者、文字緩衝區和物件清單 (的私用欄位， <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 這些欄位會對應至將參與完成會話) 的識別碼：  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. 加入可設定來源提供者和緩衝區的函式。 `TestCompletionSourceProvider`類別定義于稍後的步驟中：  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. 藉 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 由加入完成集（包含您想要在內容中提供的完成項）來執行方法。 每個完成集都包含一組完成 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> ，並對應至完成視窗的索引標籤。  (在 Visual Basic 專案中，[完成時間範圍] 索引標籤會命名為 [ **通用** ] 和 [ **全部**]。 ) FindTokenSpanAtPosition 方法會在下一個步驟中定義。  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. 下列方法可用來從資料指標的位置尋找目前的單字：  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. 執行 `Dispose()` 方法：  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>執行完成來源提供者  
 完成來源提供者是具現化完成來源的 MEF 元件部分。  
  
#### <a name="to-implement-the-completion-source-provider"></a>若要執行完成來源提供者  
  
1. 加入名為 `TestCompletionSourceProvider` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 。 使用「 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 純文字」和「測試完成」的來匯出這個類別 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 。  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. 匯入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ，用來在完成來源中尋找目前的單字。  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 方法以將完成來源具現化。  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>執行完成命令處理常式提供者  
 完成命令處理常式提供者衍生自，此提供者會 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 接聽文字視圖建立事件並從轉換成（可 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 讓 Visual Studio shell 的命令鏈）新增至 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。 因為這個類別是 MEF 匯出，所以您也可以使用它來匯入命令處理常式本身所需的服務。  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>若要執行完成命令處理常式提供者  
  
1. 新增名為的檔案 `TestCompletionCommandHandler` 。  
  
2. 新增下列 using 語句：  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. 加入名為 `TestCompletionHandlerProvider` 的類別，該類別會執行 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 。 使用「 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 權杖完成處理常式」、「 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 純文字」的和的來匯出這個類別 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> 。  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. 匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> ，這可讓您從轉換為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ，以及可 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 存取標準 Visual Studio 服務的。  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. 執行 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 方法來具現化命令處理常式。  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>執行完成命令處理常式  
 因為按鍵會觸發語句完成，所以您必須執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面以接收和處理會觸發、認可和解除完成會話的按鍵。  
  
#### <a name="to-implement-the-completion-command-handler"></a>若要執行完成命令處理常式  
  
1. 加入名為 `TestCompletionCommandHandler` 的類別，該類別會 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 執行：  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. 為下一個命令處理常式新增私用欄位， (您傳遞命令) 、文字視圖、命令處理常式提供者 (可存取各種服務) 以及完成會話：  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. 加入可設定文字視圖和提供者欄位的函式，並將命令新增至命令鏈：  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. 藉 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 由傳遞命令來執行方法：  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. 實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 當此方法收到按鍵時，必須執行下列其中一項動作：  
  
   - 允許將字元寫入緩衝區，然後觸發或篩選完成。  (列印字元這麼做。 )   
  
   - 認可完成，但不允許將字元寫入緩衝區。  (空白字元] 索引標籤，並在顯示完成會話時輸入。 )   
  
   - 允許將命令傳遞給下一個處理常式。  (所有其他命令。 )   
  
     因為此方法可能會顯示 UI，請呼叫 <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> 以確定不會在自動化內容中呼叫它：  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. 這段程式碼是一個私用方法，會觸發完成會話：  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. 下一個範例是從事件取消訂閱的私用方法 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> ：  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>建置和測試程式碼  
 若要測試此程式碼，請建立 CompletionTest 方案，並在實驗實例中執行它。  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>若要建立及測試 CompletionTest 方案  
  
1. 建置方案。  
  
2. 當您在偵錯工具中執行這個專案時，會具現化第二個 Visual Studio 執行個體。  
  
3. 建立文字檔，並輸入包含 "add" 這個字的一些文字。  
  
4. 當您輸入第一個 "a" 和 "d" 時，應該會顯示包含「新增」和「調整」的清單。 請注意，已選取 [新增]。 當您輸入另一個 "d" 時，清單只應包含 "加法"，這現在已選取。 您可以按下空格鍵、Tab 或 Enter 鍵來認可「加法」，或是輸入 Esc 或任何其他按鍵來解除清單。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
