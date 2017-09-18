---
title: "逐步解說: 實作程式碼片段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 逐步解說: 實作程式碼片段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以建立程式碼片段，並將它們包含在編輯器延伸模組，以便擴充功能的使用者可以將它們加入自己的程式碼。  
  
 程式碼片段是程式碼或其他可以合併檔案中的文字片段。 若要檢視所有已註冊為特定的程式設計語言，在程式碼片段 **工具** \] 功能表上，按一下 \[ **程式碼片段管理員**。 若要插入程式碼片段在檔案中，以滑鼠右鍵按一下您想要的程式碼片段中，按一下 **插入程式碼片段** 或 **環繞**, ，找出您想，程式碼的片段，然後按兩下它。 按 TAB 或 SHIFT \+ TAB，修改相關部分的程式碼片段，然後按下 ENTER 或 esc 鍵，以接受它。 如需詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)。  
  
 程式碼片段會包含在具有.snippet 副檔名的 XML 檔案。 程式碼片段可包含程式碼片段插入，讓使用者可以尋找並加以變更後會反白顯示的欄位。 程式碼片段檔案也會提供資訊 **程式碼片段管理員** ，讓它可以顯示程式碼片段名稱正確類別中。 如需程式碼片段結構描述資訊，請參閱 [程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)。  
  
 這個逐步解說示範如何完成這些工作:  
  
1.  建立並註冊特定語言的程式碼片段。  
  
2.  新增 **插入程式碼片段** 命令至快速鍵功能表。  
  
