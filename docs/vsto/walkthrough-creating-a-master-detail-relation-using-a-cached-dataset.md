---
title: 使用快取資料集建立主要詳細資料關聯性
description: 瞭解如何在工作表上建立主要/詳細資料關聯並快取資料，讓方案可以離線使用。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 177b21e2278153693601adf7b7dc18b751cf184e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824844"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>逐步解說：使用快取資料集建立主要詳細資料關聯
  本逐步解說將示範如何在工作表上建立主要/詳細資料關聯，以及如何快取資料，讓方案可以離線使用。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

- 將控制項新增至工作表。

- 設定要在工作表中快取的資料集。

- 加入程式碼以啟用記錄的滾動。

- 測試您的專案。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 存取 Northwind SQL Server 範例資料庫。 資料庫可以位於開發電腦或伺服器上。

- 從 SQL Server 資料庫讀取和寫入的許可權。

## <a name="create-a-new-project"></a>建立新專案
 在這個步驟中，您將建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 Visual Basic 或 c #，建立具有「 **我的主版-詳細資料**」名稱的 Excel 活頁簿專案。 確定已選取 [ **建立新檔** ]。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。

   Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的主版-詳細資料** ] 專案加入 **方案總管**。

## <a name="create-the-data-source"></a>建立資料來源
 使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [ **資料庫** ]，然後按 **[下一步]**。

4. 選取與 Northwind 範例 SQL Server 資料庫的資料連線，或使用 [ **新增連接** ] 按鈕來加入新的連接。

5. 選取或建立連接之後，請按 **[下一步]**。

6. 如果已選取連接，請清除選項來儲存連接，然後按 **[下一步]**。

7. 展開 [**資料庫物件**] 視窗中的 [**資料表**] 節點。

8. 選取 [ **Orders** ] 資料表和 [ **Order Details** ] 資料表。

9. 按一下 [完成] 。

   Wizard 會將這兩個數據表加入至 [ **資料來源** ] 視窗。 它也會將具類型的資料集加入至 **方案總管** 中可見的專案。

## <a name="add-controls-to-the-worksheet"></a>將控制項新增至工作表
 在此步驟中，您將會在第一個工作表中加入一個命名範圍、清單物件和兩個按鈕。 首先，從 [ **資料來源** ] 視窗加入命名範圍和清單物件，讓它們自動系結至資料來源。 接下來，從 [ **工具箱**] 加入按鈕。

### <a name="to-add-a-named-range-and-a-list-object"></a>若要加入命名範圍和清單物件

1. 確認 **Master-Detail.xlsx** 活頁簿已在 Visual Studio 設計工具中開啟，並顯示 **Sheet1** 。

2. 開啟 [ **資料來源** ] 視窗，並展開 [ **Orders** ] 節點。

3. 選取 [ **訂單 id** ] 資料行，然後按一下出現的下拉箭號。

4. 按一下下拉式清單中的 [ **NamedRange** ]，然後將 [ **訂單** ] 資料行拖曳至儲存格 **A2**。

     <xref:Microsoft.Office.Tools.Excel.NamedRange> `OrderIDNamedRange` 在儲存格 **A2** 中會建立名為的控制項。 同時， <xref:System.Windows.Forms.BindingSource> 已命名的 `OrdersBindingSource` 、資料表介面卡和 <xref:System.Data.DataSet> 實例會加入至專案。 控制項系結至 <xref:System.Windows.Forms.BindingSource> ，後者接著會系結至 <xref:System.Data.DataSet> 實例。

5. 將 [ **Orders** ] 資料表底下的資料行向下移動。 清單底部是 **訂單詳細資料** 表格;這是因為它是 **Orders** 資料表的子系。 選取此 **訂單詳細資料** 資料表，而不是與 **Orders** 資料表位於相同層級的資料表，然後按一下出現的下拉箭號。

6. 按一下下拉式清單中的 [ **ListObject** ]，然後將 [ **OrderDetails** ] 資料表拖曳到 [資料格 **A6**]。

