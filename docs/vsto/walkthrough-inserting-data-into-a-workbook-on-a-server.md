---
title: 逐步解說：在伺服器的活頁簿中插入資料
description: 瞭解如何使用 ServerDocument 類別，將資料插入至 Microsoft Excel 活頁簿中快取的資料集，而不需啟動 Excel。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bf5d3bcb09ce1db013b89e60b22308f1904c4796
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827717"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>逐步解說：在伺服器的活頁簿中插入資料
  本逐步解說示範如何將資料插入 Microsoft Office Excel 活頁簿中快取的資料集，而不需要使用類別啟動 Excel <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 本逐步解說將說明下列工作：

- 定義包含來自 AdventureWorksLT 資料庫之資料的資料集。

- 在 Excel 活頁簿專案和主控台應用程式專案中建立資料集的實例。

- 建立與活頁 <xref:Microsoft.Office.Tools.Excel.ListObject> 簿中的資料集系結的。

- 將活頁簿中的資料集加入至資料快取。

- 藉由在主控台應用程式中執行程式碼來將資料插入快取的資料集，而不需啟動 Excel。

  雖然本逐步解說假設您是在開發電腦上執行程式碼，但本逐步解說所示範的程式碼可在未安裝 Excel 的伺服器上使用。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- Microsoft SQL Server 的執行中實例的存取權，或已附加 AdventureWorksLT 範例資料庫的 Microsoft SQL Server Express。 您可以從 [CodePlex 網站](https://archive.codeplex.com/?p=SqlServerSamples)下載 AdventureWorksLT 資料庫。 如需附加資料庫的詳細資訊，請參閱下列主題：

  - 若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱 [如何：附加資料庫 (SQL Server Management Studio) ](/sql/relational-databases/databases/attach-a-database)。

  - 若要使用命令列附加資料庫，請參閱 [如何：將資料庫檔案附加至 SQL Server Express](/previous-versions/sql/)。

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>建立定義資料集的類別庫專案
 若要在 Excel 活頁簿專案和主控台應用程式中使用相同的資料集，您必須在這兩個專案所參考的個別元件中定義該資料集。 針對此逐步解說，請在類別庫專案中定義資料集。

### <a name="to-create-the-class-library-project"></a>若要建立類別庫專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

3. 在 [範本] 窗格中，展開 [ **Visual c #** ] 或 [ **Visual Basic**]，然後按一下 [ **Windows**]。

4. 在專案範本清單中，選取 [ **類別庫**]。

5. 在 [ **名稱** ] 方塊中，輸入 **AdventureWorksDataSet**。

6. 按一下 **[流覽]**，流覽至適用于 windows XP 及更早版本的 *%UserProfile%\My 檔* () 或 windows Vista) 資料夾的 *%UserProfile%\Documents* (，然後按一下 [ **選取資料夾**]。

7. 在 [ **新增專案** ] 對話方塊中，確定未選取 [ **建立方案的目錄** ] 核取方塊。

8. 按一下 [確定]  。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將 **AdventureWorksDataSet** 專案加入 **方案總管** ，並開啟 **class1** 或 **class1** 程式碼檔案。

9. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **class1** ] 或 [ **class1**]，然後按一下 [ **刪除**]。 在此逐步解說中不需要此檔案。

## <a name="define-a-dataset-in-the-class-library-project"></a>在類別庫專案中定義資料集
 定義具類型的資料集，其中包含 SQL Server 2005 之 AdventureWorksLT 資料庫的資料。 稍後在此逐步解說中，您將從 Excel 活頁簿專案和主控台應用程式專案參考此資料集。

 資料集是具 *類型的資料集* ，代表 AdventureWorksLT 資料庫之 Product 資料表中的資料。 如需具類型資料集的詳細資訊，請參閱 [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>在類別庫專案中定義具類型的資料集

1. 在 **方案總管** 中，按一下 [ **AdventureWorksDataSet** ] 專案。

2. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。

3. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

4. 按一下 [ **資料庫**]，然後按 [ **下一步**]。

5. 如果您已有與 AdventureWorksLT 資料庫的連線，請選擇此連接，然後按 **[下一步]**。

    否則，請按一下 [新增連接] ，然後使用 [加入連接]  對話方塊建立新的連接。 如需詳細資訊，請參閱 [如何：連接至資料庫中的資料](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)。

6. 在 [將連接字串儲存到應用程式組態檔]  頁面上，按 [下一步] 。

7. 在 [ **選擇您的資料庫物件** ] 頁面中，展開 [ **資料表]** ，然後選取 [ **Product (SalesLT)**。

8. 按一下 [完成] 。

    *Adventureworksltdataset.xsd .xsd* 檔案會新增至 **AdventureWorksDataSet** 專案。 這個檔案會定義下列項目：

   - 具類型資料集，名稱為 `AdventureWorksLTDataSet`。 此資料集會表示 AdventureWorksLT 資料庫中 Product 資料表的內容。

   - 名為的 TableAdapter `ProductTableAdapter` 。 此 TableAdapter 可以用來讀取和寫入中的資料 `AdventureWorksLTDataSet` 。 如需詳細資訊，請參閱 [TableAdapter 總覽](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

     您將在本逐步解說稍後用到這兩個物件。

9. 在 **方案總管** 中，以滑鼠右鍵按一下 **AdventureWorksDataSet** ，然後按一下 [ **建立**]。

     確認專案建置無誤。

## <a name="create-an-excel-workbook-project"></a>建立 Excel 活頁簿專案
 為數據的介面建立 Excel 活頁簿專案。 稍後在這個逐步解說中，您將會建立， <xref:Microsoft.Office.Tools.Excel.ListObject> 它會顯示資料，而且您會將資料集的實例加入至活頁簿中的資料快取。

### <a name="to-create-the-excel-workbook-project"></a>若要建立 Excel 活頁簿專案

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **AdventureWorksDataSet** 方案，指向 [ **加入**]，然後按一下 [ **新增專案**]。

2. 在範本窗格中，展開 [Visual C#] **Deploying Office Solutions** 或 [Visual Basic] ，然後展開 [Office/SharePoint] 。

3. 在展開的 [Office/SharePoint]  節點下，選取 [Office 增益集]  節點。

4. 在專案範本清單中，選取 [Excel 2010 活頁簿]  或 [Excel 2013 活頁簿]  專案。

5. 在 [ **名稱** ] 方塊中，輸入 **AdventureWorksReport**。 請勿修改位置。

6. 按一下 [確定]  。

     隨即開啟 [Visual Studio Tools for Office 專案精靈]  。

7. 確定已選取 [ **建立新檔** ]，然後按一下 **[確定]**。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 在設計工具中開啟 **AdventureWorksReport** 活頁簿，並將 **AdventureWorksReport** 專案新增至 **方案總管**。

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>將資料集新增至 Excel 活頁簿專案中的資料來源
 在 Excel 活頁簿中顯示資料集之前，您必須先將資料集加入至 Excel 活頁簿專案中的資料來源。

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>若要將資料集加入至 Excel 活頁簿專案中的資料來源

1. 在 **方案總管** 中，按兩下 [ **AdventureWorksReport** ] 專案底下的 [ **sheet1** ] 或 [ **sheet1** ]。

     活頁簿會在設計工具中開啟。

2. 在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

     [ **資料來源設定]** 設定會開啟。

3. 按一下 [ **物件**]，然後按 **[下一步]**。

4. 在 [ **選取您** 要系結的物件] 頁面中，按一下 [ **加入參考**]。

5. 在 [ **專案** ] 索引標籤上，按一下 [ **AdventureWorksDataSet** ]，然後按一下 **[確定]**。

6. 在 **AdventureWorksDataSet** 元件的 **AdventureWorksDataSet** 命名空間底下，按一下 [ **Adventureworksltdataset.xsd** ]，然後按一下 **[完成]**。

     [ **資料來源** ] 視窗隨即開啟，並將 **adventureworksltdataset.xsd** 新增至資料來源清單。

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>建立系結至資料集實例的 ListObject
 若要在活頁簿中顯示資料集，請建立系結 <xref:Microsoft.Office.Tools.Excel.ListObject> 至資料集實例的。 如需將控制項系結至資料的詳細資訊，請參閱將資料系結至 [Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>若要建立系結至資料集實例的 ListObject

1. 在 [**資料來源**] 視窗中，展開 [ **AdventureWorksDataSet**] 底下的 [ **adventureworksltdataset.xsd** ] 節點。

2. 選取 [ **產品** ] 節點，並按一下出現的下拉箭號，然後選取下拉式清單中的 [ **ListObject** ]。

     如果下拉式箭號未出現，請確認已在設計工具中開啟活頁簿。

3. 將 [ **Product** ] 資料表拖曳到儲存格 A1。

     <xref:Microsoft.Office.Tools.Excel.ListObject> `productListObject` 工作表上會建立名為的控制項（從儲存格 A1 開始）。 同時間，名為 `adventureWorksLTDataSet` 的資料集物件，和名為 <xref:System.Windows.Forms.BindingSource> 的 `productBindingSource` 會加入專案。 <xref:Microsoft.Office.Tools.Excel.ListObject> 已繫結至 <xref:System.Windows.Forms.BindingSource>，而後者又繫結至資料集物件。

## <a name="add-the-dataset-to-the-data-cache"></a>將資料集新增至資料快取
 若要讓 Excel 活頁簿專案以外的程式碼存取活頁簿中的資料集，您必須將資料集加入至資料快取。 如需資料快取的詳細資訊，請參閱 [檔層級自訂](../vsto/cached-data-in-document-level-customizations.md) 和快取 [資料](../vsto/caching-data.md)中的快取資料。

### <a name="to-add-the-dataset-to-the-data-cache"></a>將資料集新增至資料快取

1. 在設計工具中，按一下 [ **adventureworksltdataset.xsd**]。

2. 在 [ **屬性** ] 視窗中， **將 [修飾** 詞] 屬性設定為 [ **公用**]。

3. 將 **CacheInDocument** 屬性設定為 **True**。

## <a name="checkpoint"></a>Checkpoint
 建立並執行 Excel 活頁簿專案，以確保它會在沒有錯誤的情況下進行編譯和執行。

### <a name="to-build-and-run-the-project"></a>若要建置及執行專案

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **AdventureWorksReport** 專案，選擇 [ **Debug**]，然後按一下 [ **開始新實例**]。

     隨即建立專案，並在 Excel 中開啟活頁簿。 <xref:Microsoft.Office.Tools.Excel.ListObject> **Sheet1** 中的是空的，因為資料快取 `adventureWorksLTDataSet` 中的物件尚未包含任何資料。 在下一節中，您將使用主控台應用程式，將 `adventureWorksLTDataSet` 資料填入物件中。

2. 關閉 Excel。 請勿儲存變更。

## <a name="create-a-console-application-project"></a>建立主控台應用程式專案
 建立主控台應用程式專案，用來將資料插入活頁簿中的快取資料集。

### <a name="to-create-the-console-application-project"></a>建立主控台應用程式專案

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **AdventureWorksDataSet** 方案，指向 [ **加入**]，然後按一下 [ **新增專案**]。

2. 在 [ **專案類型** ] 窗格中，展開 [ **Visual c #** ] 或 [ **Visual Basic**]，然後按一下 [ **Windows**]。

3. 在 **[範本]** 窗格中，選取 **[主控台應用程式]**。

4. 在 [ **名稱** ] 方塊中，輸入 **>datawriter**。 請勿修改位置。

5. 按一下 [確定]  。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]將 >datawriter 專案加入 **方案總管**，並開啟 **程式 .Cs** 或 **的** 程式碼檔案。

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>使用主控台應用程式將資料新增至快取的資料集
 使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 主控台應用程式中的類別，在活頁簿中將資料填入快取的資料集。

### <a name="to-add-data-to-the-cached-dataset"></a>若要將資料加入至快取的資料集

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **>datawriter** 專案，然後按一下 [ **加入參考**]。

2. 在 [ **.net** ] 索引標籤上，選取 [ **VisualStudio] ServerDocument**。

3. 按一下 [確定]  。

4. 在 **方案總管** 中，以滑鼠右鍵按一下 **>datawriter** 專案，然後按一下 [ **加入參考**]。

5. 在 [ **專案** ] 索引標籤上，選取 [ **AdventureWorksDataSet**]，然後按一下 **[確定]**。

6. 在程式碼編輯器中開啟 *程式 .cs* 或 *Module1* 檔案。

7. **使用** c # 的 (新增下列程式 ) ，或將 Visual Basic) 語句的 (匯 **入** 至程式碼檔案頂端。

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. 將下列程式碼新增至 `Main` 方法。 此程式碼會宣告下列物件：

   - 和類型的實例，這些實例 `AdventureWorksLTDataSet` `ProductTableAdapter` 是在 **AdventureWorksDataSet** 專案中定義。

   - AdventureWorksReport 活頁簿在 **AdventureWorksReport** 專案的組建資料夾中的路徑。

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>用來存取活頁簿中資料快取的物件。

     > [!NOTE]
     > 下列程式碼假設您使用副檔名為 *.xlsx* 的活頁簿。 如果您專案中的活頁簿具有不同的副檔名，請視需要修改路徑。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet3":::

9. 將下列程式碼新增至 `Main` 方法，在您于上一個步驟中新增的程式碼之後。 此程式碼會執行下列工作：

   - 它會使用表格介面卡來填滿具類型的資料集物件。

   - 它會使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 類別的屬性 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 來存取活頁簿中的快取資料集。

   - 它會使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法，將來自區域具類型資料集的資料填入快取的資料集。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet4":::

10. 在 **方案總管** 中，以滑鼠右鍵按一下 **>datawriter** 專案，指向 [ **Debug**]，然後按一下 [ **開始新實例**]。

     已建立專案，而且當本機資料集填滿時，主控台應用程式會顯示數個狀態訊息，而當應用程式將資料儲存到活頁簿中的快取資料集時。 按 **Enter** 以關閉應用程式。

## <a name="test-the-workbook"></a>測試活頁簿
 當您開啟活頁簿時， <xref:Microsoft.Office.Tools.Excel.ListObject> 現在會顯示使用主控台應用程式加入至快取資料集的資料。

### <a name="to-test-the-workbook"></a>測試活頁簿

1. 如果仍然開啟，請關閉 Visual Studio 設計工具中的 AdventureWorksReport 活頁簿。

2. 在檔案總管中，開啟 **AdventureWorksReport** 專案的 [組建] 資料夾中的 AdventureWorksReport 活頁簿。 根據預設，組建資料夾會在下列其中一個位置：

    - 適用于 Windows XP 和舊版) 的 *%UserProfile%\My Documents\AdventureWorksReport\bin\Debug* (

    - 適用于 Windows Vista) 的 *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (

3. 確認在 <xref:Microsoft.Office.Tools.Excel.ListObject> 開啟活頁簿之後，已填入資料。

## <a name="next-steps"></a>下一步

您可以從下列主題深入瞭解如何使用快取的資料：

- 在不啟動 Excel 的情況下，變更快取資料集中的資料。 如需詳細資訊，請參閱 [逐步解說：變更伺服器上活頁簿中的](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)快取資料。

## <a name="see-also"></a>另請參閱

- [逐步解說：變更伺服器上活頁簿中的快取資料](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
