---
title: 將 XML 資料讀入資料集
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 2f1eb51286ae2d64738b91d997a21596fa2a7c35
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921467"
---
# <a name="read-xml-data-into-a-dataset"></a>將 XML 資料讀入資料集

ADO.NET 提供簡單的方法來處理 XML 資料。 在此逐步解說中，您可以建立 XML 資料載入資料集的 Windows 應用程式。 資料集即會顯示在<xref:System.Windows.Forms.DataGridView>控制項。 最後，XML 檔案的內容為基礎的 XML 結構描述會顯示在文字方塊中。

## <a name="create-a-new-project"></a>建立新專案

在此步驟中，建立 Visual Basic 或 VisualC#專案。

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**左窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**ReadingXML**，然後選擇**確定**。

   **ReadingXML**建立專案並將其加入至**方案總管 中**。

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>產生 XML 檔案讀入資料集

本逐步解說著重於 XML 資料讀入資料集，因為提供的 XML 檔案的內容。

1. 在 [專案] 功能表中，選取 [新增新項目]。

2. 選取  **XML 檔案**，將檔案命名**authors.xml**，然後選取**新增**。

   XML 檔案載入設計工具，並且可供編輯。

3. 貼上下列 XML 資料到編輯器中的 XML 宣告如下：

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

4. 在 **檔案**功能表上，選取**儲存 authors.xml**。

## <a name="create-the-user-interface"></a>建立使用者介面

此應用程式的使用者介面是由下列項目所組成：

-   A<xref:System.Windows.Forms.DataGridView>顯示做為資料的 XML 檔案的內容控制項。

-   A<xref:System.Windows.Forms.TextBox>顯示 XML 結構描述的 XML 檔案的控制項。

-   兩個<xref:System.Windows.Forms.Button>控制項。

    -   一個按鈕的 XML 檔案讀入資料集，並顯示在<xref:System.Windows.Forms.DataGridView>控制項。

    -   第二個按鈕會在從資料集，以及透過將結構描述擷取<xref:System.IO.StringWriter>會顯示在<xref:System.Windows.Forms.TextBox>控制項。

### <a name="to-add-controls-to-the-form"></a>若要將控制項加入至表單

1.  開啟`Form1`設計 檢視中。

2.  從**工具箱**，拖曳到表單上的下列控制項：

    -   一個<xref:System.Windows.Forms.DataGridView>控制項

    -   一個<xref:System.Windows.Forms.TextBox>控制項

    -   兩個<xref:System.Windows.Forms.Button>控制項

3.  設定下列屬性：

    |控制項|屬性|設定|
    |-------------|--------------|-------------|
    |`TextBox1`|**多行**|`true`|
    ||[ScrollBars]|**垂直**|
    |`Button1`|**名稱**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**名稱**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>建立接收 XML 資料的資料集

在此步驟中，您會建立新的資料集，名為`authors`。 如需有關資料集的詳細資訊，請參閱 < [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

1.  中**方案總管**，選取的原始程式檔**Form1**，然後選取**檢視表設計工具**按鈕**方案總管 中**工具列。

2.  從[資料索引標籤、 工具箱](../ide/reference/toolbox-data-tab.md)，拖曳**資料集**拖曳至**Form1**。

3.  在 **加入資料集**對話方塊中，選取**不具類型資料集**，然後選取**確定**。

     **DataSet1**已加入至元件匣。

4.  在 **屬性**視窗中，將**名稱**並<xref:System.Data.DataSet.DataSetName%2A>屬性`AuthorsDataSet`。

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>建立 XML 檔案讀入資料集的事件處理常式

**讀取 XML**按鈕會將 XML 檔案讀入資料集。 它接著會根據設定的屬性<xref:System.Windows.Forms.DataGridView>繫結至資料集的控制項。

1.  中**方案總管**，選取**Form1**，然後選取**檢視表設計工具**按鈕**方案總管 中**工具列。

2.  選取 [**讀取 XML** ] 按鈕。

     **程式碼編輯器**會在開啟`ReadXmlButton_Click`事件處理常式。

3.  輸入下列程式碼插入`ReadXmlButton_Click`事件處理常式：

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  在 `ReadXMLButton_Click`事件處理常式程式碼，變更`filepath =`正確路徑的項目。

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>建立事件處理常式，若要在文字方塊中顯示的結構描述

**顯示的結構描述** 按鈕會建立<xref:System.IO.StringWriter>物件，會填入結構描述，並會顯示在<xref:System.Windows.Forms.TextBox>控制項。

1.  在 **方案總管 中**，選取**Form1**，然後選取**檢視表設計工具** 按鈕。

2.  選取 [**顯示的結構描述**] 按鈕。

     **程式碼編輯器**會在開啟`ShowSchemaButton_Click`事件處理常式。

3.  將下列程式碼貼至 `ShowSchemaButton_Click` 事件處理常式。

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>測試表單

您現在可以測試表單，以確定它如預期般運作。

1.  選取  **F5**執行應用程式。

2.  選取 [**讀取 XML** ] 按鈕。

     DataGridView 中顯示 XML 檔案的內容。

3.  選取 [**顯示的結構描述**] 按鈕。

     文字方塊會顯示 XML 檔案的 XML 結構描述。

## <a name="next-steps"></a>後續步驟

本逐步解說會說明 XML 檔案讀入資料集，以及建立結構描述的 XML 檔案的內容為基礎的基本概念。 以下是接下來，您可能會執行一些工作：

-   編輯資料集並將它寫回為 XML 中的資料。 如需詳細資訊，請參閱<xref:System.Data.DataSet.WriteXml%2A>。

-   編輯資料集中的資料，並寫出至資料庫。

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 存取資料](../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)