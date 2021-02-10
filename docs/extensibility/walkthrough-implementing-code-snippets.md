---
title: 逐步解說：執行程式碼片段 |Microsoft Docs
description: 您可以建立程式碼片段，並將它們包含在編輯器延伸模組中。 瞭解如何使用本逐步解說來建立/註冊程式碼片段。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: cd01ba1196c75589c0f8844c6bfccab88772ffe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961712"
---
# <a name="walkthrough-implement-code-snippets"></a>逐步解說：執行程式碼片段
您可以建立程式碼片段，並將它們包含在編輯器延伸中，讓擴充功能的使用者可以將這些程式碼片段新增至自己的程式碼。

 程式碼片段是可併入檔案中的程式碼片段或其他文字。 若要查看已針對特定程式設計語言註冊的所有程式碼片段，請按一下 [ **工具** ] 功能表上的 [ **程式碼片段管理員**]。 若要將程式碼片段插入檔案中，請以滑鼠右鍵按一下您想要的程式碼片段、按一下 [插入程式碼片段] 或 [ **環繞**]，找出您想要的程式碼片段，然後按兩下它。 按 **tab** 或 **Shift** 索引標籤， + 以修改程式碼片段的相關部分，然後按 **enter** 或 **Esc** 接受它。 如需詳細資訊，請參閱 [程式碼片段](../ide/code-snippets.md)。

 程式碼片段包含在副檔名為程式碼片段的 XML 檔案中。 程式碼片段可以包含欄位，這些欄位會在插入程式碼片段之後反白顯示，讓使用者可以找到並變更它們。 程式碼片段檔案也會提供 **程式碼片段管理員** 的資訊，讓它可以在正確的類別目錄中顯示程式碼片段名稱。 如需程式碼片段架構的詳細資訊，請參閱 [程式碼片段架構參考](../ide/code-snippets-schema-reference.md)。

 本逐步解說會教您如何完成這些工作：

1. 建立並註冊特定語言的程式碼片段。

2. 將 [ **插入程式碼片段** ] 命令新增至快捷方式功能表。

3. 執行程式碼片段展開。

   本逐步解說是根據 [逐步解說：顯示語句完成](../extensibility/walkthrough-displaying-statement-completion.md)。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-and-register-code-snippets"></a>建立並註冊程式碼片段
 一般來說，程式碼片段會與已註冊的語言服務相關聯。 不過，您不需要執行 <xref:Microsoft.VisualStudio.Package.LanguageService> 來註冊程式碼片段。 相反地，只需在程式碼片段索引檔案中指定 GUID，然後在 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 您新增至專案的中使用相同的 guid。

 下列步驟示範如何建立程式碼片段，並將其與特定的 GUID 建立關聯。

1. 建立下列目錄結構：

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    其中 *% InstallDir%* 是 Visual Studio 安裝資料夾。  (雖然這個路徑通常是用來安裝程式碼片段，但您可以指定任何路徑。 ) 

2. 在 \ 1033 \ 資料夾中，建立一個 *.xml* 檔案，然後將它命名為 **TestSnippets.xml**。  (雖然此名稱通常用於程式碼片段索引檔案，但您可以指定任何名稱（只要副檔名為 *.xml* ）。 ) 新增下列文字，然後刪除預留位置 GUID 並加入您自己的 GUID。

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. 在程式碼片段資料夾中建立檔案，將它命名為 **test** `.snippet` ，然後新增下列文字：

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   下列步驟說明如何註冊程式碼片段。

### <a name="to-register-code-snippets-for-a-specific-guid"></a>註冊特定 GUID 的程式碼片段

1. 開啟 **CompletionTest** 專案。 如需如何建立此專案的詳細資訊，請參閱 [逐步解說：顯示語句完成](../extensibility/walkthrough-displaying-statement-completion.md)。

2. 在專案中，加入下列元件的參考：

    - VisualStudio. TextManager. Interop

    - VisualStudio. TextManager. Interop

    - microsoft msxml

3. 在專案中，開啟 **extension.vsixmanifest** 檔案。

4. 請確定 [ **資產** ] 索引標籤包含 **VsPackage** 內容類型，而且該 **專案** 設定為專案的名稱。

5. 選取 CompletionTest 專案，然後在屬性視窗設定 **產生 .pkgdef** 檔案為 **true**。 儲存專案。

6. 將靜態 `SnippetUtilities` 類別加入至專案。

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. 在 SnippetUtilities 類別中定義 GUID，並為其提供您在 *SnippetsIndex.xml* 檔案中使用的值。

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. 將加入 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 至 `TestCompletionHandler` 類別。 這個屬性可以加入至專案中的任何公用或內部 (非靜態) 類別。  (您可能必須加入 `using` VisualStudio 命名空間的指示詞。 ) 

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. 建置並執行專案。 在執行專案時，Visual Studio 的實驗實例中，您剛剛註冊的程式碼片段應該會以 **TestSnippets** 語言顯示在 **程式碼片段管理員** 中。

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>將 [插入程式碼片段] 命令新增至快捷方式功能表
 文字檔的快捷方式功能表上不包含 [ **插入程式碼片段** ] 命令。 因此，您必須啟用此命令。

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>將 [插入程式碼片段] 命令新增至快捷方式功能表

