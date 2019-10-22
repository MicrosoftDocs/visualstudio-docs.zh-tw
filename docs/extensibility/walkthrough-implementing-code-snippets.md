---
title: 逐步解說：執行程式碼片段 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: madskristensen
ms.author: madsk
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 84674a12165a3c5cd47c9004274669d377d330c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632500"
---
# <a name="walkthrough-implement-code-snippets"></a>逐步解說：執行程式碼片段
您可以建立程式碼片段，並將它們包含在編輯器延伸模組中，讓擴充功能的使用者可以將它們加入自己的程式碼中。

 程式碼片段是可以併入檔案中的程式碼片段或其他文字。 若要查看已針對特定程式設計語言註冊的所有程式碼片段，請在 [**工具**] 功能表上，按一下 [**程式碼片段管理員**]。 若要在檔案中插入程式碼片段，請以滑鼠右鍵按一下您想要的程式碼片段，按一下 [插入程式碼片段 **] 或 [** 範圍語句]，找出您想要的程式碼片段，然後按兩下它。 按**tab**或**Shift** +索引標籤可修改程式碼片段的相關部分，然後按**enter**或**Esc**接受它。 如需詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)。

 程式碼片段包含在副檔名為程式碼片段的 XML 檔案中。 程式碼片段可以包含插入程式碼片段後反白顯示的欄位，讓使用者可以尋找並變更它們。 程式碼片段檔案也會提供**程式碼片段管理員**的資訊，讓它可以在正確的類別目錄中顯示程式碼片段名稱。 如需程式碼片段架構的詳細資訊，請參閱[程式碼片段架構參考](../ide/code-snippets-schema-reference.md)。

 本逐步解說將教您如何完成這些工作：

1. 建立並註冊特定語言的程式碼片段。

2. 將 [**插入程式碼片段**] 命令新增至快捷方式功能表。

3. 執行程式碼片段擴充。

   此逐步解說是以[逐步解說：顯示語句完成](../extensibility/walkthrough-displaying-statement-completion.md)為基礎。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-and-register-code-snippets"></a>建立並註冊程式碼片段
 通常，程式碼片段會與已註冊的語言服務相關聯。 不過，您不需要執行 <xref:Microsoft.VisualStudio.Package.LanguageService> 來註冊程式碼片段。 相反地，只需在程式碼片段索引檔中指定 GUID，然後在您新增至專案的 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 中使用相同的 GUID。

 下列步驟示範如何建立程式碼片段，並將其與特定的 GUID 建立關聯。

1. 建立下列目錄結構：

    **%InstallDir%\TestSnippets\Snippets\1033 \\**

    其中 *% InstallDir%* 是 Visual Studio 安裝資料夾。 （雖然此路徑通常用來安裝程式碼片段，但您可以指定任何路徑）。

2. 在 \ 1033 \ 資料夾中，建立 *.xml*檔案，並將它命名為**TestSnippets**。 （雖然此名稱通常用於程式碼片段索引檔案，但您可以指定任何名稱，只要其副檔名為 *.xml* ）。新增下列文字，然後刪除預留位置 GUID 並新增您自己的 GUID。

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

3. 在 [程式碼片段] 資料夾中建立檔案，將它命名為**test** `.snippet`，然後新增下列文字：

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

   下列步驟顯示如何註冊程式碼片段。

### <a name="to-register-code-snippets-for-a-specific-guid"></a>若要註冊特定 GUID 的程式碼片段

1. 開啟**CompletionTest**專案。 如需如何建立此專案的詳細資訊，請參閱[逐步解說：顯示語句完成](../extensibility/walkthrough-displaying-statement-completion.md)。

2. 在專案中，加入下列元件的參考：

    - VisualStudio. TextManager Interop

    - VisualStudio. TextManager. Interop 8。0

    - microsoft msxml

3. 在專案中，開啟**extension.vsixmanifest**檔案。

4. 請確定 [**資產**] 索引標籤包含**VsPackage**內容類型，且該**專案**已設定為專案的名稱。

5. 選取 [CompletionTest] 專案，然後在屬性視窗將 [**產生 .pkgdef**檔案] 設定為 [ **true**]。 儲存專案。

6. 將靜態 `SnippetUtilities` 類別加入至專案。

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. 在 SnippetUtilities 類別中，定義 GUID，並為它提供您在*SnippetsIndex*中使用的值。

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. 將 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 新增至 `TestCompletionHandler` 類別。 這個屬性可以加入至專案中的任何公用或內部（非靜態）類別。 （您可能必須為 VisualStudio 命名空間加入 `using` 指示詞）。

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. 建置並執行專案。 在執行專案時啟動之 Visual Studio 的實驗實例中，您剛註冊的程式碼片段應該會顯示在 [**程式碼片段管理員**] 中的**TestSnippets**語言之下。

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>將 [插入程式碼片段] 命令新增至快捷方式功能表
 [**插入程式碼片段**] 命令不會包含在文字檔的快捷方式功能表上。 因此，您必須啟用命令。

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>若要將 [插入程式碼片段] 命令新增至快捷方式功能表

