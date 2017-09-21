---
title: "逐步解說：建立程式碼片段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼片段, 建立"
  - "程式碼片段, 匯入"
  - "程式碼片段, 參考"
  - "程式碼片段, 取代"
  - "程式碼片段, 捷徑"
  - "程式碼片段, 範本"
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 逐步解說：建立程式碼片段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以建立只有少數步驟的程式碼片段。  您所要做的只是建立 XML 檔案、填入適當的項目並加入您的程式碼。  您也可以加入參考和取代參數至您的程式碼。  您可以在程式碼片段管理員 \(\[**工具\/程式碼片段管理員**\]\) 中使用匯入按鈕將程式碼片段加入到 Visual Studio 安裝中。  
  
> [!TIP]
>  如需如何更輕鬆撰寫程式碼片段的詳細資訊，請在 CodePlex 網站搜尋社群工具，例如[程式碼片段編輯器](http://go.microsoft.com/fwlink/?LinkId=251033) \(英文\)。  
  
## 程式碼片段範本  
 下列是基本程式碼片段範本：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title></Title>  
        </Header>  
        <Snippet>  
            <Code Language="">  
                <![CDATA[]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
  
```  
  
### 建立程式碼片段  
  
1.  在 Visual Studio 建立新的 XML 檔案，並加入上面顯示的範本。  
  
2.  在 Title 項目中填入程式碼片段的標題，例如 "Hello World VB"。  
  
3.  在 Code 項目的 Languages 屬性中填入程式碼片段的語言。  在這個範例中使用 "VB"。  
  
4.  在程式碼項目內的 CDATA 區段中加入一些程式碼，例如：  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  將這個程式碼片段儲存為 VBCodeSnippet.snippet。  
  
### 若要將程式碼片段加入至 Visual Studio  
  
1.  使用程式碼片段管理員，您可以將您的程式碼片段加入至 Visual Studio 安裝。  開啟程式碼片段管理員 \(\[**工具\/程式碼片段管理員**\]\)。  
  
2.  按一下 \[**匯入**\] 按鈕。  
  
3.  移至您在先前程序中儲存程式碼片段的位置，選取它，然後按一下 \[**開啟**\]。  
  
4.  \[**匯入程式碼片段**\] 對話方塊隨即開啟，要求您從右窗格的選項中選擇在哪裡加入程式碼片段。  其中一個選擇應為 \[**My Code 程式碼片段**\]。  選取並按一下 \[**完成**\]，再按一下 \[**確定**\]。  
  
5.  這個程式碼片段複製到下列位置：  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  開啟 Visual Basic 專案並開啟程式碼檔，測試您的程式碼片段。  在檔案中，按一下內容功能表上的 \[**插入程式碼片段**\]，然後按一下 \[**My Code 程式碼片段**\]。  您應該會看到名為 \[**我的 Visual Basic 程式碼片段**\] 的程式碼片段。  按兩下它。  
  
7.  您應會看到 `Console.WriteLine("Hello, World!")` 插入在程式碼中。  
  
### 加入描述和捷徑欄位  
  
1.  描述當您在程式碼片段管理員中檢視時，提供程式碼片段詳細資訊的欄位。  捷徑是標記，使用者可以輸入標記，以插入您的程式碼片段。  編輯您開啟檔案 `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet` 所加入的程式碼片段。  
  
2.  將作者和描述項目加入至標頭項目，並將資料填入。  
  
3.  標頭項目看起來會類似下列所示：  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  開啟程式碼片段管理員並選取您的程式碼片段。  在右窗格中，您應該會看到 \[描述\] 和 \[作者\] 欄位現在已填入。  
  
5.  若要加入捷徑，請加入 Shortcut 項目，以及 Author 和 Description 項目:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  再次儲存程式碼片段檔案。  
  
7.  若要測試捷徑，開啟 Visual Basic 專案並開啟程式碼檔。  在檔案中輸入 `hello`，然後按 TAB。  應該插入程式碼片段。  
  
### 加入參考和匯入  
  
1.  Visual Basic 程式碼片段可讓您使用參考項目在專案中加入參考，以及使用匯入項目加入匯入宣告。\(其他語言中的程式碼片段沒有這項功能\)。例如，如果您將程式碼範例中的 `Console.WriteLine` 變更為 `MessageBox.Show`，則可能需要將 System.Windows.Forms.dll 組件加入至專案。  
  
2.  開啟您的程式碼片段。  
  
3.  在 Snippet 項目之下加入 References 項目：  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  在 Snippet 項目之下加入 Imports 項目：  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  將 CDATA 區段變更為下列項目：  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  儲存程式碼片段。  
  
7.  開啟 Visual Basic 專案並加入程式碼片段。  
  
8.  您會在程式碼行的頂端看見 Imports 陳述式：  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. 查看專案的屬性。  \[參考\] 索引標籤包括 System.Windows.Forms.dll 的參考。  
  
### 加入取代文字  
  
1.  您可以讓使用者取代部份程式碼片段，例如如果您加入變數並且希望使用者以目前專案中的變數取代該變數。  您可以提供兩種類型的取代:常值和物件。  常值是某個類型的字串 \(字串常值、變數名稱或數值字串表示\)。  物件是字串以外的某個類型的執行個體。  在這個程序中，您將宣告常值取代和物件取代，並變更程式碼以參考這些取代。  
  
2.  開啟您的程式碼片段。  
  
3.  這個範例使用 SQL 連接字串，因此，您必須變更 Imports 和 References 項目加入適當的參考：  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Data.dll</Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>System.Xml.dll</Assembly>  
        </Reference>  
    </References>  
    <Imports>  
        <Import>  
            <Namespace>System.Data</Namespace>  
        </Import>  
        <Import>  
            <Namespace>System.Data.SqlClient</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
4.  若要宣告 SQL 連接字串的常值取代，請在 Snippet 項目下方加入 Declarations 項目，在其中加入 Literal 項目與 ID、工具提示和取代預設值的子項目：  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  若要宣告 SQL 連接的物件取代，在 Declarations 項目內加入 Object 項目，然後加入 ID、物件類型、工具提示和預設值的子項目。  產生的 Declarations 項目看起來應該如下所示：  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
        <Object>  
            <ID>SqlConnection</ID>  
            <Type>System.Data.SqlClient.SqlConnection</Type>  
            <ToolTip>Replace with a connection object in your application.</ToolTip>  
            <Default>dcConnection</Default>  
        </Object>  
    </Declarations>  
    ```  
  
6.  在程式碼區段中，使用周圍 $ 符號參考取代文字，例如 `$replacement$`：  
  
    ```  
    <Code Language="VB" Kind="method body">  
        <![CDATA[Dim daCustomers As SqlDataAdapter  
            Dim selectCommand As SqlCommand  
  
            daCustomers = New SqlClient.SqlDataAdapter()  
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)  
            daCustomers.SelectCommand = selectCommand  
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>  
    </Code>  
    ```  
  
7.  儲存程式碼片段。  
  
8.  開啟 Visual Basic 專案並加入程式碼片段。  
  
9. 程式碼應該看起來如下，其中取代 `SQL connection string` 和 `dcConnection` 以淺橙反白顯示。  按 TAB 鍵從一個巡覽至另一個。  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## 請參閱  
 [程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)