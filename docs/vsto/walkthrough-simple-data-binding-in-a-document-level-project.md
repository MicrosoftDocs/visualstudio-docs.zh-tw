---
title: 逐步解說：在文件層級專案中的簡單資料繫結
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b6a23609f096f28d63afc952c069ef6e280f132
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640260"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>逐步解說：在文件層級專案中的簡單資料繫結
  本逐步解說會示範在文件層級專案中的資料繫結的基本概念。 SQL Server 資料庫中的單一資料欄位繫結至 Microsoft Office Excel 中的具名範圍。 本逐步解說也示範如何新增控制項，可讓您捲動瀏覽資料表中的所有記錄。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 這個逐步解說將說明下列工作：

- 建立 Excel 專案的資料來源。

- 將控制項加入工作表。

- 捲動資料庫記錄。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

-   伺服器的存取權與 Northwind SQL Server 範例資料庫。

-   讀取和寫入至 SQL Server 資料庫的權限。

## <a name="create-a-new-project"></a>建立新專案
 在此步驟中，您將建立的 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立 Excel 活頁簿專案同名**我的簡單資料繫結**，使用 Visual Basic 或 C#。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

   Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**我的簡單資料繫結**專案加入**方案總管 中**。

## <a name="create-the-data-source"></a>建立資料來源
 使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 如果**資料來源**看不到視窗，顯示，請在功能表列選擇**檢視** > **其他 Windows**  >  **資料來源**。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [**資料庫**，然後按一下**下一步]**。

4. 選取資料連接至 Northwind 範例 SQL Server 資料庫，或加入新的連接 using**新的連接** 按鈕。

5. 已選取或建立連接之後，請按一下**下一步**。

6. 清除 [可儲存連線，如果已選取，選項，然後按**下一步]**。

7. 依序展開**資料表**中的節點**資料庫物件**視窗。

8. 選取此核取方塊旁**客戶**資料表。

9. 按一下 [ **完成**]。

   精靈會新增**客戶**資料表**Zdroje dat**視窗。 它也將具類型資料集加入專案中可見**方案總管 中**。

## <a name="add-controls-to-the-worksheet"></a>將控制項加入工作表
 此逐步解說中，您需要兩個已命名的範圍和第一個工作表上的四個按鈕。 首先，新增兩個具名的範圍，從**Zdroje dat**視窗，讓它們自動繫結至資料來源。 接下來，新增按鈕等，從**工具箱**。

### <a name="to-add-two-named-ranges"></a>若要新增兩個名為範圍

1.  確認*我的簡單資料 Binding.xlsx*活頁簿是在 Visual Studio 設計工具中開啟具有**Sheet1**顯示。

2.  開啟**資料來源**視窗中，展開**客戶**節點。

3.  選取  **CompanyName**資料行，然後按一下出現的下拉式箭號。

4.  選取  **NamedRange**在下拉式清單，然後拖曳**CompanyName**加入儲存格的資料行**A1**。

     A<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`companyNameNamedRange`會建立在資料格中**A1**。 在此同時<xref:System.Windows.Forms.BindingSource>名為`customersBindingSource`，資料表配接器和<xref:System.Data.DataSet>執行個體加入至專案。 控制項所繫結<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。

5.  選取 [ **CustomerID**中的資料行**Zdroje dat** ] 視窗中，然後按一下出現的下拉式箭號。

6.  按一下  **NamedRange**在下拉式清單，然後拖曳**CustomerID**加入儲存格的資料行**B1**。

7.  另一個<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`customerIDNamedRange`會建立在資料格中**B1**，並繫結至<xref:System.Windows.Forms.BindingSource>。

### <a name="to-add-four-buttons"></a>若要加入四個按鈕

1. 從**通用控制項**索引標籤**工具箱**，加入<xref:System.Windows.Forms.Button>控制項加入儲存格**A3**工作表。

    此欄位稱為`Button1`。

2. 將另外三個按鈕新增至 依此順序中，下列資料格，讓名稱所示：

   |資料格|(名稱)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   下一個步驟是將文字加入至按鈕，並在 C# 中，加入事件處理常式。

## <a name="initialize-the-controls"></a>初始化的控制項
 設定按鈕文字，並新增事件處理常式期間<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件。

### <a name="to-initialize-the-controls"></a>若要初始化的控制項

1. 在**方案總管 中**，以滑鼠右鍵按一下**Sheet1.vb**或**Sheet1.cs**，然後按一下**檢視程式碼**快顯功能表。

2. 將下列程式碼加入`Sheet1_Startup`方法來設定每個按鈕的文字。

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. 僅適用 C#，加入事件處理常式按鈕按一下事件`Sheet1_Startup`方法。

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   現在將新增程式碼來處理<xref:System.Windows.Forms.Control.Click>按鈕的事件，讓使用者可以瀏覽記錄。

## <a name="add-code-to-enable-scrolling-through-the-records"></a>加入程式碼來啟用捲動記錄
 將程式碼加入<xref:System.Windows.Forms.Control.Click>記錄之間移動的每個按鈕事件處理常式。

### <a name="to-move-to-the-first-record"></a>移至第一筆記錄

1.  新增事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`Button1`按鈕，然後新增下列程式碼移至第一筆記錄：

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>若要移到上一筆記錄

1.  新增事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`Button2`按鈕，然後新增下列程式碼，將位置移回一個：

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>移至下一筆記錄

1.  新增事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`Button3`按鈕，然後新增下列程式碼位置前移一個：

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>若要移動的最後一個記錄

1.  新增事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`Button4`按鈕，然後新增下列程式碼移到最後的記錄：

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的活頁簿，藉此確定您可以瀏覽資料庫中的記錄。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1.  按下**F5**執行您的專案。

2.  確認第一筆記錄出現在資料格中**A1**並**B1**。

3.  按一下  **>** (`Button3`) 按鈕，然後確認 下一筆記錄顯示在儲存格中**A1**並**B1**。

4.  按一下 其他捲軸按鈕，以確認記錄變更如預期般運作。

## <a name="next-steps"></a>後續步驟
 本逐步解說會示範繫結至資料庫中的欄位的已命名的範圍的基本概念。 接著可以執行下列一些工作：

-   快取的資料，以便可以離線使用。 如需詳細資訊，請參閱[如何：離線或在伺服器上快取資料以用於](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。

-   繫結至資料表中的多個資料行的資料格而不是至一個欄位。 如需詳細資訊，請參閱[逐步解說：在文件層級專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)。

-   使用<xref:System.Windows.Forms.BindingNavigator>捲動記錄的控制項。 如需詳細資訊，請參閱[如何：使用 Windows Form BindingNavigator 控制項巡覽資料](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)。

## <a name="see-also"></a>另請參閱
- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [在 Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [逐步解說：在文件層級專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
