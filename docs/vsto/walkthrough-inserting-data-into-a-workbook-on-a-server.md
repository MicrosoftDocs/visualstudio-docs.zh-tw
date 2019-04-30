---
title: 逐步解說：在伺服器上的活頁簿中插入資料
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: daf5251aa32f4101bfba21d053d72abceef1eb15
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440859"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>逐步解說：在伺服器上的活頁簿中插入資料
  本逐步解說示範如何將資料插入的資料集，Microsoft Office Excel 活頁簿中快取不會啟動 Excel 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 這個逐步解說將說明下列工作：

- 定義包含在 AdventureWorksLT 資料庫中的資料的資料集。

- 在 Excel 活頁簿專案] 和 [主控台應用程式專案中建立資料集的執行個體。

- 建立<xref:Microsoft.Office.Tools.Excel.ListObject>繫結至活頁簿中的資料集。

- 新增活頁簿中的資料集，資料快取。

- 將資料插入至快取的資料集執行主控台應用程式中的程式碼，而不啟動 Excel。

  雖然本逐步解說假設您的開發電腦上執行的程式碼，本逐步解說所示範的程式碼可用並沒有 Excel 安裝在伺服器上。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 存取權的 Microsoft SQL Server 或 Microsoft SQL Server Express 具有附加的 AdventureWorksLT 範例資料庫執行個體。 您可以下載 AdventureWorksLT 資料庫，從[CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843)。 如需附加資料庫的詳細資訊，請參閱下列主題：

    - 若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱[How to:附加資料庫 (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database)。

    - 若要使用命令列附加資料庫，請參閱[How to:將資料庫檔案附加至 SQL Server Express](/previous-versions/sql/)。

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>建立定義資料集的類別庫專案
 若要使用相同的資料集的 Excel 活頁簿專案和主控台應用程式中，您必須定義資料集由兩個專案參考其他組件中。 此逐步解說中定義的類別庫專案中的資料集。

### <a name="to-create-the-class-library-project"></a>若要建立類別庫專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

3. 在 [範本] 窗格中，依序展開**Visual C#** 或是**Visual Basic**，然後按一下**Windows**。

4. 在專案範本清單中，選取**類別庫**。

5. 在 **名稱**方塊中，輸入**AdventureWorksDataSet**。

6. 按一下 **瀏覽**，瀏覽至您 *%UserProfile%\My Documents* （適用於 Windows XP 及更早版本） 或 *%UserProfile%\Documents* （適用於 Windows Vista) 資料夾，然後再按一下**選取資料夾**。

7. 在 **新的專案**對話方塊方塊中，請確認**為方案建立目錄**核取方塊未選取。

8. 按一下 [確定] 。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**AdventureWorksDataSet**專案加入**方案總管** ，並開啟**Class1.cs**或是**Class1.vb**程式碼檔案。

9. 在 [**方案總管] 中**，以滑鼠右鍵按一下**Class1.cs**或**Class1.vb**，然後按一下**刪除**。 此逐步解說不需要此檔案。

## <a name="define-a-dataset-in-the-class-library-project"></a>類別庫專案中定義資料集
 定義具類型的資料集，其中包含適用於 SQL Server 2005 的 AdventureWorksLT 資料庫中的資料。 稍後在本逐步解說中，您將參考此資料集的 Excel 活頁簿專案和主控台應用程式專案。

 資料集*類型資料集*表示 AdventureWorksLT 資料庫之 Product 資料表中的資料。 如需有關具類型資料集的詳細資訊，請參閱 < [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>若要定義類別庫專案中的具類型資料集

1. 在 **方案總管**，按一下**AdventureWorksDataSet**專案。

2. 如果**資料來源**看不到視窗，顯示，請在功能表列選擇**檢視** > **其他 Windows**  >  **資料來源**。

3. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

4. 按一下 [ **資料庫**]，然後按 [ **下一步**]。

5. 如果您有現有的連線到 AdventureWorksLT 資料庫，請選擇此連線，然後按一下 [**下一步]**。

    否則，請按一下 [ **新增連接**]，然後使用 [ **加入連接** ] 對話方塊建立新的連接。 如需詳細資訊，請參閱[如何：連接到資料庫中的資料](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)。

6. 在 [將連接字串儲存到應用程式組態檔]  頁面上，按 [下一步] 。

7. 在 **選擇您的資料庫物件**頁面上，展開**資料表**，然後選取**Product (SalesLT)**。

8. 按一下 [ **完成**]。

    *AdventureWorksLTDataSet.xsd*檔案新增至**AdventureWorksDataSet**專案。 這個檔案會定義下列項目：

   - 具類型資料集，名稱為 `AdventureWorksLTDataSet`。 此資料集代表 AdventureWorksLT 資料庫中的 [Product] 資料表的內容。

   - 名為 TableAdapter `ProductTableAdapter`。 這個 TableAdapter 可用來讀取和寫入資料中`AdventureWorksLTDataSet`。 如需詳細資訊，請參閱 < [TableAdapter 概觀](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

     您將在本逐步解說稍後用到這兩個物件。

9. 在 **方案總管 中**，以滑鼠右鍵按一下**AdventureWorksDataSet** ，按一下 **建置**。

     確認專案建置無誤。

## <a name="create-an-excel-workbook-project"></a>建立 Excel 活頁簿專案
 建立 Excel 活頁簿專案資料的介面。 稍後在本逐步解說中，您將建立<xref:Microsoft.Office.Tools.Excel.ListObject>會顯示資料，並要將加入活頁簿中的資料快取中的資料集執行個體。

### <a name="to-create-the-excel-workbook-project"></a>若要建立 Excel 活頁簿專案

1. 在**方案總管 中**，以滑鼠右鍵按一下**AdventureWorksDataSet**方案，指向**新增**，然後按一下**新專案**。

2. 在範本窗格中，展開 **[Visual C#]** 或 **[Visual Basic]**，然後展開 **[Office/SharePoint]**。

3. 在展開的 [Office/SharePoint]  節點下，選取 [Office 增益集]  節點。

4. 在專案範本清單中，選取 [Excel 2010 活頁簿]  或 [Excel 2013 活頁簿]  專案。

5. 在 **名稱**方塊中，輸入**AdventureWorksReport**。 請勿修改的位置。

6. 按一下 [確定] 。

     隨即開啟 [Visual Studio Tools for Office 專案精靈]  。

7. 請確認**建立新的文件**已選取，然後按一下**確定**。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會開啟**AdventureWorksReport**設計工具中的活頁簿，並將**AdventureWorksReport**專案加入**方案總管 中**。

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>將資料集加入至 Excel 活頁簿專案中的資料來源
 您可以在 Excel 活頁簿中顯示資料集之前，您必須先將資料集加入 Excel 活頁簿專案中的資料來源。

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>若要將資料集加入至 Excel 活頁簿專案中的資料來源

1. 在 **方案總管**，按兩下**Sheet1.cs**或**Sheet1.vb**下**AdventureWorksReport**專案。

     在設計工具中開啟活頁簿。

2. 在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

     [資料來源組態精靈] 隨即開啟。

3. 按一下 [**物件**，然後按一下**下一步]**。

4. 在 **選取您要繫結物件**頁面上，按一下**加入參考**。

5. 在上**專案**索引標籤上，按一下**AdventureWorksDataSet** ，然後按一下 **確定**。

6. 底下**AdventureWorksDataSet**命名空間**AdventureWorksDataSet**組件中，按一下  **AdventureWorksLTDataSet** ，然後按一下 **完成**.

     **資料來源**視窗隨即開啟，並**AdventureWorksLTDataSet**加入至資料來源的清單。

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>建立繫結至資料集執行個體的清單物件
 若要顯示活頁簿中的資料集，請建立<xref:Microsoft.Office.Tools.Excel.ListObject>，繫結至資料集執行個體。 如需控制項繫結至資料的詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>若要建立繫結至資料集執行個體的清單物件

1. 在 [**資料來源**] 視窗中，展開**AdventureWorksLTDataSet**節點底下**AdventureWorksDataSet**。

2. 選取 **產品**節點中，按一下下拉式箭號，隨即出現，並選取**ListObject**下拉式清單中。

     如果未出現的下拉式箭號，確認在設計工具中開啟活頁簿。

3. 拖曳**產品**A1 儲存格的資料表。

     A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為`productListObject`上的工作表中，然後再啟動儲存格 A1 中建立。 同時間，名為 `adventureWorksLTDataSet` 的資料集物件，和名為 <xref:System.Windows.Forms.BindingSource> 的 `productBindingSource` 會加入專案。 <xref:Microsoft.Office.Tools.Excel.ListObject> 已繫結至 <xref:System.Windows.Forms.BindingSource>，而後者又繫結至資料集物件。

## <a name="add-the-dataset-to-the-data-cache"></a>將資料集加入至資料快取
 若要啟用外部存取活頁簿中的資料集的 Excel 活頁簿專案的程式碼，您必須新增資料集的資料快取。 如需有關資料快取的詳細資訊，請參閱[快取文件層級自訂中的資料](../vsto/cached-data-in-document-level-customizations.md)並[快取資料](../vsto/caching-data.md)。

### <a name="to-add-the-dataset-to-the-data-cache"></a>若要加入的資料快取中的資料集

1. 在設計工具中，按一下**adventureWorksLTDataSet**。

2. 在 **屬性**視窗中，將**修飾詞**屬性設**公用**。

3. 設定**CacheInDocument**屬性設 **，則為 True**。

## <a name="checkpoint"></a>檢查點
 建置並執行 Excel 活頁簿專案，以確保它會編譯並執行無誤。

### <a name="to-build-and-run-the-project"></a>若要建置及執行專案

1. 中**方案總管**，以滑鼠右鍵按一下**AdventureWorksReport**專案中，選擇 **偵錯**，然後按一下**開始新執行個體**。

     建置專案時，並在 Excel 中開啟活頁簿。 <xref:Microsoft.Office.Tools.Excel.ListObject>中**Sheet1**是空的因為`adventureWorksLTDataSet`資料快取中的物件尚未有任何資料。 在下一步 區段中，您將使用的主控台應用程式，來填入`adventureWorksLTDataSet`物件的資料。

2. 關閉 Excel。 不要儲存變更。

## <a name="create-a-console-application-project"></a>建立主控台應用程式專案
 建立將資料插入活頁簿中快取的資料集所使用的主控台應用程式專案。

### <a name="to-create-the-console-application-project"></a>若要建立主控台應用程式專案

1. 在**方案總管 中**，以滑鼠右鍵按一下**AdventureWorksDataSet**方案，指向**新增**，然後按一下**新專案**。

2. 在 [**專案類型**] 窗格中，展開**Visual C#** 或**Visual Basic**，然後按一下**Windows**。

3. 在 **範本**窗格中，選取**主控台應用程式**。

4. 在 **名稱**方塊中，輸入**資料寫入元**。 請勿修改的位置。

5. 按一下 [確定] 。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**資料寫入元**專案加入**方案總管** ，並開啟**Program.cs**或是**Module1.vb**程式碼檔案。

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>使用主控台應用程式，將資料新增至快取的資料集
 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>來填入快取的資料集與資料的活頁簿中的主控台應用程式中的類別。

### <a name="to-add-data-to-the-cached-dataset"></a>若要將資料加入至快取的資料集

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下**資料寫入元**專案，然後按一下**加入參考**。

2. 在  **.NET**索引標籤上，選取**microsoft.visualstudio.tools.applications.serverdocument 的參考**。

3. 按一下 [確定] 。

4. 在 [**方案總管] 中**，以滑鼠右鍵按一下**資料寫入元**專案，然後按一下**加入參考**。

5. 在上**專案**索引標籤上，選取**AdventureWorksDataSet**，然後按一下**確定**。

6. 開啟*Program.cs*或是*Module1.vb*檔案在程式碼編輯器。

7. 新增下列**使用**（適用於 C#) 或**匯入**（適用於 Visual Basic) 陳述式的程式碼檔案頂端。

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. 將下列程式碼加入至 `Main` 方法。 此程式碼會宣告下列物件：

   - 執行個體`AdventureWorksLTDataSet`並`ProductTableAdapter`中所定義的型別**AdventureWorksDataSet**專案。

   - AdventureWorksReport 活頁簿中的 [組建] 資料夾的路徑**AdventureWorksReport**專案。

   - A<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>物件，用來存取活頁簿中的資料快取。

     > [!NOTE]
     > 下列程式碼假設您使用具有的活頁簿 *.xlsx*副檔名。 如果您的專案中的活頁簿會有不同的檔案副檔名，修改視的路徑。

     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]

9. 將下列程式碼加入`Main`方法中，您在上一個步驟中新增的程式碼之後。 這個程式碼會執行下列工作：

   - 使用資料表配接器填入的具類型資料集物件。

   - 它會使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別來存取活頁簿中快取的資料集。

   - 它會使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>方法來填入快取的資料集，以從本機的具類型資料集的資料。

     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]

10. 在 **方案總管 中**，以滑鼠右鍵按一下**資料寫入元**專案，指向**偵錯**，然後按一下 **開始新執行個體**。

     建置專案時，並填入本機的資料集和應用程式會將資料儲存至活頁簿中快取的資料集時，主控台應用程式會顯示數個狀態訊息。 按下**Enter**關閉應用程式。

## <a name="test-the-workbook"></a>測試活頁簿
 當您開啟活頁簿，<xref:Microsoft.Office.Tools.Excel.ListObject>現在會顯示已加入使用主控台應用程式的快取的資料集的資料。

### <a name="to-test-the-workbook"></a>若要測試的活頁簿

1. 它是否仍保持開啟，請關閉 AdventureWorksReport 活頁簿，在 Visual Studio 設計工具中。

2. 在 檔案總管 中，開啟 AdventureWorksReport 活頁簿中的 組建 資料夾**AdventureWorksReport**專案。 根據預設，[組建] 資料夾是在下列位置：

    - *%UserProfile%\My Documents\AdventureWorksReport\bin\Debug* （適用於 Windows XP 及更早版本）

    - *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* （適用於 Windows Vista)

3. 確認<xref:Microsoft.Office.Tools.Excel.ListObject>開啟活頁簿之後，已填入資料。

## <a name="next-steps"></a>後續步驟

您可以深入了解使用快取的資料，從下列主題：

- 中的快取的資料集的資料變更而不啟動 Excel。 如需詳細資訊，請參閱[逐步解說：變更伺服器的活頁簿中的快取的資料](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：變更伺服器的活頁簿中的快取的資料](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)