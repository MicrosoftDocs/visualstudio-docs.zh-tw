---
title: 演練:實現代碼段 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697105"
---
# <a name="walkthrough-implement-code-snippets"></a>演練:實現代碼段
您可以建立程式碼段並將其包含在編輯器擴展中,以便擴展的用戶可以將它們添加到自己的代碼中。

 代碼段是可以合併到檔中的代碼或其他文本片段。 要檢視已註冊為特定程式設計語言的所有程式碼段,請在 **「工具」** 選單上按**一個程式管理員**。 若要在檔案中插入程式碼段,請右鍵按下所需的程式碼段,按下「插入程式碼段」 或「**環繞」** 找到所需的程式碼段,然後按兩碼段。 按**選項卡**或 **「移位**+**」選項卡**可修改代碼段的相關部分,然後按**Enter**或**Esc**將其接受。 有關詳細資訊,請參閱[程式碼碼段](../ide/code-snippets.md)。

 代碼段包含在具有 .snippet® 檔案名副檔名的 XML 檔中。 代碼段可以包含插入程式碼段後突出顯示的欄位,以便使用者可以尋找和更改這些欄位。 代碼段檔還為**代碼代碼段管理員**提供資訊,以便它可以在正確的類別中顯示代碼段名稱。 有關代碼段架構的資訊,請參考[程式碼碼段架構參考](../ide/code-snippets-schema-reference.md)。

 本演練將介紹如何完成這些任務:

1. 為特定語言創建和註冊代碼段。

2. 將 **「插入代碼段」** 指令加入到快捷選單。

3. 實現代碼段擴展。

   這個演練以[演練:顯示敘述完成](../extensibility/walkthrough-displaying-statement-completion.md)。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-and-register-code-snippets"></a>建立與註冊代碼段
 通常,代碼段與註冊的語言服務相關聯。 但是,您不必實現<xref:Microsoft.VisualStudio.Package.LanguageService>註冊代碼段。 相反,只需在代碼段索引檔中指定 GUID,然後在添加到專案中的<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>GUID 中使用相同的 GUID。

 以下步驟演示如何創建代碼段並將其與特定的 GUID 相關聯。

