---
title: 將 XML 資料讀入資料集
description: 將 XML 資料讀入資料集。 在這個逐步解說中，您會建立 Windows 應用程式，將 XML 資料載入資料集。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b3a238bf325819b340b983618b5aac8f723184f4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216185"
---
# <a name="read-xml-data-into-a-dataset"></a>將 XML 資料讀入資料集

ADO.NET 提供簡單的方法來處理 XML 資料。 在這個逐步解說中，您會建立 Windows 應用程式，將 XML 資料載入資料集。 然後，資料集會顯示在 <xref:System.Windows.Forms.DataGridView> 控制項中。 最後，根據 XML 檔案內容的 XML 架構會顯示在文字方塊中。

## <a name="create-a-new-project"></a>建立新專案

為 c # 或 Visual Basic 建立新的 **Windows Forms 應用程式** 專案。 將專案命名為 **ReadingXML**。

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>產生要讀入資料集的 XML 檔案

因為本逐步解說著重于將 XML 資料讀入資料集，所以會提供 XML 檔案的內容。

1. 在 [專案] 功能表上，選取 [新增項目]。

2. 選取 [ **XML** 檔案]，將檔案命名為 **authors.xml**，然後選取 [ **新增**]。

   XML 檔案會載入至設計工具中，並且可供編輯。

3. 將下列 XML 資料貼入編輯器的 XML 宣告下方：

   ```xml
   <Authors_Table>
     <authors>
       <au_id>172-32-1176</au_id>
       <au_lname>White</au_lname>
       <au_fname>Johnson</au_fname>
       <phone>408 496-7223</phone>
       <address>10932 Bigge Rd.</address>
       <city>Menlo Park</city>
       <state>CA</state>
       <zip>94025</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>213-46-8915</au_id>
       <au_lname>Green</au_lname>
       <au_fname>Margie</au_fname>
       <phone>415 986-7020</phone>
       <address>309 63rd St. #411</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94618</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>238-95-7766</au_id>
       <au_lname>Carson</au_lname>
       <au_fname>Cheryl</au_fname>
       <phone>415 548-7723</phone>
       <address>589 Darwin Ln.</address>
       <city>Berkeley</city>
       <state>CA</state>
       <zip>94705</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>267-41-2394</au_id>
       <au_lname>Hunter</au_lname>
       <au_fname>Anne</au_fname>
       <phone>408 286-2428</phone>
       <address>22 Cleveland Av. #14</address>
       <city>San Jose</city>
       <state>CA</state>
       <zip>95128</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>274-80-9391</au_id>
       <au_lname>Straight</au_lname>
       <au_fname>Dean</au_fname>
       <phone>415 834-2919</phone>
       <address>5420 College Av.</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94609</zip>
       <contract>true</contract>
     </authors>
   </Authors_Table>
   ```

4. **在 [檔案**] 功能表上，選取 [**儲存 authors.xml**。

## <a name="create-the-user-interface"></a>建立使用者介面

此應用程式的使用者介面包含下列各項：

- 將 <xref:System.Windows.Forms.DataGridView> XML 檔案的內容顯示為數據的控制項。

- <xref:System.Windows.Forms.TextBox>控制項，顯示 xml 檔案的 xml 架構。

- 兩個 <xref:System.Windows.Forms.Button> 控制項。

  - 其中一個按鈕會將 XML 檔案讀入資料集，並將它顯示在 <xref:System.Windows.Forms.DataGridView> 控制項中。

  - 第二個按鈕會將架構從資料集解壓縮，然後 <xref:System.IO.StringWriter> 在控制項中顯示架構 <xref:System.Windows.Forms.TextBox> 。

### <a name="to-add-controls-to-the-form"></a>若要將控制項加入至表單

1. `Form1`在設計檢視中開啟。

2. 將下列控制項從 [ **工具箱**] 拖曳至表單：

    - 一個 <xref:System.Windows.Forms.DataGridView> 控制項

    - 一個 <xref:System.Windows.Forms.TextBox> 控制項

    - 兩個 <xref:System.Windows.Forms.Button> 控制項

3. 設定下列屬性：

    |控制|屬性|設定|
    |-------------|--------------|-------------|
    |`TextBox1`|**多行**|`true`|
    ||**ScrollBars**|**Vertical**|
    |`Button1`|**名稱**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**名稱**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>建立接收 XML 資料的資料集

在此步驟中，您會建立名為的新資料集 `authors` 。 如需有關資料集的詳細資訊，請參閱 [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

1. 在 **方案總管** 中，選取 **Form1** 的原始程式檔，然後選取 **方案總管** 工具列上的 [**視圖設計** 工具] 按鈕。

2. 從 [ [工具箱] 的 [資料]](../ide/reference/toolbox-data-tab.md)索引標籤，將 **資料集** 拖曳到 **Form1**。

3. 在 [ **加入資料集** ] 對話方塊中，選取 [不具 **類型的資料集**]，然後選取 **[確定]**。

     **DataSet1** 會新增至元件匣。

4. 在 [ **屬性** ] 視窗中，設定的 **名稱** 和 <xref:System.Data.DataSet.DataSetName%2A> 屬性 `AuthorsDataSet` 。

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>建立事件處理常式，以將 XML 檔案讀取至資料集

[ **讀取 xml** ] 按鈕會將 XML 檔案讀取至資料集。 然後，它會在控制項上設定屬性 <xref:System.Windows.Forms.DataGridView> ，以將其系結至資料集。

1. 在 **方案總管** 中，選取 [ **Form1**]，然後選取 **方案總管** 工具列上的 [**視圖設計** 工具] 按鈕。

2. 選取 [ **讀取 XML** ] 按鈕。

     程式 **代碼編輯器** 會在 `ReadXmlButton_Click` 事件處理常式中開啟。

3. 在 `ReadXmlButton_Click` 事件處理常式中輸入下列程式碼：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet2":::

4. 在 `ReadXMLButton_Click` 事件處理常式程式碼中，將 `filepath =` 專案變更為正確的路徑。

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>建立事件處理常式，以在文字方塊中顯示架構

[ **顯示架構** ] 按鈕 <xref:System.IO.StringWriter> 會建立填入架構的物件，並顯示在 <xref:System.Windows.Forms.TextBox> 控制項中。

1. 在 **方案總管** 中，選取 [ **Form1**]，然後選取 [ **視圖設計** 工具] 按鈕。

2. 選取 [ **顯示架構** ] 按鈕。

     程式 **代碼編輯器** 會在 `ShowSchemaButton_Click` 事件處理常式中開啟。

3. 將下列程式碼貼至 `ShowSchemaButton_Click` 事件處理常式。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form"></a>測試表單

您現在可以測試表單，以確保其行為如預期般運作。

1. 選取 **F5** 以執行應用程式。

2. 選取 [ **讀取 XML** ] 按鈕。

     DataGridView 會顯示 XML 檔案的內容。

3. 選取 [ **顯示架構** ] 按鈕。

     此文字方塊會顯示 XML 檔案的 XML 架構。

## <a name="next-steps"></a>下一步

本逐步解說會教您如何將 XML 檔案讀入資料集，以及根據 XML 檔案的內容建立架構。 以下是您接下來可能會執行的一些工作：

- 編輯資料集中的資料，並將其寫回為 XML。 如需詳細資訊，請參閱<xref:System.Data.DataSet.WriteXml%2A>。

- 編輯資料集中的資料，並將它寫出至資料庫。

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 存取資料](../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)
