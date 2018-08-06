---
title: 逐步解說： 實作程式碼片段 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d3191f14cb3ad10b6fb95f2da6a3a4281c839de
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566593"
---
# <a name="walkthrough-implement-code-snippets"></a>逐步解說： 實作程式碼片段
您可以建立程式碼片段，並將它們包含在編輯器擴充功能，以便延伸模組的使用者可以將它們加入自己的程式碼。  
  
 程式碼片段是程式碼或其他可以納入檔案中的文字片段。 若要檢視所有已註冊的特定程式設計語言，在程式碼片段**工具**功能表上，按一下**程式碼片段管理員**。 若要在檔案中，以滑鼠右鍵按一下您想要的程式碼片段中，插入程式碼片段中，按一下 插入程式碼片段，或**環繞**，找出您想，程式碼的片段，，然後按兩下它。 按下** 索引標籤**或是**Shift**+**索引標籤**修改程式碼片段的相關部分，然後按下**Enter**或**Esc**接受它。 如需詳細資訊，請參閱 <<c0> [ 程式碼片段](../ide/code-snippets.md)。  
  
 具有.snippet * 檔案名稱副檔名的 XML 檔案中包含的程式碼片段。 程式碼片段可包含程式碼片段插入，讓使用者可以尋找並加以變更後會反白顯示的欄位。 程式碼片段檔案也會提供資訊**程式碼片段管理員**，讓它可以顯示正確的類別中的程式碼片段名稱。 如需程式碼片段結構描述資訊，請參閱[程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)。  
  
 本逐步解說將說明如何完成這些工作：  
  
1.  建立並註冊特定語言的程式碼片段。  
  
2.  新增**插入程式碼片段**命令至捷徑功能表。  
  