3.  實作程式碼片段擴充。  
  
 本逐步解說根據 [逐步解說: 顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
## 必要條件  
 若要依照本逐步解說，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 建立和註冊程式碼片段  
 一般來說，程式碼片段是與已註冊的語言服務相關聯。 然而，您不需要實作 <xref:Microsoft.VisualStudio.Package.LanguageService> 註冊程式碼片段。 相反地，只在程式碼片段的索引檔案中指定的 GUID，然後使用相同的 GUID 在 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 您加入至您的專案。  
  
 下列步驟示範如何建立程式碼片段，並將它們關聯的特定 GUID。  
  
1.  建立下列目錄結構:  
  
     **%InstallDir%\\TestSnippets\\Snippets\\1033\\**  
  
     其中 *%installdir%* 是 Visual Studio 安裝資料夾。 \(雖然這個路徑通常用來安裝程式碼片段中，您可以指定任何路徑\)。  
  
2.  在 \\1033\\ 資料夾中，建立一個.xml 檔案，並將它 **TestSnippets.xml**。 \(雖然這個名稱通常用於程式碼片段的索引檔案，您可以指定任何名稱，只要它具有.xml 副檔名。\) 加入下列文字，然後刪除版面配置區 GUID，並加入您自己。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  程式碼片段資料夾中建立的檔案、 將它命名 **測試**`.snippet`, ，然後加入下列文字:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 下列步驟顯示如何註冊的程式碼片段。  
  
#### 特定 GUID 的註冊程式碼片段  
  
1.  開啟 **CompletionTest** 專案。 如需有關如何建立此專案的資訊，請參閱 [逐步解說: 顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
2.  在專案中，加入下列組件的參考:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml  
  
3.  在專案中，開啟 source.extension.vsixmanifest 檔案。  
  
4.  請確定 **資產** \] 索引標籤包含 **VsPackage** 內容型別， **專案** 設為專案的名稱。  
  
5.  選取 CompletionTest 專案，然後在 \[屬性\] 視窗中設定 **產生 Pkgdef 檔** 至 **true**。 儲存專案。  
  
6.  新增靜態 `SnippetUtilities` 類別至專案。  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  在 SnippetUtilities 類別中，定義 GUID，並提供您使用 SnippetsIndex.xml 檔案中的值。  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  新增 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 至 `TestCompletionHandler` 類別。 這個屬性可以加入至專案中任何公用或內部 \(非靜態\) 類別中。 \(您可能要加入 `using` Microsoft.VisualStudio.Shell 命名空間陳述式。\)  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. 建置並執行專案。 在 Visual Studio 啟動時執行專案時執行的實驗執行個體，您剛登錄的程式碼片段應該會顯示在 **程式碼片段管理員** 下 **TestSnippets** 語言。  
  
## 加入快顯功能表插入片段命令  
 **插入程式碼片段** 命令未包含在文字檔案的捷徑功能表。 因此，您必須啟用命令。  
  
#### 若要新增的快顯功能表插入片段\] 命令  
  
1.  開啟 `TestCompletionCommandHandler` 類別檔案。  
  
     因為這個類別會實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, ，您可以啟用 **插入程式碼片段** 命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法。 啟用此命令之前，請檢查，呼叫這個方法不是被自動化函式內因為時 **插入程式碼片段** 命令被按下，便會顯示程式碼片段選擇器使用者介面 \(UI\)。  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  建置並執行專案。 在實驗性的執行個體，開啟.zzz 副檔名的檔案，然後以滑鼠右鍵按一下任何位置中。**插入程式碼片段** 命令應該會出現快顯功能表。  
  
## 在程式碼片段選擇器 UI 中實作程式碼片段擴充  
 本節說明如何實作程式碼片段擴充，使程式碼片段選擇器 UI 時顯示 **插入程式碼片段** 快顯功能表上按一下。 使用者類型的程式碼片段捷徑，然後按下 TAB 時，則也會延伸程式碼片段。  
  
 若要顯示的程式碼片段選擇器 UI，並啟用瀏覽及後續插入程式碼片段接受，請使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 插入本身由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。  
  
 程式碼片段展開的實作會使用舊版 <xref:Microsoft.VisualStudio.TextManager.Interop> 介面。 當您從目前的編輯器類別轉譯為舊版程式碼時，請記得舊版的介面使用行號和欄數字的組合，在文字緩衝區中，指定位置，但目前的類別會使用一個索引。 因此，如果緩衝區有每個都有 10 個字元的三行 \(加上 1 個字元都算是一個新行\)、 第三列第四個字元位於位置 27 在目前的實作，但它是第 2 行，在舊的實作中的位置 3。  
  
#### 若要實作程式碼片段擴充  
  
1.  包含檔案 `TestCompletionCommandHandler` 類別中，新增下列 `using` 陳述式。  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  請 `TestCompletionCommandHandler` 類別實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 介面。  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  在 `TestCompletionCommandHandlerProvider` 類別中，匯入 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>。  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  加入一些程式碼擴充介面的私用欄位和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  建構函式中 `TestCompletionCommandHandler` 類別中，設定下列欄位。  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  若要顯示程式碼片段選擇器，當使用者按一下 **插入程式碼片段** 命令中，加入下列程式碼以 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 \(若要使這項說明更容易閱讀，不顯示用來完成陳述式的 exec \(\) 程式碼; 相反地，程式碼區塊加入至現有的方法\)。 檢查字元的程式碼後面加入下列程式碼區塊。  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  直到明確地接受擴充; 如果程式碼片段會有可巡覽的欄位，擴充工作階段會保持開啟如果程式碼片段會不有任何欄位，在工作階段已關閉，而且會當做傳回 `null` 由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> 方法。 在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法中，程式碼片段選擇器 UI 程式碼，您在上一個步驟中，加入之後新增下列程式碼來處理片段巡覽 \(當使用者程式碼片段插入後，按 TAB 或 SHIFT \+ TAB\)。  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  若要插入的程式碼片段，使用者型別對應的捷徑，然後按下 TAB 時，將程式碼加入 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法。 私用方法插入程式碼片段會顯示在稍後的步驟。 您在上一個步驟中加入導覽程式碼後面加入下列程式碼。  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. 實作的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 介面。 在此實作中，只有感興趣的方法都是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>。 其他方法應該只會傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。 在稍後的步驟將說明實際插入擴充功能的 helper 方法。<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 提供列和資料行資訊，您可以從取得 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. 下列的私用方法插入程式碼片段，根據捷徑或標題和路徑。 然後它會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> 方法，使用程式碼片段。  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## 建置和測試程式碼片段擴充  
 您可以測試是否擴充程式碼片段適用於您的專案。  
  
1.  建置方案。 當您執行此專案的偵錯工具時，Visual Studio 的第二個執行個體具現化。  
  
2.  開啟文字檔案，並輸入一些文字。  
  
3.  在文字中的某處按一下滑鼠右鍵，然後按一下 **插入程式碼片段**。  
  
4.  UI 應會顯示快顯視窗顯示的程式碼片段選擇器 **測試取代欄位**。 按兩下快顯視窗。  
  
     應插入下列程式碼片段。  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     不要按 ENTER 或 esc 鍵。  
  
5.  按下 TAB，SHIFT \+ TAB 切換之間"first"和"第二個 」。  
  
6.  按下 ENTER 或 esc 鍵，以接受插入。  
  
7.  在文字的不同部分中，輸入 「 測試 」，然後按 TAB 鍵。 因為 「 測試 」 程式碼片段捷徑，應該再次插入程式碼片段。  
  
## 後續步驟