7. <xref:Microsoft.Office.Tools.Excel.ListObject>名為 **Order_DetailsListObject** 的控制項會在儲存格 **A6** 中建立，並系結至 <xref:System.Windows.Forms.BindingSource> 。

### <a name="to-add-two-buttons"></a>加入兩個按鈕

1. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 <xref:System.Windows.Forms.Button> 控制項加入工作表的儲存格 **A3** 。

    此按鈕的名稱為 `Button1` 。

2. 將另一個 <xref:System.Windows.Forms.Button> 控制項新增至工作表的儲存格 **B3** 。

    此按鈕的名稱為 `Button2` 。

   接下來，標記要在檔中快取的資料集。

## <a name="cache-the-dataset"></a>快取資料集
 將資料集設為公用，並設定 **CacheInDocument** 屬性，以標記要在檔中快取的資料集。

### <a name="to-cache-the-dataset"></a>快取資料集

1. 選取元件匣中的 [ **NorthwindDataSet** ]。

2. 在 [ **屬性** ] 視窗中， **將 [修飾** 詞] 屬性變更為 [ **Public**]。

    在啟用快取之前，資料集必須是公用的。

3. 將 [ **CacheInDocument** ] 屬性變更為 [ **True**]。

   下一步是要在按鈕中加入文字，而在 c # 中加入程式碼來連結事件處理常式。

## <a name="initialize-the-controls"></a>初始化控制項
 設定按鈕文字並在事件期間新增事件處理常式 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 。

### <a name="to-initialize-the-data-and-the-controls"></a>若要初始化資料和控制項

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **sheet1** ] 或 [ **sheet1**]，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 將下列程式碼加入至 `Sheet1_Startup` 方法，以設定按鈕的文字。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet15":::

3. 針對 c #，請將按鈕 click 事件的事件處理常式加入至 `Sheet1_Startup` 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet16":::

## <a name="add-code-to-enable-scrolling-through-the-records"></a>新增程式碼以啟用記錄的滾動
 將程式碼加入至 <xref:System.Windows.Forms.Control.Click> 每個按鈕的事件處理常式，以移動記錄。

### <a name="to-scroll-through-the-records"></a>捲動資料列

1. 加入事件的事件處理常式 <xref:System.Windows.Forms.Control.Click> `Button1` ，並加入下列程式碼，以便在記錄中向前移動：

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet17":::

2. 加入事件的事件處理常式 <xref:System.Windows.Forms.Control.Click> `Button2` ，並加入下列程式碼以前進記錄：

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet18":::

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的活頁簿，以確定資料會如預期般顯示，而且您可以離線使用方案。

### <a name="to-test-the-data-caching"></a>測試資料快取

1. 按 **F5**。

2. 確認已命名範圍和清單物件已填入資料來源中的資料。

3. 按一下按鈕以滾動記錄部分記錄。

4. 儲存活頁簿，然後關閉活頁簿並 Visual Studio。

5. 停用資料庫的連接。 如果資料庫位於伺服器上，請從電腦拔下網路纜線，或如果資料庫位於您的開發電腦上，請停止 SQL Server 服務。

6. 開啟 Excel，然後從 *\bin* 目錄中開啟 **我的 Master-Detail.xlsx** ， (*\My Master-Detail\bin* 中的 Visual Basic 或 *\My Master-Detail\bin\debug* 中的 c # ) 。

7. 滾動某些記錄，以查看工作表在中斷連接時正常運作。

8. 重新連接至資料庫。 如果資料庫位於伺服器上，請再次將您的電腦連接到網路，如果資料庫是在您的開發電腦上，請啟動 SQL Server 服務。

## <a name="next-steps"></a>下一步
 本逐步解說會示範如何在工作表上建立主/詳細資料關聯性，以及快取資料集的基本概念。 接著可以執行下列一些工作：

- 部署該方案。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [快取資料](../vsto/caching-data.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
