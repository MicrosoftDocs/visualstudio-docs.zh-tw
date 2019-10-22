---
title: 查詢資料集 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607442"
---
# <a name="query-datasets"></a>查詢資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要搜尋資料集中的特定記錄，請在 DataTable 上使用 FindBy 方法、在資料表的資料列集合上撰寫您自己的 foreach 迴圈，或使用[LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)。 LINQ to DataSet。

## <a name="dataset-case-sensitivity"></a>資料集區分大小寫
 在 dataset 中，資料表和資料行名稱預設不區分大小寫，也就是說，名為「Customers」的資料集內的資料表也可以稱為「客戶」。 這符合許多資料庫中的命名慣例，包括 SQL Server.In SQL Server，預設行為是資料元素的名稱不能只有大小寫區分。

> [!NOTE]
> 與資料集不同的是，XML 檔會區分大小寫，因此，在架構中定義的資料元素名稱會區分大小寫。 例如，架構通訊協定允許架構定義名為「Customers」的資料表，以及稱為「customers」的不同資料表。 當包含只有大小寫不同之專案的架構用來產生資料集類別時，這可能會導致名稱衝突。

 不過，區分大小寫，可以是資料在 dataset 內的轉譯方式的因素。 例如，如果您在資料集資料表中篩選資料，則根據比較是否區分大小寫，搜尋準則可能會傳回不同的結果。 您可以藉由設定資料集的 <xref:System.Data.DataSet.CaseSensitive%2A> 屬性，來控制篩選、搜尋和排序的區分大小寫。 資料集中的所有資料表預設都會繼承這個屬性的值。 （您可以藉由設定資料表的 <xref:System.Data.DataTable.CaseSensitive%2A> 屬性來覆寫每個個別資料表的這個屬性）。

## <a name="locate-a-specific-row-in-a-data-table"></a>找出資料表中的特定資料列

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>若要在具類型的資料集內尋找具有主鍵值的資料列

- 若要找出資料列，請呼叫使用資料表主鍵的強型別 `FindBy` 方法。

     在下列範例中，`CustomerID` 資料行是 `Customers` 資料表的主要索引鍵。 這表示會 `FindByCustomerID` 產生的 `FindBy` 方法。 此範例示範如何使用產生的 `FindBy` 方法，將特定 <xref:System.Data.DataRow> 指派給變數。

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>若要在具有主鍵值的不具類型資料集中尋找資料列

- 呼叫 <xref:System.Data.DataRowCollection> 集合的 <xref:System.Data.DataRowCollection.Find%2A> 方法，傳遞主要金鑰做為參數。

     下列範例示範如何宣告名為 `foundRow` 的新資料列，並將 <xref:System.Data.DataRowCollection.Find%2A> 方法的傳回值指派給它。 如果找到主要金鑰，則會在訊息方塊中顯示資料行索引1的內容。

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>依資料行值 Findrows

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>根據任何資料行中的值尋找資料列

- 資料表是使用 <xref:System.Data.DataTable.Select%2A> 方法所建立，它會根據傳遞給 <xref:System.Data.DataTable.Select%2A> 方法的運算式，傳回 <xref:System.Data.DataRow>s 的陣列。 如需建立有效運算式的詳細資訊，請參閱關於 <xref:System.Data.DataColumn.Expression%2A> 屬性之頁面的「運算式語法」一節。

     下列範例顯示如何使用 <xref:System.Data.DataTable> 的 <xref:System.Data.DataTable.Select%2A> 方法來尋找特定的資料列。

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>存取相關記錄
 當資料集內的資料表相關時，<xref:System.Data.DataRelation> 物件可以讓相關記錄在另一個資料表中提供。 例如，您可以使用包含 `Customers` 和 `Orders` 資料表的資料集。

 您可以藉由呼叫父資料表中 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRow.GetChildRows%2A> 方法，使用 <xref:System.Data.DataRelation> 物件來尋找相關記錄。這個方法會傳回相關的子記錄陣列。 或者，您可以在子資料工作表中呼叫 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRow.GetParentRow%2A> 方法。這個方法會從父資料表傳回單一 <xref:System.Data.DataRow>。

 此頁面提供使用具類型資料集的範例。 如需在不具類型的資料集中導覽關聯性的詳細資訊，請參閱[導覽 datarelation](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e)。

> [!NOTE]
> 如果您在 Windows Forms 應用程式中工作，並使用資料系結功能來顯示資料，則設計工具產生的表單可能會為您的應用程式提供足夠的功能。 如需詳細資訊，請參閱[將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

 下列程式碼範例示範如何在具類型的資料集中導覽和關閉關聯性。 程式碼範例會使用具類型的 <xref:System.Data.DataRow>s （`NorthwindDataSet.OrdersRow`）和產生的 `FindBy`*PrimaryKey* （`FindByCustomerID`）方法來找出所需的資料列，並傳回相關的記錄。 只有當您有下列情況時，範例才會編譯並執行正確：

- 具有 `Customers` 資料表且名為 `NorthwindDataSet` 之資料集的實例。

- @No__t_0 資料表。

- 名為的關聯性 `FK_Orders_Customers`relating 兩個可用於程式碼範圍的資料表

此外，這兩個數據表都必須填入資料，以供傳回任何記錄。

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>傳回所選父記錄的子記錄

- 呼叫特定 `Customers` 資料列的 <xref:System.Data.DataRow.GetChildRows%2A> 方法，並傳回 `Orders` 資料表中的資料列陣列：

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>傳回所選子記錄的父記錄

- 呼叫特定 `Orders` 資料列的 <xref:System.Data.DataRow.GetParentRow%2A> 方法，並從 `Customers` 資料表傳回單一資料列：

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
