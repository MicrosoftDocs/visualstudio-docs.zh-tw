---
title: 查詢資料集
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0fb1310649a1aeba7fd46acf9277ef7ea5825472
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="query-datasets"></a>查詢資料集
若要搜尋特定的資料錄集中的資料，請使用 FindBy 方法在資料表上，撰寫迴圈時，資料表的資料列集合，或使用您自己 foreach 陳述式[LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)。

## <a name="dataset-case-sensitivity"></a>資料集區分大小寫
資料集內資料表和資料行名稱會依預設不區分大小寫，也就是資料集稱為 「 客戶 」 資料表可以也稱為 「 客戶 」。 這符合許多資料庫，包括 SQL Server 中的命名慣例。 SQL Server 中的預設行為是，不能只有大小寫辨別資料元素的名稱。

> [!NOTE]
>  不同的資料集，於 XML 文件不區分大小寫，因此，結構描述中定義的資料元素的名稱都會區分大小寫。 結構描述的通訊協定，例如允許定義名為 「 客戶 」 和名為 「 客戶 」。 不同資料表的資料表的結構描述 這可能會導致名稱衝突時的結構描述包含只有大小寫不同的項目用以產生資料集類別。

區分大小寫，不過，可以是如何解譯資料之資料集內的因素。 例如，如果您篩選資料集資料表中的資料，請搜尋準則可能會傳回根據比較是否區分大小寫不同的結果。 您可以控制的篩選、 搜尋和排序設定資料集的區分大小寫<xref:System.Data.DataSet.CaseSensitive%2A>屬性。 在資料集中的所有資料表預設會都繼承這個屬性的值。 (您可以藉由設定資料表的覆寫這個屬性的每個個別資料表<xref:System.Data.DataTable.CaseSensitive%2A>屬性。)

## <a name="locate-a-specific-row-in-a-data-table"></a>在資料表中尋找特定的資料列

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>尋找列在具有主索引鍵值的具類型資料集

-   若要尋找資料列，呼叫強型別`FindBy`使用資料表的主索引鍵的方法。

     在下列範例中，`CustomerID`資料行是主索引鍵`Customers`資料表。 這表示，產生`FindBy`方法`FindByCustomerID`。 此範例示範如何指派特定<xref:System.Data.DataRow>使用所產生變數`FindBy`方法。

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>尋找不具類型資料集與主索引鍵值的資料列

-   呼叫<xref:System.Data.DataRowCollection.Find%2A>方法<xref:System.Data.DataRowCollection>集合，做為參數傳遞的主索引鍵。

     下列範例示範如何宣告新的資料列呼叫`foundRow`並將其指派的傳回值<xref:System.Data.DataRowCollection.Find%2A>方法。 如果找到的主索引鍵，資料行索引 1 的內容會顯示在訊息方塊。

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>尋找資料列的資料行值

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>若要尋找任何資料行中的值為基礎的資料列

-   資料表會建立與<xref:System.Data.DataTable.Select%2A>方法，傳回的陣列<xref:System.Data.DataRow>s 根據運算式傳遞至<xref:System.Data.DataTable.Select%2A>方法。 建立有效的運算式的詳細資訊，請參閱頁面的 「 運算式的語法 」 一節，關於<xref:System.Data.DataColumn.Expression%2A>屬性。

     下列範例示範如何使用<xref:System.Data.DataTable.Select%2A>方法<xref:System.Data.DataTable>尋找特定的資料列。

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>存取相關的記錄
當資料集內的資料表相關時，<xref:System.Data.DataRelation>物件可以讓相關的記錄使用另一個資料表中。 例如，一個資料集，其中包含`Customers`和`Orders`資料表可以成為可用。

您可以使用<xref:System.Data.DataRelation>要尋找相關的記錄，藉由呼叫物件<xref:System.Data.DataRow.GetChildRows%2A>方法<xref:System.Data.DataRow>父資料表中。 這個方法會傳回相關的子記錄的陣列。 您可以呼叫<xref:System.Data.DataRow.GetParentRow%2A>方法<xref:System.Data.DataRow>子資料表中。 這個方法會傳回單一<xref:System.Data.DataRow>從父資料表。

此頁面會提供使用具類型資料集的範例。 瀏覽關聯性中不具類型資料集的相關資訊，請參閱[導覽 Datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations)。

> [!NOTE]
>  如果您是在 Windows Form 應用程式運作，而且使用的資料繫結功能，顯示資料，設計工具產生的表單，可能會提供足夠的功能，您的應用程式。 如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。 具體來說，請參閱[集中的關聯性](relationships-in-datasets.md)。

下列程式碼範例示範如何巡覽向上和向下中具類型資料集的關聯性。 程式碼範例使用具類型<xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) 和產生的 FindBy*PrimaryKey* (`FindByCustomerID`) 方法來找出所需的資料列，並傳回相關的記錄。 範例正確編譯和執行只有您具有：

-   名為資料集的執行個體`NorthwindDataSet`與`Customers`資料表。

-   `Orders`資料表。

-   名為的關聯性`FK_Orders_Customers`相關的兩個資料表。

此外，這兩個資料表需要填滿的任何記錄，要傳回的資料。

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>傳回子選取的父記錄的記錄

-   呼叫<xref:System.Data.DataRow.GetChildRows%2A>方法的特定`Customers`資料列，並傳回陣列中的資料列`Orders`資料表：

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>傳回所選取的子記錄的父記錄

-   呼叫<xref:System.Data.DataRow.GetParentRow%2A>方法的特定`Orders`資料列，並傳回單一資料列從`Customers`資料表：

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)