3.  實作程式碼片段展開。  
  
 本逐步解說根據[逐步解說： 顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從下載中心取得。 它包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="create-and-register-code-snippets"></a>建立並註冊程式碼片段  
 一般來說，程式碼片段是與已註冊的語言服務相關聯。 不過，您就不必實作<xref:Microsoft.VisualStudio.Package.LanguageService>註冊程式碼片段。 相反地，只在程式碼片段索引檔案中指定的 GUID，然後使用 在相同的 GUID<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>您新增至您的專案。  
  
 下列步驟示範如何建立程式碼片段，並將它們關聯的特定 GUID。  
  
1.  建立下列目錄結構：  
  
     **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
     何處 *%installdir%* 是 Visual Studio 安裝資料夾。 （雖然這個路徑通常用來安裝的程式碼片段中，您可以指定任何路徑）。  
  
2.  在 [\1033\] 資料夾中，建立 *.xml*檔案並將它命名**TestSnippets.xml**。 (雖然此名稱通常用於程式碼片段索引檔案，您就可以指定任何名稱，因為它具有 *.xml*副檔名。)加入下列文字，然後刪除版面配置區 GUID，並新增您自己。  
  
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
  
3.  在程式碼片段資料夾中建立檔案，將其命名**測試**`.snippet`，然後加入下列文字：  
  
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
  
 下列步驟示範如何註冊的程式碼片段。  
  
### <a name="to-register-code-snippets-for-a-specific-guid"></a>若要針對特定的 GUID 註冊程式碼片段  
  
1.  開啟**CompletionTest**專案。 如需有關如何建立此專案的資訊，請參閱 <<c0> [ 逐步解說： 顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
2.  在專案中，新增下列組件的參考：  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml  
  
3.  在專案中，開啟**source.extension.vsixmanifest**檔案。  
  
4.  請確定**資產**索引標籤包含**VsPackage**內容類型，以及**專案**設為專案的名稱。  
  
5.  選取 CompletionTest 專案，然後在 [屬性] 視窗中設定**產生 Pkgdef 檔案**要 **，則為 true**。 儲存專案。  
  
6.  新增靜態`SnippetUtilities`類別至專案。  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  SnippetUtilities 類別中定義的 GUID，並指定其值用於*SnippetsIndex.xml*檔案。  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  新增<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>至`TestCompletionHandler`類別。 這個屬性可以加入至專案中任何公用或內部 （非靜態） 類別。 (您可能需要新增`using`Microsoft.VisualStudio.Shell 命名空間陳述式。)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. 建置並執行專案。 在啟動時執行專案的 Visual Studio 的實驗性執行個體，您剛剛註冊的程式碼片段應該會顯示在**程式碼片段管理員**下方**TestSnippets**語言。  
  
## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>加入快顯功能表插入片段 命令  
 **插入程式碼片段**命令未包含在文字檔案的捷徑功能表。 因此，您必須啟用命令。  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>若要加入快顯功能表插入片段 命令  
  
1.  開啟`TestCompletionCommandHandler`類別檔案。  
  
     因為這個類別會實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>，您可以啟用**插入程式碼片段**命令，在<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 啟用此命令之前，請檢查，呼叫這個方法是不在 automation 函式因為時**插入程式碼片段**按一下命令時，它會顯示程式碼片段選擇器使用者介面 (UI)。  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  建置並執行專案。 在實驗執行個體中，開啟檔案具有 *.zzz*檔案副檔名，然後再以滑鼠右鍵按一下任何位置中。 **插入程式碼片段**命令應該會出現快顯功能表。  
  
## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>在程式碼片段選擇器 UI 中的實作程式碼片段展開  
 本節說明如何實作程式碼程式碼片段展開，使程式碼片段選擇器 UI 顯示何時**插入程式碼片段**快顯功能表上按一下。 使用者類型的程式碼片段捷徑，然後按下時，也會展開程式碼片段** 索引標籤**。  
  
 若要顯示程式碼片段選擇器 UI，並啟用導覽和接受後插入程式碼片段，使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法。 插入本身由<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>方法。  
  
 程式碼程式碼片段展開的實作會使用舊版<xref:Microsoft.VisualStudio.TextManager.Interop>介面。 當您將從目前的編輯器類別轉譯的舊版程式碼時，請記住，舊版的介面會使用行號和欄數字的組合，在指定的文字緩衝區中的位置，但目前的類別會使用一個索引。 因此，如果緩衝區有每一個都有 10 個字元的三行 （加上新行字元、 一個字元都會被視為）、 第三行的第四個字元位於位置 27 在目前的實作中，但它是第 2 行，在舊的實作中的位置 3。  
  
#### <a name="to-implement-snippet-expansion"></a>若要實作程式碼片段展開  
  
1.  要包含的檔案`TestCompletionCommandHandler`類別中，新增下列`using`陳述式。  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  製作`TestCompletionCommandHandler`類別會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>介面。  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  在 `TestCompletionCommandHandlerProvider`類別中，匯入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>。  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  新增一些程式碼擴充介面的私用欄位和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  建構函式中`TestCompletionCommandHandler`類別中，設定下列欄位。  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  若要顯示的程式碼片段選擇器，當使用者按一下**插入程式碼片段**命令，新增下列程式碼<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法。 (若要讓此說明更容易閱讀，`Exec()`不顯示用於陳述式完成的程式碼; 相反地，程式碼區塊會新增至現有的方法。)字元檢查的程式碼之後新增下列程式碼區塊。  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  如果程式碼片段會有可巡覽的欄位，擴充工作階段保持開啟直到明確接受擴充;如果程式碼片段會不有任何欄位，在工作階段已關閉，而且會當做傳回`null`由<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A>方法。 在 [<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法，您在上一個步驟中，加入的 UI 程式碼片段選擇器之後加入下列程式碼來處理片段瀏覽 (當使用者按下**索引標籤**或**Shift** + **] 索引標籤**之後插入程式碼片段)。  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  若要在使用者型別對應的捷徑，然後按下時插入程式碼片段** 索引標籤**，將程式碼加入<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法。 私用方法，將程式碼片段會顯示在稍後的步驟。 您在上一個步驟中新增的瀏覽程式碼之後新增下列程式碼。  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. 實作的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>介面。 在此實作，感興趣的唯一方法是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>。 其他方法應該只會傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。 實際插入擴充的 helper 方法會涵蓋在稍後的步驟。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>提供列和資料行資訊，您可以從取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. 下列的私用方法插入程式碼片段中，根據捷徑或標題和路徑。 然後它會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A>使用程式碼片段的方法。  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="build-and-test-code-snippet-expansion"></a>建置和測試程式碼程式碼片段展開  
 您可以測試是否在您專案中的程式碼片段展開運作。  
  
1.  建置方案。 當您執行此專案的偵錯工具時，會啟動 Visual Studio 的第二個執行個體。  
  
2.  開啟文字檔案，並輸入一些文字。  
  
3.  在文字中的某處按一下滑鼠右鍵，然後按一下**插入程式碼片段**。  
  
4.  UI 應會顯示與快顯視窗顯示程式碼片段選擇器**測試取代欄位**。 按兩下快顯視窗中。  
  
     應該插入下列程式碼片段。  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     請勿按**Enter**或是**Esc**。  
  
5.  按下** 索引標籤**並**Shift**+**索引標籤**"first"和 「 秒 」 之間切換。  
  
6.  藉由按下其中一個接受插入**Enter**或是**Esc**。  
  
7.  在文字的不同部分中，輸入 「 測試 」，然後按** 索引標籤**。由於 「 測試 」 程式碼片段捷徑，應該再次插入程式碼片段。  
  
## <a name="next-steps"></a>後續步驟