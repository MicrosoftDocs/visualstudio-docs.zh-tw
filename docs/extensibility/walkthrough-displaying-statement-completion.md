---
title: 逐步解說：顯示語句完成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: madskristensen
ms.author: madsk
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 82ce8a1b9cbc79925ff2f4a1c1df9d832bb96f7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632519"
---
# <a name="walkthrough-display-statement-completion"></a>逐步解說：顯示語句完成
您可以藉由定義要提供完成的識別碼，然後觸發完成會話，來執行以語言為基礎的語句完成。 您可以在語言服務的內容中定義語句完成、定義您自己的副檔名和內容類型，然後只顯示該類型的完成。 或者，您可以觸發現有內容類型的完成（例如，「純文字」）。 本逐步解說會示範如何觸發「純文字」內容類型（也就是文字檔的內容類型）的語句完成。 "Text" 內容類型是所有其他內容類型的上階，包括程式碼和 XML 檔案。

 語句完成通常是藉由輸入特定字元來觸發，例如，藉由輸入識別碼的開頭，例如 "using"。 通常會藉由按**空格鍵**、 **Tab**或**Enter**鍵來認可選取專案來關閉它。 在輸入字元時，您可以使用按鍵的命令處理常式（<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面）和執行 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 介面的處理常式提供者，來實作為 IntelliSense 功能。 若要建立完成來源（這是參與完成的識別碼清單），請執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 介面和完成來源提供者（<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 介面）。 提供者是 Managed Extensibility Framework （MEF）元件部分。 它們負責匯出來源和控制器類別，以及匯入服務和訊息代理程式（例如 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>），這會啟用文字緩衝區中的導覽，以及觸發完成會話的 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>。

 本逐步解說示範如何針對硬式編碼的識別碼集執行語句完成。 在完整的執行中，語言服務和語言檔會負責提供該內容。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-mef-project"></a>建立 MEF 專案

#### <a name="to-create-a-mef-project"></a>建立 MEF 專案

1. 建立C# VSIX 專案。 （在 [**新增專案**] 對話方塊中，選取 [**視覺效果C# /** 擴充性]、[ **VSIX 專案**]）。將方案命名為 `CompletionTest`。

2. 將編輯器分類器專案範本加入至專案。 如需詳細資訊，請參閱[使用編輯器專案範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)功能。

3. 刪除現有類別檔案。

4. 將下列參考新增至專案，並確定**CopyLocal**設定為 `false`：

     VisualStudio 編輯器

     Microsoft.VisualStudio.Language.Intellisense

     VisualStudio. Interop

     VisualStudio. Shell 14。0

     VisualStudio：不變的10。0

     VisualStudio. TextManager Interop

## <a name="implement-the-completion-source"></a>執行完成來源
 完成來源會負責收集一組識別碼，並在使用者輸入完成觸發程式（例如識別碼的第一個字母）時，將內容新增至完成視窗。 在此範例中，識別碼和其描述在 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 方法中是硬式編碼的。 在大部分真實世界的使用中，您會使用語言的剖析器來取得權杖，以填入完成清單。

### <a name="to-implement-the-completion-source"></a>若要執行完成來源

1. 加入類別檔案，並將它命名為 `TestCompletionSource`。

2. 新增下列匯入：

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. 修改 `TestCompletionSource` 的類別宣告，讓它執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>：

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. 新增來源提供者、文字緩衝區的私用欄位，以及 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 物件清單（對應至將參與完成會話的識別碼）：

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. 加入設定來源提供者和緩衝區的函式。 @No__t_0 類別定義于稍後的步驟中：

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. 藉由新增完成集（其中包含您要在內容中提供的完成）來執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 方法。 每個完成集都包含一組 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 完成，並對應至完成視窗的索引標籤。 （在 Visual Basic 專案中，完成視窗索引標籤會命名為**Common**和**All**）。@No__t_2 方法是在下一個步驟中定義。

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. 下列方法可用來從資料指標的位置尋找目前的文字：

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. 執行 `Dispose()` 方法：

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>執行完成來源提供者
 完成來源提供者是具現化完成來源的 MEF 元件部分。

### <a name="to-implement-the-completion-source-provider"></a>若要執行完成來源提供者

1. 新增一個名為 `TestCompletionSourceProvider` 的類別，以執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>。 使用 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的「純文字」和「測試完成」 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 匯出此類別。

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. 匯入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>，以尋找完成來源中的目前文字。

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. 執行 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 方法，以具現化完成來源。

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>執行完成命令處理常式提供者
 完成命令處理常式提供者衍生自 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>，它會接聽文字視圖建立事件，並將此視圖從 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> （可將命令新增至 Visual Studio shell 的命令鏈）轉換成 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 因為此類別是 MEF 匯出，所以您也可以使用它來匯入命令處理常式本身所需的服務。

#### <a name="to-implement-the-completion-command-handler-provider"></a>若要執行完成命令處理常式提供者

1. 新增名為 `TestCompletionCommandHandler` 的檔案。

2. 新增下列 using 指示詞：

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. 新增一個名為 `TestCompletionHandlerProvider` 的類別，以執行 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>。 使用「token 完成處理常式」 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>、「純文字」 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 和 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 來匯出此類別。

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. 匯入 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>，這可讓您從 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 轉換成 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>，以及可存取標準 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 服務的 Visual Studio。

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. 執行 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 方法，以具現化命令處理常式。

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>執行完成命令處理常式
 因為按鍵會觸發語句完成，所以您必須執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面來接收和處理可觸發、認可和解除完成會話的按鍵。

#### <a name="to-implement-the-completion-command-handler"></a>若要執行完成命令處理常式

1. 新增一個名為 `TestCompletionCommandHandler` 的類別，以執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>：

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. 新增下一個命令處理常式的私用欄位（您傳遞命令的目標）、文字視圖、命令處理常式提供者（可存取各種服務），以及完成會話：

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. 新增可設定文字視圖和提供者欄位的函式，並將命令新增至命令鏈：

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. 藉由傳遞命令來執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法：

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. 實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 當此方法收到按鍵時，它必須執行下列其中一項動作：

   - 允許將字元寫入緩衝區，然後觸發或篩選完成。 （列印字元會執行此動作）。

   - 認可完成，但不允許將字元寫入緩衝區。 （**空白、索引標籤和** **Enter 鍵**會在完成會話顯示時執行此動作）。

   - 允許將命令傳遞至下一個處理常式。 （所有其他命令）。

     因為此方法可能會顯示 UI，所以請呼叫 <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>，以確保它不會在自動化內容中呼叫：

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. 此程式碼是用來觸發完成會話的私用方法：

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. 下一個範例是從 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> 事件取消訂閱的私用方法：

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>建立並測試程式碼
 若要測試此程式碼，請建立 CompletionTest 方案，並在實驗實例中執行它。

#### <a name="to-build-and-test-the-completiontest-solution"></a>若要建立並測試 CompletionTest 解決方案

1. 建置方案。

2. 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

3. 建立文字檔，並輸入包含 "add" 一字的一些文字。

4. 當您輸入「a」和「d」時，應該會出現包含「新增」和「調整」的清單。 請注意，已選取 [新增]。 當您輸入另一個 "d" 時，清單應該只會包含「新增」，這現在已被選取。 您可以按**空格鍵**、 **Tab**或**enter**鍵來認可「新增」，或是輸入 Esc 或任何其他按鍵來關閉清單。

## <a name="see-also"></a>請參閱
- [逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