1. 開啟 `TestCompletionCommandHandler` 類別檔案。

     因為這個類別會實 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>，所以您可以在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法中啟動 [**插入程式碼片段**] 命令。 啟用命令之前，請先檢查是否未在 automation 函式內呼叫這個方法，因為按一下 [**插入程式碼片段**] 命令時，它會顯示程式碼片段選擇器使用者介面（UI）。

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. 建置並執行專案。 在實驗實例中，開啟副檔名為*zzz*的檔案，然後以滑鼠右鍵按一下其中的任何位置。 [**插入程式碼片段**] 命令應該會出現在快捷方式功能表上。

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>在程式碼片段選擇器 UI 中執行程式碼片段擴充
 本節說明如何執行程式碼片段擴充，以便在快捷方式功能表上按一下 [**插入程式碼片段**] 時，顯示程式碼片段選擇器 UI。 當使用者輸入程式碼片段快捷方式，然後按**Tab 鍵**時，也會展開程式碼片段。

 若要顯示程式碼片段選擇器 UI，並啟用導覽和後置插入程式碼片段接受，請使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 插入本身會由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法處理。

 程式碼片段擴展的執行會使用舊版 <xref:Microsoft.VisualStudio.TextManager.Interop> 介面。 當您從目前的編輯器類別轉譯為舊版程式碼時，請記住，舊版介面會使用行號和欄號的組合來指定文本緩衝區中的位置，但目前的類別會使用一個索引。 因此，如果緩衝區有三行，其中每個都有10個字元（加上一個分行符號，這會計算為一個字元），則第四行的第四個字元會在目前的實作為位置27，但在舊的執行中，位置為3。

#### <a name="to-implement-snippet-expansion"></a>若要執行程式碼片段擴充

1. 在包含 `TestCompletionCommandHandler` 類別的檔案中，新增下列 `using` 指示詞。

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. 讓 `TestCompletionCommandHandler` 類別執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 介面。

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. 在 `TestCompletionCommandHandlerProvider` 類別中，匯入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>。

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. 為程式碼展開介面和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 新增一些私用欄位。

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. 在 `TestCompletionCommandHandler` 類別的函式中，設定下欄欄位。

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. 當使用者按一下 [**插入程式碼片段**] 命令時，若要顯示程式碼片段選擇器，請將下列程式碼新增至 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 （若要讓此說明更容易閱讀，則不會顯示用於語句完成的 `Exec()`code，而是會將程式碼區塊新增至現有的方法）。在檢查字元的程式碼後面新增下列程式碼區塊。

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. 如果程式碼片段有可流覽的欄位，展開會話會保持開啟狀態，直到明確接受擴展為止;如果程式碼片段沒有任何欄位，則會話會關閉，並以 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> 方法所 `null` 的方式傳回。 在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法中，在您于上一個步驟中新增的程式碼片段選擇器 UI 程式碼之後，新增下列程式碼以處理程式碼片段導覽（當使用者在插入程式碼片段後按**tab**鍵或**Shift** +**tab** ）。

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. 若要在使用者輸入對應的快捷方式，然後按下**Tab 鍵**時插入程式碼片段，請將程式碼加入至 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 插入程式碼片段的私用方法會在稍後的步驟中顯示。 在您于上一個步驟中新增的導覽程式碼之後，新增下列程式碼。

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. 執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 介面的方法。 在此執行中，只會 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 相關的唯一方法。 其他方法應該只傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。 在稍後的步驟中，會說明實際插入擴充的 helper 方法。 @No__t_0 提供行和欄資訊，您可以從 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 取得這兩者。

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. 下列私用方法會根據快捷方式或標題和路徑，插入程式碼片段。 然後，它會使用程式碼片段呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> 方法。

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>組建和測試程式碼片段擴充
 您可以測試專案中的程式碼片段展開是否正常運作。

1. 建置方案。 當您在偵錯工具中執行此專案時，會啟動 Visual Studio 的第二個實例。

2. 開啟文字檔並輸入一些文字。

3. 以滑鼠右鍵按一下文字中的任何位置，然後按一下 [**插入程式碼片段**]。

4. 程式碼片段選擇器 UI 應該會出現一個快顯視窗，指出**測試取代欄位**。 按兩下快顯視窗。

     應插入下列程式碼片段。

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     不要按**enter**或**Esc**鍵。

5. 按**tab**和**Shift** +索引標籤，在「第一個」和「第二個」之間切換。

6. 按**enter**或**Esc**鍵接受插入。

7. 在文字的不同部分中，輸入 "test"，然後按**tab**鍵。因為「測試」是程式碼片段的快捷方式，所以應該再次插入程式碼片段。

## <a name="next-steps"></a>後續步驟