1. 開啟 `TestCompletionCommandHandler` 類別檔案。

     因為這個類別 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 會執行，所以您可以在方法中啟用 [ **插入程式碼片段** ] 命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 。 在您啟用命令之前，請先檢查是否未在 automation 函式內呼叫這個方法，因為按一下 [ **插入程式碼片段** ] 命令時，會顯示程式碼片段選擇器使用者介面 (UI) 。

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. 建置並執行專案。 在實驗實例中，開啟副檔名為 *zzz* 的檔案，然後以滑鼠右鍵按一下其中的任何位置。 [ **插入程式碼片段** ] 命令應該會出現在快捷方式功能表上。

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>在程式碼片段選擇器 UI 中執行程式碼片段展開
 本節說明如何執行程式碼片段展開，以便在快捷方式功能表上按一下 [ **插入程式碼片段** ] 時，顯示程式碼片段選擇器 UI。 當使用者輸入程式碼片段快捷方式，然後按 **Tab 鍵** 時，也會展開程式碼片段。

 若要顯示程式碼片段選擇器 UI，以及啟用流覽和插入後代碼段，請使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 插入本身會由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法處理。

 程式碼片段擴充的執行會使用舊版 <xref:Microsoft.VisualStudio.TextManager.Interop> 介面。 當您從目前的編輯器類別轉譯為舊版程式碼時，請記住，舊版介面會使用行號和欄號的組合來指定文字緩衝區中的位置，但目前的類別會使用一個索引。 因此，如果緩衝區有三行，其中每個字元都有10個字元 (加一個新行，它會計算為一個字元) ，第三行的第四個字元在目前的執行中是位置27，但在舊的實作為第2行的位置3。

#### <a name="to-implement-snippet-expansion"></a>若要執行程式碼片段展開

1. 在包含類別的檔案 `TestCompletionCommandHandler` 中，新增下列指示詞 `using` 。

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. 讓 `TestCompletionCommandHandler` 類別實作為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 介面。

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. 在 `TestCompletionCommandHandlerProvider` 類別中，匯入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 。

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. 為程式碼擴充介面和新增一些私用欄位 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. 在類別的函式中 `TestCompletionCommandHandler` ，設定下欄欄位。

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. 若要在使用者按一下 [ **插入程式碼片段** ] 命令時顯示程式碼片段選擇器，請將下列程式碼加入至 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。  (使此說明更容易閱讀，則 `Exec()` 不會顯示用於語句完成的程式碼，而是會將程式碼區塊新增至現有的方法。 ) 在檢查字元的程式碼之後新增下列程式碼區塊。

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. 如果程式碼片段具有可流覽的欄位，展開會話會保持開啟，直到明確接受擴充為止;如果程式碼片段沒有任何欄位，則會關閉會話，並以 `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> 方法傳回。 在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法中，于您在上一個步驟中新增的程式碼片段選擇器 UI 程式碼之後，新增下列程式碼來處理程式碼片段導覽 (當使用者在插入程式碼片段之後按下 **tab** 鍵或 **Shift** + **鍵** 時，) 。

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. 若要在使用者輸入對應的快捷方式，然後按 **Tab 鍵** 時插入程式碼片段，請將程式碼加入至 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 插入程式碼片段的私用方法會在稍後的步驟中顯示。 在您于上一個步驟中新增的導覽程式碼之後，新增下列程式碼。

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. 執行介面的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 。 在此實行中，唯一感興趣的方法是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 。 其他方法應該只會傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 。

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。 實際插入擴充的 helper 方法會在稍後的步驟中討論。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>提供行和資料行資訊，您可以從取得這些資訊 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. 下列私用方法會根據快速鍵或標題和路徑，插入程式碼片段。 然後，它會 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> 使用程式碼片段來呼叫方法。

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>組建和測試程式碼片段展開
 您可以測試程式碼片段展開是否適用于您的專案。

1. 建置方案。 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

2. 開啟文字檔並輸入一些文字。

3. 以滑鼠右鍵按一下文字中的某處，然後按一下 [ **插入程式碼片段**]。

4. 程式碼片段選擇器 UI 應該會出現一個快顯視窗，指出 **測試取代欄位**。 按兩下快顯視窗。

     應插入下列程式碼片段。

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     請勿按 **enter** 或 **Esc 鍵**。

5. 按 **tab** 和 **Shift** 索引標籤， + 以在 "first" 和 "second" 之間切換。

6. 按 **enter** 或 **Esc** 接受插入。

7. 在文字的不同部分中，輸入 "test"，然後按 **tab** 鍵。因為「測試」是程式碼片段快捷方式，所以應該再次插入程式碼片段。

## <a name="next-steps"></a>後續步驟