1. 建立以下目錄結構:

    **%安裝 Dir%\測試片段\片段\1033\\**

    *其中 %InstallDir%* 是可視化工作室安裝資料夾。 (儘管此路徑通常用於安裝代碼段,但您可以指定任何路徑。

2. 在 {1033} 資料夾中,建立*一個 .xml*檔並將命名為**TestSnippets.xml**。 (儘管此名稱通常用於代碼段索引檔,但只要具有 *.xml*檔名擴展名,就可以指定任何名稱。新增以下文字,然後刪除佔位元 GUID 並加入您自己的文字。

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

3. 在程式碼資料夾中建立檔案,命名它**測試**`.snippet`,然後新增以下文字:

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

   以下步驟演示如何註冊代碼段。

### <a name="to-register-code-snippets-for-a-specific-guid"></a>註冊化化介面段

1. 打開**完成測試**專案。 有關如何建立此專案的資訊,請參閱[演練:顯示敘述完成](../extensibility/walkthrough-displaying-statement-completion.md)。

2. 在專案中,新增對以下程式集的引用:

    - 微軟.VisualStudio.文字管理員.互通

    - 微軟.VisualStudio.文本管理員.Interop.8.0

    - 微軟.msxml

3. 在專案中,打開**源.擴展.vsixmanifest**檔案。

4. 確保 **"資產"** 選項卡包含**VsPackage**內容類型,並且**專案**已設置為專案的名稱。

5. 選擇「完成測試」專案,並在「屬性」 視窗集中**將 Pkgdef 檔產生****為 true**。 儲存專案。

6. 向專案添加`SnippetUtilities`靜態類。

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. 在程式碼段實用程式類別中,定義 GUID 並賦予它在*程式碼段索引.xml*檔中使用的值。

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. 將<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>添加到`TestCompletionHandler`類。 此屬性可以添加到專案中的任何公共或內部(非靜態)類。 (您可能需要為 Microsoft`using`添加指令。VisualStudio.Shell 命名空間。

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. 建置並執行專案。 在執行項目時開始的 Visual Studio 實驗實例中,您剛剛註冊的代碼段應以**TestSnippets**語言顯示在**程式碼片段管理器**中。

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>將「插入代碼段」指令加入到快捷選單
 文字檔案的快捷選單中不包括「**插入程式碼段」** 命令。 因此,必須啟用該命令。

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>將「插入代碼段」指令加入到快捷選單

1. 打開類`TestCompletionCommandHandler`檔。

     由於此類實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>,因此<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>可以在方法中啟動**插入代碼段**命令。 在啟用該命令之前,請檢查在自動化函數中未呼叫此方法,因為單擊 **「插入程式碼段」** 命令時,將顯示代碼段選取器使用者介面 (UI)。

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. 建置並執行專案。 在實驗實例中,打開具有 *.zzz*檔名擴展名的檔,然後右鍵單擊其中的任意位置。 **「插入代碼段」** 命令應出現在快捷選單上。

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>在程式碼段選取器 UI 中實現代碼段延伸
 本節演示如何實現代碼段擴展,以便在單擊快捷功能表上單擊**插入代碼段**時顯示代碼段選取器 UI。 當用戶鍵入代碼段快捷方式然後按**Tab**時,代碼段也會展開。

 要顯示程式碼段選取器 UI 並啟用導航和插入後程式碼<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>段接受, 請使用方法。 插入本身由方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>處理。

 程式碼段延伸的使用舊介面<xref:Microsoft.VisualStudio.TextManager.Interop>。 從當前編輯器類轉換為舊代碼時,請記住,舊介面使用行號和列號的組合來指定文本緩衝區中的位置,但當前類使用一個索引。 因此,如果緩衝區有三行,每行有 10 個字元(加上一個換行符,這表示為一個字元),則第三行的第四個字元在當前實現中位於位置 27,但它位於舊實現中的行 2 位置 3。

#### <a name="to-implement-snippet-expansion"></a>實現片段

1. 到包含類`TestCompletionCommandHandler`的檔,添加以下`using`指令。

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. 使`TestCompletionCommandHandler`類實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>介面。

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. 在`TestCompletionCommandHandlerProvider`類別中,匯<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>入 。

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. 為程式碼延伸介面與 新增私密字段<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. 在類的構造函數中`TestCompletionCommandHandler`,設置以下欄位。

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. 若要在使用者按下 **「插入代碼段」** 命令時顯示代碼段選取器,請將以下代碼添加<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>到方法。 (為了使此解釋更具可讀性,不`Exec()`顯示用於語句完成的代碼;相反,代碼塊將添加到現有方法中。在檢查字元的代碼之後添加以下代碼塊。

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. 如果代碼段具有可導航的欄位,則擴展會話將保持打開狀態,直到顯式接受擴展;如果代碼段沒有欄位,則會話將關閉,`null`並<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A>由 方法返回。 在方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>中,在上一步中添加的代碼段選取器 UI 代碼後,添加以下代碼來處理代碼段導航(當使用者在代碼段插入後按**Tab**或**Shift**+**選項卡**)。

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. 若要在使用者鍵入相應的快捷方式然後按**Tab**時插入程式<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>碼段, 請向方法添加代碼。 插入代碼段的私有方法將在後面的步驟中顯示。 在上一步驟中添加的導航代碼後添加以下代碼。

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. 實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>介面的方法。 在這裡實作中,唯一感興趣的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A>是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>與 。 其他方法應該傳<xref:Microsoft.VisualStudio.VSConstants.S_OK>回 。

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。 後續步驟將介紹實際插入擴展的幫助器方法。 提供<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>列和列資訊,可以從抓<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>取 。

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. 以下私有方法基於快捷方式或標題和路徑插入代碼段。 然後,<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A>它使用代碼段調用方法。

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>組建及測試程式碼段延伸
 您可以測試代碼段擴展是否在專案中有效。

1. 建置方案。 在除錯器中執行此專案時,將啟動 Visual Studio 的第二個實體。

2. 開啟文字檔並鍵入一些文字。

3. 右鍵按一下文字中的某處,然後按下**插入代碼段**。

4. 程式碼段選取器 UI 應帶有一個彈出視窗,其中顯示 **「測試替換欄位**」。 按兩下彈出視窗。

     應插入以下代碼段。

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     不要按**Enter**或**Esc**。

5. 按**選項卡****「和」移位**+**」選項卡**在「第一」和「第二」之間切換。

6. 通過按**Enter**或**Esc**接受插入。

7. 在文字的不同部份,鍵入「測試」,然後按**Tab**。由於「測試」是程式碼段快捷方式,因此應再次插入代碼段。

## <a name="next-steps"></a>後續步驟
