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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ccd8bd0cb37aaa2d4bfad7ea20979987048bf862
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050669"
---
# <a name="query-datasets"></a>查詢資料集
若要搜尋的資料集內的特定記錄，請使用`FindBy`datatable，方法撰寫您自己的 foreach 陳述式，以使用迴圈處理資料表的資料列集合，或使用[LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)。

## <a name="dataset-case-sensitivity"></a>資料集區分大小寫
資料集，資料表和資料行名稱會依預設不區分大小寫 — 也就是資料集稱為 「 客戶 」 資料表可以也稱為 「 客戶 」。 這會比對多個資料庫，包括 SQL Server 中的命名慣例。 在 SQL Server 的預設行為會是資料元素的名稱不能進行區分大小寫。

> [!NOTE]
>  不同的資料集，於 XML 文件都區分大小寫，因此結構描述中定義的資料元素的名稱會區分大小寫。 例如，結構描述的通訊協定可讓要定義名為 「 客戶 」 並建立名為 「 客戶。 」 的不同資料表的資料表的結構描述 當結構描述，其中包含只有大小寫不同的元素用來產生資料集類別，這會導致名稱衝突。

區分大小寫，不過，可能會如何解譯資料之資料集內的因素。 例如，如果您篩選資料集資料表中的資料，請搜尋條件可能會傳回根據比較是否區分大小寫不同的結果。 您可以控制的篩選、 搜尋和排序資料集設為區分大小寫<xref:System.Data.DataSet.CaseSensitive%2A>屬性。 在資料集中的所有資料表預設會都繼承這個屬性的值。 (您可以設定資料表的連線，覆寫這個屬性為每個個別的資料表<xref:System.Data.DataTable.CaseSensitive%2A>屬性。)

## <a name="locate-a-specific-row-in-a-data-table"></a>在資料表中找出特定的資料列

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>若要尋找在具類型的資料集與主索引鍵值的資料列

- 若要尋找資料列，呼叫強型別`FindBy`使用資料表的主索引鍵的方法。

     在下列範例中，`CustomerID`資料行是主索引鍵`Customers`資料表。 這表示，產生`FindBy`方法是`FindByCustomerID`。 此範例示範如何指派特定<xref:System.Data.DataRow>使用 產生變數`FindBy`方法。

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>若要尋找的資料列中含有主索引鍵值的不具類型資料集

- 呼叫<xref:System.Data.DataRowCollection.Find%2A>方法的<xref:System.Data.DataRowCollection>集合，做為參數傳遞的主索引鍵。

     下列範例示範如何宣告新的資料列，呼叫`foundRow`並將其指派的傳回值<xref:System.Data.DataRowCollection.Find%2A>方法。 如果找到的主索引鍵，則資料行索引 1 的內容會顯示在訊息方塊。

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>尋找資料列的資料行值

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>若要尋找任何資料行的值為基礎的資料列

- 使用建立資料表<xref:System.Data.DataTable.Select%2A>方法，以傳回的陣列<xref:System.Data.DataRow>s 根據運算式傳遞至<xref:System.Data.DataTable.Select%2A>方法。 建立有效的運算式的詳細資訊，請參閱頁面的 「 運算式的語法 」 一節，關於<xref:System.Data.DataColumn.Expression%2A>屬性。

     下列範例示範如何使用<xref:System.Data.DataTable.Select%2A>方法的<xref:System.Data.DataTable>找出特定的資料列。

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>存取相關的記錄
當資料集內的資料表彼此相關時，<xref:System.Data.DataRelation>物件可以提供相關的記錄另一個資料表中。 例如，一個資料集，其中包含`Customers`和`Orders`資料表可以成為可用。

您可以使用<xref:System.Data.DataRelation>物件，以找出相關的記錄，藉由呼叫<xref:System.Data.DataRow.GetChildRows%2A>方法<xref:System.Data.DataRow>父資料表中。 這個方法會傳回相關的子記錄的陣列。 或者，您可以呼叫<xref:System.Data.DataRow.GetParentRow%2A>方法的<xref:System.Data.DataRow>子資料表中。 這個方法會傳回單一<xref:System.Data.DataRow>父資料表中。

此頁面提供使用具類型資料集的範例。 瀏覽關聯性中不具類型資料集的相關資訊，請參閱[巡覽 Datarelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations)。

> [!NOTE]
>  如果您是在 Windows Forms 應用程式中，而且顯示的資料使用的資料繫結功能，設計工具所產生的表單可能會提供足夠的功能，您的應用程式。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。 具體來說，請參閱 <<c0> [ 中的資料集的關聯性](relationships-in-datasets.md)。

下列程式碼範例示範如何瀏覽向上和向下中具類型資料集的關聯性。 程式碼範例使用具類型<xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) 和產生的 FindBy*PrimaryKey* (`FindByCustomerID`) 方法，以找出所需的資料列，並傳回相關的記錄。 範例正確編譯和執行只有當您擁有：

- 名為資料集的執行個體`NorthwindDataSet`與`Customers`資料表。

- `Orders`資料表。

- 名為的關聯性`FK_Orders_Customers`相關的兩個資料表。

此外，這兩個資料表需要填滿要傳回的任何記錄的資料。

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>傳回子系的已選取的父記錄的記錄

- 呼叫<xref:System.Data.DataRow.GetChildRows%2A>方法的特定`Customers`資料列，並傳回陣列中的資料列`Orders`資料表：

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>傳回所選的子記錄的父記錄

- 呼叫<xref:System.Data.DataRow.GetParentRow%2A>方法的特定`Orders`資料列，並傳回單一資料列從`Customers`資料表：

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)