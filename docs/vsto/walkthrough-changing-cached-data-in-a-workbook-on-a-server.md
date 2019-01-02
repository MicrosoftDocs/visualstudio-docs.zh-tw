---
title: 逐步解說：變更伺服器的活頁簿中的快取的資料
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30f2c8576aaf26d2cb643327fb989d90a8964552
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804373"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>逐步解說：變更伺服器的活頁簿中的快取的資料
  本逐步解說示範如何修改 Microsoft Office Excel 活頁簿中快取不會啟動 Excel 所使用的資料集<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 這個逐步解說將說明下列工作：

- 定義包含在 AdventureWorksLT 資料庫中的資料的資料集。

- 在 Excel 活頁簿專案] 和 [主控台應用程式專案中建立資料集的執行個體。

- 建立<xref:Microsoft.Office.Tools.Excel.ListObject>已繫結至活頁簿中的資料集並填入<xref:Microsoft.Office.Tools.Excel.ListObject>時開啟的活頁簿的資料。

- 新增活頁簿中的資料集，資料快取。

- 執行主控台應用程式中的程式碼，而不啟動 Excel，以修改快取的資料集內的資料行。

  雖然本逐步解說假設您的開發電腦上執行的程式碼，本逐步解說所示範的程式碼可用並沒有 Excel 安裝在伺服器上。

> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   存取權的 Microsoft SQL Server 或 Microsoft SQL Server Express 具有附加的 AdventureWorksLT 範例資料庫執行個體。 您可以下載 AdventureWorksLT 資料庫，從[CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843)。 如需附加資料庫的詳細資訊，請參閱下列主題：

    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱[How to:附加資料庫 (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database)。

    -   若要使用命令列附加資料庫，請參閱[How to:將資料庫檔案附加至 SQL Server Express](/previous-versions/sql/)。

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>建立定義資料集的類別庫專案
 若要使用相同的資料集的 Excel 活頁簿專案和主控台應用程式中，您必須定義資料集由兩個專案參考其他組件中。 此逐步解說中定義的類別庫專案中的資料集。

### <a name="to-create-the-class-library-project"></a>若要建立類別庫專案

1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

3.  在 [範本] 窗格中，依序展開**Visual C#** 或是**Visual Basic**，然後按一下**Windows**。

4.  在專案範本清單中，選取**類別庫**。

5.  在 **名稱**方塊中，輸入**AdventureWorksDataSet**。

6.  按一下 **瀏覽**，瀏覽至您 *%UserProfile%\My Documents* （適用於 Windows XP 及更早版本） 或 *%UserProfile%\Documents* （適用於 Windows Vista) 資料夾，然後再按一下**選取資料夾**。

7.  在 **新的專案**對話方塊方塊中，請確認**為方案建立目錄**核取方塊未選取。

8.  按一下 [確定 **Deploying Office Solutions**]。

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

    否則，請按一下 [ **新增連接**]，然後使用 [ **加入連接** ] 對話方塊建立新的連接。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。

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

1.  在**方案總管 中**，以滑鼠右鍵按一下**AdventureWorksDataSet**方案，指向**新增**，然後按一下**新專案**。

2.  在 [範本] 窗格中，依序展開**Visual C#** 或是**Visual Basic**，然後展開**Office**。

3.  下展開**辦公室**節點中，選取**2010年**節點。

4.  在專案範本清單中，選取 Excel 活頁簿專案。

5.  在 **名稱**方塊中，輸入**AdventureWorksReport**。 請勿修改的位置。

6.  按一下 [確定 **Deploying Office Solutions**]。

     隨即開啟 [Visual Studio Tools for Office 專案精靈]  。

7.  請確認**建立新的文件**已選取，然後按一下**確定**。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會開啟**AdventureWorksReport**設計工具中的活頁簿，並將**AdventureWorksReport**專案加入**方案總管 中**。

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>將資料集加入至 Excel 活頁簿專案中的資料來源
 您可以在 Excel 活頁簿中顯示資料集之前，您必須先將資料集加入 Excel 活頁簿專案中的資料來源。

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>若要將資料集加入至 Excel 活頁簿專案中的資料來源

1.  在 **方案總管**，按兩下**Sheet1.cs**或**Sheet1.vb**下**AdventureWorksReport**專案。

     在設計工具中開啟活頁簿。

2.  在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

     [資料來源組態精靈] 隨即開啟。

3.  按一下 [**物件**，然後按一下**下一步]**。

4.  在 **選取您要繫結至物件**頁面上，按一下**加入參考**。

5.  在上**專案**索引標籤上，按一下**AdventureWorksDataSet** ，然後按一下 **確定**。

6.  底下**AdventureWorksDataSet**命名空間**AdventureWorksDataSet**組件中，按一下  **AdventureWorksLTDataSet** ，然後按一下 **完成**.

     **資料來源**視窗隨即開啟，並**AdventureWorksLTDataSet**加入至資料來源的清單。

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>建立繫結至資料集執行個體的清單物件
 若要顯示活頁簿中的資料集，請建立<xref:Microsoft.Office.Tools.Excel.ListObject>，繫結至資料集執行個體。 如需控制項繫結至資料的詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>若要建立繫結至資料集執行個體的清單物件

1.  在 [**資料來源**] 視窗中，展開**AdventureWorksLTDataSet**節點底下**AdventureWorksDataSet**。

2.  選取 **產品**節點中，按一下下拉式箭號，隨即出現，並選取**ListObject**下拉式清單中。

     如果未出現的下拉式箭號，確認在設計工具中開啟活頁簿。

3.  拖曳**產品**A1 儲存格的資料表。

     A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為`productListObject`上的工作表中，然後再啟動儲存格 A1 中建立。 同時間，名為 `adventureWorksLTDataSet` 的資料集物件，和名為 <xref:System.Windows.Forms.BindingSource> 的 `productBindingSource` 會加入專案。 <xref:Microsoft.Office.Tools.Excel.ListObject> 已繫結至 <xref:System.Windows.Forms.BindingSource>，而後者又繫結至資料集物件。

## <a name="add-the-dataset-to-the-data-cache"></a>將資料集加入至資料快取
 若要啟用外部存取活頁簿中的資料集的 Excel 活頁簿專案的程式碼，您必須新增資料集的資料快取。 如需有關資料快取的詳細資訊，請參閱[快取文件層級自訂中的資料](../vsto/cached-data-in-document-level-customizations.md)並[快取資料](../vsto/caching-data.md)。

### <a name="to-add-the-dataset-to-the-data-cache"></a>若要加入的資料快取中的資料集

1.  在設計工具中，按一下**adventureWorksLTDataSet**。

2.  在 **屬性**視窗中，將**修飾詞**屬性設**公用**。

3.  設定**CacheInDocument**屬性設 **，則為 True**。

## <a name="initialize-the-dataset-in-the-workbook"></a>初始化活頁簿中的資料集
 您也可以使用主控台應用程式從快取的資料集擷取資料之前，您必須先將資料填入快取的資料集的資料。

### <a name="to-initialize-the-dataset-in-the-workbook"></a>將活頁簿中的資料集

1.  在 **方案總管**，以滑鼠右鍵按一下**Sheet1.cs**或**Sheet1.vb**檔案，然後按一下 **檢視程式碼**。

2.  以下列程式碼取代 `Sheet1_Startup` 事件處理常式。 此程式碼使用的執行個體`ProductTableAdapter`中所定義的類別**AdventureWorksDataSet**專案要使用資料，填入快取的資料集，如果它目前是空的。

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>檢查點
 建置並執行 Excel 活頁簿專案，以確保它會編譯並執行無誤。 這項作業也會填滿快取的資料集，並將資料儲存在活頁簿中。

### <a name="to-build-and-run-the-project"></a>若要建置及執行專案

1.  中**方案總管**，以滑鼠右鍵按一下**AdventureWorksReport**專案中，選擇 **偵錯**，然後按一下**開始新執行個體**。

     建置專案時，並在 Excel 中開啟活頁簿。 驗證下列各項：

    -   <xref:Microsoft.Office.Tools.Excel.ListObject>填入資料。

    -   中的值**ListPrice**的第一個資料列的資料行<xref:Microsoft.Office.Tools.Excel.ListObject>是 1431.5。 稍後在本逐步解說中，您將使用的主控台應用程式來修改中的值**ListPrice**資料行。

2.  儲存活頁簿。 請勿修改的檔案名稱或活頁簿的位置。

3.  關閉 Excel。

## <a name="create-a-console-application-project"></a>建立主控台應用程式專案
 建立主控台應用程式專案，用以修改活頁簿中快取的資料集內的資料。

### <a name="to-create-the-console-application-project"></a>若要建立主控台應用程式專案

1.  在**方案總管 中**，以滑鼠右鍵按一下**AdventureWorksDataSet**方案，指向**新增**，然後按一下**新專案**。

2.  在 [**專案類型**] 窗格中，展開**Visual C#** 或**Visual Basic**，然後按一下**Windows**。

3.  在 **範本**窗格中，選取**主控台應用程式**。

4.  在 **名稱**方塊中，輸入**資料寫入元**。 請勿修改的位置。

5.  按一下 [確定 **Deploying Office Solutions**]。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**資料寫入元**專案加入**方案總管** ，並開啟**Program.cs**或是**Module1.vb**程式碼檔案。

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>使用主控台應用程式來變更快取的資料集內的資料
 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別中的主控台應用程式，以將資料讀入本機`AdventureWorksLTDataSet`物件，修改這項資料，然後將它儲存回快取的資料集。

### <a name="to-change-data-in-the-cached-dataset"></a>若要變更快取的資料集內的資料

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下**資料寫入元**專案，然後按一下**加入參考**。

2. 在  **.NET**索引標籤上，選取**Microsoft.VisualStudio.Tools.Applications**。

3. 按一下 [確定 **Deploying Office Solutions**]。

4. 在 [**方案總管] 中**，以滑鼠右鍵按一下**資料寫入元**專案，然後按一下**加入參考**。

5. 在上**專案**索引標籤上，選取**AdventureWorksDataSet**，然後按一下**確定**。

6. 開啟*Program.cs*或是*Module1.vb*檔案在程式碼編輯器。

7. 新增下列**使用**（適用於 C#) 或**匯入**（適用於 Visual Basic) 陳述式的程式碼檔案頂端。

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. 將下列程式碼加入至 `Main` 方法。 此程式碼會宣告下列物件：

   - 執行個體`AdventureWorksLTDataSet`中所定義的型別**AdventureWorksDataSet**專案。

   - AdventureWorksReport 活頁簿中的 [組建] 資料夾的路徑**AdventureWorksReport**專案。

   - A<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>物件，用來存取活頁簿中的資料快取。

     > [!NOTE]
     >  下列程式碼假設您使用具有的活頁簿 *.xlsx*副檔名。 如果您的專案中的活頁簿會有不同的檔案副檔名，修改視的路徑。

     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]

