---
title: 逐步解說： 將資料插入到之伺服器上的活頁簿 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7257094aa0fb29c1b03878f5ac39c3d4f4864022
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-inserting-data-into-a-workbook-on-a-server"></a>逐步解說：在伺服器的活頁簿中插入資料
  本逐步解說示範如何將資料插入的資料集，在 Microsoft Office Excel 活頁簿中快取不會啟動 Excel 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   定義包含有提供 AdventureWorksLT 資料庫中的資料的資料集。  
  
-   在 Excel 活頁簿專案和主控台應用程式專案中建立資料集的執行個體。  
  
-   建立<xref:Microsoft.Office.Tools.Excel.ListObject>活頁簿中的資料集繫結。  
  
-   加入活頁簿中的資料集，讓資料快取。  
  
-   將資料插入至快取的資料集執行主控台應用程式中的程式碼，而不啟動 Excel。  
  
 雖然本逐步解說假設您在開發電腦上執行程式碼，但是本逐步解說所示範的程式碼可以使用未安裝 Excel 的伺服器上。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Microsoft SQL Server 或 Microsoft SQL Server Express 已有提供 AdventureWorksLT 範例資料庫附加到它的執行個體的存取。 您可以下載 AdventureWorksLT 資料庫從[CodePlex 網站上](http://go.microsoft.com/fwlink/?linkid=87843)。 如需附加資料庫的詳細資訊，請參閱下列主題：  
  
    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱 [如何：附加資料庫 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)。  
  
    -   若要使用命令列附加資料庫，請參閱 [如何：將資料庫檔案附加到 SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>建立類別庫專案來定義資料集  
 若要使用相同的資料集的 Excel 活頁簿專案和主控台應用程式中，您必須在不同的組件所參考的兩個專案中定義資料集。 對於此逐步解說，請在類別庫專案中定義資料集。  
  
#### <a name="to-create-the-class-library-project"></a>若要建立類別庫專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
3.  在 範本 窗格中，依序展開**Visual C#**或**Visual Basic**，然後按一下  **Windows**。  
  
4.  在專案範本清單中選取**類別庫**。  
  
5.  在**名稱**方塊中，輸入**AdventureWorksDataSet**。  
  
6.  按一下**瀏覽**，巡覽至您 %UserProfile%\My 文件 （Windows XP 及更早版本） 或 （適用於 Windows Vista) %UserProfile%\Documents 資料夾，然後按一下**選取資料夾**。  
  
7.  在**新專案**對話方塊方塊中，確定**為方案建立目錄**未選取核取方塊。  
  
8.  按一下 [確定 **Deploying Office Solutions**]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**AdventureWorksDataSet**專案加入**方案總管 中**並開啟**Class1.cs**或**Class1.vb**程式碼檔案。  
  
9. 在**方案總管] 中**，以滑鼠右鍵按一下**Class1.cs**或**Class1.vb**，然後按一下 [**刪除**。 這個逐步解說不需要此檔案。  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>類別庫專案中定義的資料集  
 定義具類型的資料集，其中包含適用於 SQL Server 2005 AdventureWorksLT 資料庫中的資料。 稍後在本逐步解說中，您將參考此資料集的 Excel 活頁簿專案和主控台應用程式專案。  
  
 資料集是*具類型資料集*代表 AdventureWorksLT 資料庫之 Product 資料表中的資料。 如需具類型資料集的詳細資訊，請參閱[Visual Studio 中的資料集工具](/visualstudio/data-tools/dataset-tools-in-visual-studio)。  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>若要定義類別庫專案中的具類型資料集  
  
1.  在**方案總管] 中**，按一下 [ **AdventureWorksDataSet**專案。  
  
2.  如果看不到 [ **資料來源** ] 視窗，請在功能表列選擇 [ **檢視**]、[ **其他視窗**]、[ **資料來源**] 即可顯示。  
  
3.  選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。  
  
4.  按一下 [ **資料庫**]，然後按 [ **下一步**]。  
  
5.  如果您有現有的連接與 AdventureWorksLT 資料庫，請選擇這個連線，然後按一下**下一步**。  
  
     否則，請按一下 [ **新增連接**]，然後使用 [ **加入連接** ] 對話方塊建立新的連接。 如需詳細資訊，請參閱[如何： 連接到資料庫中的資料](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)。  
  
6.  在 [將連接字串儲存到應用程式組態檔]  頁面上，按 [下一步] 。  
  
7.  在**選擇您的資料庫物件**頁面上，展開**資料表**選取**Product (SalesLT)**。  
  
8.  按一下 [ **完成**]。  
  
     AdventureWorksLTDataSet.xsd 檔案加入至**AdventureWorksDataSet**專案。 這個檔案會定義下列項目：  
  
    -   具類型資料集，名稱為 `AdventureWorksLTDataSet`。 此資料集代表 AdventureWorksLT 資料庫中的 Product 資料表的內容。  
  
    -   名為 TableAdapter `ProductTableAdapter`。 此 TableAdapter 可以用來讀取和寫入資料`AdventureWorksLTDataSet`。 如需詳細資訊，請參閱 [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。  
  
     您將在本逐步解說稍後用到這兩個物件。  
  
9. 在**方案總管 中**，以滑鼠右鍵按一下**AdventureWorksDataSet**按一下**建置**。  
  
     確認專案建置無誤。  
  
## <a name="creating-an-excel-workbook-project"></a>建立 Excel 活頁簿專案  
 建立 Excel 活頁簿專案資料的介面。 稍後在本逐步解說，您將建立<xref:Microsoft.Office.Tools.Excel.ListObject>，會顯示資料，以及您將會加入活頁簿中的資料快取中的資料集的執行個體。  
  
#### <a name="to-create-the-excel-workbook-project"></a>若要建立 Excel 活頁簿專案  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**AdventureWorksDataSet**方案，指向**新增**，然後按一下 [**新專案**。  
  
2.  在範本窗格中，展開 [Visual C#] **Deploying Office Solutions** 或 [Visual Basic] ，然後展開 [Office/SharePoint] 。  
  
3.  在展開的 [Office/SharePoint] **Deploying Office Solutions** 節點下，選取 [Office 增益集]  節點。  
  
4.  在專案範本清單中，選取 [Excel 2010 活頁簿]  或 [Excel 2013 活頁簿]  專案。  
  
5.  在**名稱**方塊中，輸入**AdventureWorksReport**。 請勿修改的位置。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
     隨即開啟 [Visual Studio Tools for Office 專案精靈]  。  
  
7.  請確認**建立新的文件**已選取，然後按一下**確定**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 開啟**AdventureWorksReport**設計工具中的活頁簿，並將**AdventureWorksReport**專案加入**方案總管 中**。  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>將資料集加入至 Excel 活頁簿專案中的資料來源  
 您可以在 Excel 活頁簿中顯示資料集之前，您必須先將資料集加入 Excel 活頁簿專案中的資料來源。  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>若要將資料集加入至 Excel 活頁簿專案中的資料來源  
  
1.  在**方案總管 中**，連按兩下**Sheet1.cs**或**Sheet1.vb**下**AdventureWorksReport**專案。  
  
     在設計工具中開啟活頁簿。  
  
2.  在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。  
  
     **資料來源組態精靈**隨即開啟。  
  
3.  按一下**物件**，然後按一下 **下一步**。  
  
4.  在**選取您要繫結物件**頁面上，請按一下 **加入參考**。  
  
5.  在**專案**索引標籤上，按一下  **AdventureWorksDataSet** ，然後按一下 **確定**。  
  
6.  在下**AdventureWorksDataSet**命名空間的**AdventureWorksDataSet**組件中，按一下**AdventureWorksLTDataSet** ，然後按一下 **完成**.  
  
     **資料來源**視窗隨即開啟，並**AdventureWorksLTDataSet**加入至資料來源的清單。  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>建立清單物件繫結至資料集的執行個體  
 若要顯示活頁簿中的資料集，請建立<xref:Microsoft.Office.Tools.Excel.ListObject>繫結至資料集的執行個體。 如需將控制項繫結至資料的詳細資訊，請參閱 [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>若要建立 ListObject 繫結至資料集的執行個體  
  
1.  在**資料來源**視窗中，展開  **AdventureWorksLTDataSet**節點下的**AdventureWorksDataSet**。  
  
2.  選取**產品**節點中，按一下下拉式箭號，隨即出現，並選取**ListObject**下拉式清單中。  
  
     如果未出現下拉箭號，確認活頁簿是在設計工具中開啟。  
  
3.  拖曳**產品**表格儲存格 A1。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為`productListObject`建立在工作表中儲存格 A1 中啟動。 同時間，名為 `adventureWorksLTDataSet` 的資料集物件，和名為 `productBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 會加入專案。 <xref:Microsoft.Office.Tools.Excel.ListObject> 會繫結至 <xref:System.Windows.Forms.BindingSource>，而後者則繫結至資料集物件。  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>將資料集加入至資料快取  
 若要啟用存取活頁簿中的資料集在 Excel 活頁簿專案外的程式碼，您必須加入資料集的資料快取。 如需詳細資料快取的詳細資訊，請參閱[文件層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)和[快取資料](../vsto/caching-data.md)。  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>若要將資料快取的資料集  
  
1.  在設計工具中，按一下**adventureWorksLTDataSet**。  
  
2.  在**屬性**視窗中，將**修飾詞**屬性**公用**。  
  
3.  設定**CacheInDocument**屬性**True**。  
  
## <a name="checkpoint"></a>檢查點  
 建置並執行 Excel 活頁簿專案，以確保它會編譯並執行無誤。  
  
#### <a name="to-build-and-run-the-project"></a>若要建置及執行專案  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**AdventureWorksReport**專案，選擇**偵錯**，然後按一下 [**開始新執行個體**。  
  
     建置專案，並在 Excel 中開啟活頁簿。 <xref:Microsoft.Office.Tools.Excel.ListObject>中**Sheet1**是空的因為`adventureWorksLTDataSet`資料快取中的物件尚未有任何資料。 在下一節中，您將使用的主控台應用程式以填入`adventureWorksLTDataSet`物件資料。  
  
2.  關閉 Excel。 不要儲存變更。  
  
## <a name="creating-a-console-application-project"></a>建立主控台應用程式專案  
 建立將資料插入活頁簿中快取的資料集所使用的主控台應用程式專案。  
  
#### <a name="to-create-the-console-application-project"></a>若要建立主控台應用程式專案  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**AdventureWorksDataSet**方案，指向**新增**，然後按一下 [**新專案**。  
  
2.  在**專案類型** 窗格中，展開  **Visual C#**或**Visual Basic**，然後按一下  **Windows**。  
  
3.  在**範本**窗格中，選取**主控台應用程式**。  
  
4.  在**名稱**方塊中，輸入**DataWriter**。 請勿修改的位置。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**DataWriter**專案加入**方案總管 中**並開啟**Program.cs**或**Module1.vb**程式碼檔案。  
  
## <a name="adding-data-to-the-cached-dataset-by-using-the-console-application"></a>使用主控台應用程式，將資料加入至快取的資料集  
 使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別中的主控台應用程式，以填入資料的活頁簿中的快取資料集。  
  
#### <a name="to-add-data-to-the-cached-dataset"></a>若要將資料加入至快取的資料集  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下**DataWriter**專案，然後按一下**加入參考**。  
  
2.  在**.NET**索引標籤上，選取**microsoft.visualstudio.tools.applications.serverdocument 的參考**。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。  
  
4.  在**方案總管 中**，以滑鼠右鍵按一下**DataWriter**專案，然後按一下**加入參考**。  
  
5.  在**專案**索引標籤上，選取**AdventureWorksDataSet**，然後按一下**確定**。  
  
6.  在程式碼編輯器中開啟 Program.cs 或 Module1.vb 檔案。  
  
7.  加入下列**使用**（適用於 C#) 或**匯入**（適用於 Visual Basic) 陳述式的程式碼檔案頂端。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  將下列程式碼加入至 `Main` 方法。 此程式碼會宣告下列物件：  
  
    -   執行個體`AdventureWorksLTDataSet`和`ProductTableAdapter`中所定義的型別**AdventureWorksDataSet**專案。  
  
    -   AdventureWorksReport 活頁簿中的組建資料夾的路徑**AdventureWorksReport**專案。  
  
    -   A<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>来用來存取活頁簿中的資料快取的物件。  
  
        > [!NOTE]  
        >  下列程式碼假設您使用副檔名為.xlsx 檔案的活頁簿。 如果您的專案中的活頁簿會有不同的檔案副檔名，修改視路徑。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]  
  
9. 將下列程式碼加入`Main`方法，您在上一個步驟中加入的程式碼之後。 這個程式碼會執行下列工作：  
  
    -   它會使用資料表配接器，填滿具類型資料集物件。  
  
    -   它會使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>屬性<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別來存取活頁簿中快取的資料集。  
  
    -   它會使用<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>填入本機的具類型資料集的資料快取的資料集的方法。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]  
  
10. 在**方案總管] 中**，以滑鼠右鍵按一下**DataWriter**專案，指向**偵錯**，然後按一下 [**開始新執行個體**。  
  
     建置專案，並填入本機的資料集，而且應用程式將資料儲存至活頁簿中快取的資料集時，主控台應用程式會顯示數個狀態訊息。 按 enter 鍵關閉應用程式。  
  
## <a name="testing-the-workbook"></a>測試活頁簿  
 當您開啟活頁簿，<xref:Microsoft.Office.Tools.Excel.ListObject>現在會顯示已加入使用主控台應用程式的快取的資料集的資料。  
  
#### <a name="to-test-the-workbook"></a>若要測試的活頁簿  
  
1.  如果，關閉 AdventureWorksReport 中的活頁簿 Visual Studio 設計工具中，它仍為開啟。  
  
2.  在 檔案總管 中，開啟 AdventureWorksReport 活頁簿中的組建資料夾**AdventureWorksReport**專案。 根據預設，組建資料夾是在下列位置：  
  
    -   %UserProfile%\My Documents\AdventureWorksReport\bin\Debug （Windows XP 及更早版本）  
  
    -   %UserProfile%\Documents\AdventureWorksReport\bin\Debug （適用於 Windows Vista)  
  
3.  確認<xref:Microsoft.Office.Tools.Excel.ListObject>開啟活頁簿之後，會填入資料。  
  
## <a name="next-steps"></a>後續步驟  
 您可以深入了解使用快取的資料，從下列主題：  
  
-   變更中快取的資料集的資料，而不啟動 Excel。 如需詳細資訊，請參閱[逐步解說： 變更伺服器上的活頁簿中快取的資料](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 變更伺服器上的活頁簿中快取的資料](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [連接至 Windows Forms 應用程式中的資料](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  