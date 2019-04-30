---
title: 查詢資料集 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 69ca24f45384ef650c4a692a8ec0afc079f19bac
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425364"
---
# <a name="query-datasets"></a>查詢資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要搜尋的資料集內的特定記錄，使用 FindBy 方法 datatable、 撰寫您自己的 foreach 迴圈，對資料表的資料列集合，或使用[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)。 LINQ to DataSet。  
  
## <a name="dataset-case-sensitivity"></a>資料集區分大小寫  
 資料集，資料表和資料行名稱會依預設不區分大小寫 — 也就是資料集稱為 「 客戶 」 資料表可以也稱為 「 客戶 」。 這符合多個資料庫，包括 SQL 伺服器的 SQL Server 中的命名慣例，預設行為是資料元素的名稱不能進行區分大小寫。  
  
> [!NOTE]
> 不同的資料集，於 XML 文件都區分大小寫，因此結構描述中定義的資料元素的名稱會區分大小寫。 例如，結構描述的通訊協定可讓要定義名為 「 客戶 」 並建立名為 「 客戶。 」 的不同資料表的資料表的結構描述 當結構描述，其中包含只有大小寫不同的元素用來產生資料集類別，這會導致名稱衝突。  
  
 區分大小寫，不過，可能會如何解譯資料之資料集內的因素。 例如，如果您篩選資料集資料表中的資料，請搜尋條件可能會傳回根據比較是否區分大小寫不同的結果。 您可以控制的篩選、 搜尋和排序資料集設為區分大小寫<xref:System.Data.DataSet.CaseSensitive%2A>屬性。 在資料集中的所有資料表預設會都繼承這個屬性的值。 (您可以設定資料表的連線，覆寫這個屬性為每個個別的資料表<xref:System.Data.DataTable.CaseSensitive%2A>屬性。)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>在資料表中找出特定的資料列  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>若要尋找在具類型的資料集與主索引鍵值的資料列  
  
- 若要尋找資料列，呼叫強型別`FindBy`使用資料表的主索引鍵的方法。  
  
     在下列範例中，`CustomerID`資料行是主索引鍵`Customers`資料表。 這表示，產生`FindBy`方法是`FindByCustomerID`。 此範例示範如何指派特定<xref:System.Data.DataRow>使用 產生變數`FindBy`方法。  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>若要尋找的資料列中含有主索引鍵值的不具類型資料集  
  
- 呼叫<xref:System.Data.DataRowCollection.Find%2A>方法的<xref:System.Data.DataRowCollection>集合，做為參數傳遞的主索引鍵。  
  
     下列範例示範如何宣告新的資料列，呼叫`foundRow`並將其指派的傳回值<xref:System.Data.DataRowCollection.Find%2A>方法。 如果找到的主索引鍵，則資料行索引 1 的內容會顯示在訊息方塊。  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>Findrows 依資料行值  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>若要尋找任何資料行的值為基礎的資料列  
  
- 使用建立資料表<xref:System.Data.DataTable.Select%2A>方法，以傳回的陣列<xref:System.Data.DataRow>s 根據運算式傳遞至<xref:System.Data.DataTable.Select%2A>方法。 建立有效的運算式的詳細資訊，請參閱頁面的 「 運算式的語法 」 一節，關於<xref:System.Data.DataColumn.Expression%2A>屬性。  
  
     下列範例示範如何使用<xref:System.Data.DataTable.Select%2A>方法的<xref:System.Data.DataTable>找出特定的資料列。  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="access-related-records"></a>存取相關的記錄  
 當資料集內的資料表彼此相關時，<xref:System.Data.DataRelation>物件可以提供相關的記錄另一個資料表中。 例如，一個資料集，其中包含`Customers`和`Orders`資料表可以成為可用。  
  
 您可以使用<xref:System.Data.DataRelation>物件，以找出相關的記錄，藉由呼叫<xref:System.Data.DataRow.GetChildRows%2A>方法<xref:System.Data.DataRow>父資料表中。這個方法會傳回相關的子記錄的陣列。 您也可以呼叫<xref:System.Data.DataRow.GetParentRow%2A>方法的<xref:System.Data.DataRow>子資料表中。這個方法會傳回單一<xref:System.Data.DataRow>父資料表中。  
  
 此頁面提供使用具類型資料集的範例。 瀏覽關聯性中不具類型資料集的相關資訊，請參閱[巡覽 Datarelation](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e)。  
  
> [!NOTE]
> 如果您是在 Windows Forms 應用程式中，而且顯示的資料使用的資料繫結功能，設計工具所產生的表單可能會提供足夠的功能，您的應用程式。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
 下列程式碼範例示範如何瀏覽向上和向下中具類型資料集的關聯性。 程式碼範例使用具類型<xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) 並已產生`FindBy` *PrimaryKey* (`FindByCustomerID`) 方法，以找出所需的資料列，並傳回相關的記錄。 範例正確編譯和執行只有當您擁有：  
  
- 名為資料集的執行個體`NorthwindDataSet`與`Customers`資料表。  
  
- `Orders`資料表。  
  
- 名為的關聯性`FK_Orders_Customers`與可用的兩個資料表相關的程式碼範圍  
  
此外，這兩個資料表需要填滿要傳回的任何記錄的資料。  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>傳回子系的已選取的父記錄的記錄  
  
- 呼叫<xref:System.Data.DataRow.GetChildRows%2A>方法的特定`Customers`資料列，並傳回陣列中的資料列`Orders`資料表：  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>傳回所選的子記錄的父記錄  
  
- 呼叫<xref:System.Data.DataRow.GetParentRow%2A>方法的特定`Orders`資料列，並傳回單一資料列從`Customers`資料表：  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