9. 將下列程式碼加入`Main`方法中，您在上一個步驟中新增的程式碼之後。 這個程式碼會執行下列工作：

   - 它會使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別來存取活頁簿中快取的資料集。

   - 它會從快取的資料集讀取資料到本機的資料集。

   - 它會變更`ListPrice`每項產品的資料集之 Product 資料表中的值。

   - 它會將變更儲存至活頁簿中快取的資料集。

     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]

10. 在 **方案總管 中**，以滑鼠右鍵按一下**資料寫入元**專案，指向**偵錯**，然後按一下 **開始新執行個體**。

     它會讀取快取的資料集到本機的資料集、 修改產品價格，在本機的資料集，並將新的值儲存至快取的資料集時，主控台應用程式就會顯示訊息。 按下**Enter**關閉應用程式。

## <a name="test-the-workbook"></a>測試活頁簿
 當您開啟活頁簿<xref:Microsoft.Office.Tools.Excel.ListObject>現在會顯示您對所做的變更`ListPrice`中快取的資料集的資料行。

### <a name="to-test-the-workbook"></a>若要測試的活頁簿

1.  它是否仍保持開啟，請關閉 AdventureWorksReport 活頁簿，在 Visual Studio 設計工具中。

2.  開啟 AdventureWorksReport 活頁簿中的 [組建] 資料夾**AdventureWorksReport**專案。 根據預設，[組建] 資料夾是在下列位置：

    -   *%UserProfile%\My Documents\AdventureWorksReport\bin\Debug* （適用於 Windows XP 及更早版本）

    -   *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* （適用於 Windows Vista)

3.  確認中的值**ListPrice**的第一個資料列的資料行<xref:Microsoft.Office.Tools.Excel.ListObject>現 1574.65。

4.  關閉活頁簿。

## <a name="see-also"></a>另請參閱

- [逐步解說：在伺服器上的活頁簿中插入資料](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)