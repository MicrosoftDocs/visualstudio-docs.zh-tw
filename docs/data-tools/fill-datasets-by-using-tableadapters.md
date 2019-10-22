---
title: 使用 TableAdapter 填入資料集
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fcecafaa36aabf3249bacf0788c2d19f945ad1b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648481"
---
# <a name="fill-datasets-by-using-tableadapters"></a>使用 TableAdapter 填入資料集

TableAdapter 元件會根據您指定的一或多個查詢或預存程式，將資料庫中的資料填入資料集。 Tableadapter 也可以在資料庫上執行加入、更新和刪除，以保存您對資料集所做的變更。 您也可以發出與任何特定資料表無關的全域命令。

> [!NOTE]
> Tableadapter 是由 Visual Studio 設計工具產生。 如果您要以程式設計方式建立資料集，請使用 DataAdapter，這是 .NET 類別。

如需有關 TableAdapter 作業的詳細資訊，您可以直接跳到下列其中一個主題：

|主題|描述|
|-----------|-----------------|
|[建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|如何使用設計工具來建立及設定 Tableadapter|
|[建立參數型 TableAdapter 查詢](../data-tools/create-parameterized-tableadapter-queries.md)|如何讓使用者提供 TableAdapter 程式或查詢的引數|
|[以 TableAdapter 直接存取資料庫](../data-tools/directly-access-the-database-with-a-tableadapter.md)|如何使用 Tableadapter 的 Dbdirect 方法|
|[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|更新資料時如何使用外鍵條件約束|
|[如何擴充 TableAdapter 的功能](../data-tools/fill-datasets-by-using-tableadapters.md)|如何將自訂程式碼新增至 Tableadapter|
|[將 XML 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md)|如何使用 XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter 概觀

Tableadapter 是設計工具產生的元件，可連接至資料庫、執行查詢或預存程式，並以傳回的資料填入其 DataTable。 Tableadapter 也會將更新的資料從您的應用程式傳送回資料庫。 您可以視需要在 TableAdapter 上執行任意數目的查詢，只要它們傳回的資料符合與 TableAdapter 相關聯之資料表的架構即可。 下圖顯示 Tableadapter 如何與記憶體中的資料庫和其他物件互動：

![用戶端應用程式中的資料流程](../data-tools/media/clientdatadiagram.gif)

雖然 Tableadapter 是使用**DataSet 設計工具**所設計，但 TableAdapter 類別並不會產生為 <xref:System.Data.DataSet> 的嵌套類別。 它們位於每個資料集特有的個別命名空間中。 例如，如果您有一個名為 `NorthwindDataSet` 的資料集，則與 `NorthwindDataSet` 中 <xref:System.Data.DataTable>s 相關聯的 Tableadapter 會在 `NorthwindDataSetTableAdapters` 命名空間中。 若要以程式設計方式存取特定的 TableAdapter，您必須宣告 TableAdapter 的新實例。 例如:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>相關聯的 DataTable 架構

當您建立 TableAdapter 時，您會使用初始查詢或預存程式來定義 TableAdapter 相關聯 <xref:System.Data.DataTable> 的架構。 您可以藉由呼叫 TableAdapter 的 `Fill` 方法（它會填入 TableAdapter 相關聯的 <xref:System.Data.DataTable>），來執行這個初始查詢或預存程式。 對 TableAdapter 的主查詢進行的任何變更都會反映在相關聯之資料表的架構中。 例如，從主要查詢中移除資料行時，也會從相關聯的資料表中移除資料行。 如果 TableAdapter 上的任何其他查詢使用 SQL 語句來傳回不在主要查詢中的資料行，則設計工具會嘗試同步處理主要查詢與其他查詢之間的資料行變更。

## <a name="tableadapter-update-commands"></a>TableAdapter 更新命令

TableAdapter 的更新功能取決於**Tableadapter Wizard**的主要查詢中有多少可用的資訊。 例如，設定為從多個資料表提取值的 Tableadapter （使用 `JOIN`）、純量值、views 或彙總函式的結果，一開始並不會有將更新傳回基礎資料庫的能力。 不過，您可以在 [**屬性**] 視窗中，手動設定 `INSERT`、`UPDATE` 和 `DELETE` 命令。

## <a name="tableadapter-queries"></a>TableAdapter 查詢

![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif)

Tableadapter 可以包含多個查詢，以填滿其相關聯的資料表。 只要每個查詢傳回的資料符合與其相關聯的資料表相同的架構，您就可以定義 TableAdapter 的查詢，如同您的應用程式所需。 這項功能可讓 TableAdapter 根據不同的準則載入不同的結果。

例如，如果您的應用程式包含具有客戶名稱的資料表，您可以建立一個查詢，以使用以特定字母開頭的每個客戶名稱來填滿資料表，另一個則會在資料表中填入相同狀態的所有客戶。 若要在具有給定狀態的客戶中填入 `Customers` 資料表，您可以建立一個 `FillByState` 查詢，其接受狀態值的參數，如下所示： `SELECT * FROM Customers WHERE State = @State`。 您可以藉由呼叫 `FillByState` 方法來執行查詢，並傳入參數值，如下所示： `CustomerTableAdapter.FillByState("WA")`。

除了加入查詢，以傳回與 TableAdapter 資料表相同之架構的資料，您還可以加入傳回純量（單一）值的查詢。 例如，傳回客戶計數的查詢（`SELECT Count(*) From Customers`）對 `CustomersTableAdapter,` 有效，即使傳回的資料不符合資料表的架構也一樣。

## <a name="clearbeforefill-property"></a>ClearBeforeFill 屬性

根據預設，每次您執行查詢來填滿 TableAdapter 的資料表時，就會清除現有的資料，而且只會將查詢的結果載入資料表。 如果您想要將查詢所傳回的資料，加入或合併到資料表中的現有資料，請將 TableAdapter 的 `ClearBeforeFill` 屬性設定為 [`false`]。 不論您是否清除資料，如果您想要保存更新，則需要明確地將更新傳送回資料庫。 因此，在執行另一個填入資料表的查詢之前，請記得先儲存資料表中資料的任何變更。 如需詳細資訊，請參閱[使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。

## <a name="tableadapter-inheritance"></a>TableAdapter 繼承

Tableadapter 會封裝已設定的 <xref:System.Data.Common.DataAdapter> 類別，以擴充標準資料介面卡的功能。 根據預設，TableAdapter 會繼承自 <xref:System.ComponentModel.Component> 類別，而且無法轉換成 <xref:System.Data.Common.DataAdapter> 類別。 將 TableAdapter 轉換成 <xref:System.Data.Common.DataAdapter> 類別會導致 <xref:System.InvalidCastException> 錯誤。 若要變更 TableAdapter 的基類，您可以在**DataSet 設計工具**的 TableAdapter 的**基類**屬性中，指定衍生自 <xref:System.ComponentModel.Component> 的類別。

## <a name="tableadapter-methods-and-properties"></a>TableAdapter 方法和屬性

TableAdapter 類別不是 .NET 型別。 這表示您無法在檔或**物件瀏覽器**中查閱它。 當您使用稍早所述的其中一個嚮導時，就會在設計階段建立此檔案。 建立時指派給 TableAdapter 的名稱是以您要使用的資料表名稱為基礎。 例如，當您根據名為 `Orders` 的資料庫中的資料表建立 TableAdapter 時，會將 TableAdapter 命名為 `OrdersTableAdapter`。 您可以使用**DataSet 設計工具**中的**name**屬性來變更 TableAdapter 的類別名稱。

以下是 Tableadapter 常用的方法和屬性：

|成員|描述|
|------------|-----------------|
|`TableAdapter.Fill`|使用 TableAdapter 的 `SELECT` 命令的結果，填入 TableAdapter 的相關聯資料表。|
|`TableAdapter.Update`|將變更傳送回資料庫，並傳回代表受更新影響之資料列數目的整數。 如需詳細資訊，請參閱[使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。|
|`TableAdapter.GetData`|傳回填入資料的新 <xref:System.Data.DataTable>。|
|`TableAdapter.Insert`|在資料表中建立新的資料列。 如需詳細資訊，請參閱[在資料庫中插入新記錄](../data-tools/insert-new-records-into-a-database.md)。|
|`TableAdapter.ClearBeforeFill`|在您呼叫其中一個 `Fill` 方法之前，判斷資料表是否已清空。|

## <a name="tableadapter-update-method"></a>TableAdapter 更新方法

Tableadapter 使用資料命令來讀取及寫入資料庫。 使用 TableAdapter 的初始 `Fill` （main）查詢做為建立相關聯資料表之架構的基礎，以及與 `TableAdapter.Update` 方法相關聯的 `InsertCommand`、`UpdateCommand` 和 `DeleteCommand` 命令。 呼叫 TableAdapter 的 `Update` 方法，會執行原本已設定 TableAdapter 時所建立的語句，而不是您使用 [ **TableAdapter 查詢設定] Wizard**新增的其中一個額外查詢。

當您使用 TableAdapter 時，它會有效地使用您通常會執行的命令來執行相同的作業。 例如，當您呼叫介面卡的 `Fill` 方法時，介面卡會在其 `SelectCommand` 屬性中執行資料命令，並使用資料讀取器（例如 <xref:System.Data.SqlClient.SqlDataReader>）將結果集載入至資料表。 同樣地，當您呼叫介面卡的 `Update` 方法時，它會針對資料表中每個已變更的記錄，執行適當的命令（在 [`UpdateCommand`]、[`InsertCommand`] 和 [`DeleteCommand` 屬性] 中）。

> [!NOTE]
> 如果主要查詢中有足夠的資訊，則在產生 TableAdapter 時，預設會建立 `InsertCommand`、`UpdateCommand` 和 `DeleteCommand` 命令。 如果 TableAdapter 的主查詢不是單一資料表 `SELECT` 語句，則設計工具可能無法產生 `InsertCommand`、`UpdateCommand` 和 `DeleteCommand`。 如果未產生這些命令，當您執行 `TableAdapter.Update` 方法時，可能會收到錯誤。

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

除了 `InsertCommand`、`UpdateCommand` 和 `DeleteCommand` 之外，也會使用您可以直接對資料庫執行的方法來建立 Tableadapter。 您可以直接呼叫這些方法（`TableAdapter.Insert`、`TableAdapter.Update` 和 `TableAdapter.Delete`），以運算元據庫中的資料。 這表示您可以從程式碼呼叫這些個別方法，而不是呼叫 `TableAdapter.Update` 來處理針對關聯資料表暫止的插入、更新和刪除。

如果您不想要建立這些直接方法，請將 TableAdapter 的**GenerateDbDirectMethods**屬性設定為 `false` （在 [**屬性**] 視窗中）。 新增至 TableAdapter 的其他查詢是獨立查詢，它們不會產生這些方法。

## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter 支援可為 null 的類型

Tableadapter 支援可為 null 的類型 `Nullable(Of T)` 和 `T?`。 如需 Visual Basic 可為 Null 型別的詳細資訊，請參閱[可為 Null 的實值類型](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)。 如需中C#可為 null 之類型的詳細資訊，請參閱[使用可為 null 的類型](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)。

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 參考

根據預設，當您建立包含相關資料表的資料集時，TableAdapterManager 類別會產生。 若要防止產生類別，請將資料集的 [`Hierarchical Update`] 屬性值變更為 [false]。 當您將具有關聯性的資料表拖曳至 Windows Form 或 WPF 頁面的設計介面時，Visual Studio 會宣告類別的成員變數。 如果您不使用資料系結，就必須手動宣告變數。

TableAdapterManager 類別不是 .NET 型別。 因此，您無法在檔中查閱。 它是在設計階段建立，做為資料集建立過程的一部分。

以下是 `TableAdapterManager` 類別的常用方法和屬性：

|成員|描述|
|------------|-----------------|
|`UpdateAll` 方法|儲存所有資料表的所有資料。|
|`BackUpDataSetBeforeUpdate` 屬性|決定在執行 `TableAdapterManager.UpdateAll` 方法之前，是否要建立資料集的備份複本。True.|
|*tableName* `TableAdapter` 屬性|代表 TableAdapter。 產生的 TableAdapterManager 包含其所管理之每個 `TableAdapter` 的屬性。 例如，具有 Customers 和 Orders 資料表的資料集會產生包含 `CustomersTableAdapter` 和 `OrdersTableAdapter` 屬性的 TableAdapterManager。|
|`UpdateOrder` 屬性|控制個別 insert、update 和 delete 命令的順序。 將此設定為 `TableAdapterManager.UpdateOrderOption` 列舉中的其中一個值。<br /><br /> 根據預設，`UpdateOrder` 會設定為**InsertUpdateDelete**。 這表示會針對資料集內的所有資料表執行插入、更新和刪除作業。|

## <a name="security"></a>安全性

當您使用 CommandType 屬性設定為 <xref:System.Data.CommandType.Text> 的資料命令時，請仔細檢查從用戶端傳送的資訊，再將它傳遞至您的資料庫。 惡意的使用者可能會嘗試傳送 (插入) 修改過或額外的 SQL 陳述式，以獲得未授權的存取權或藉此破壞資料庫。 將使用者輸入傳送至資料庫之前，請務必確認該資訊是否有效。 最佳做法是盡可能使用參數化查詢或預存程式。

## <a name="see-also"></a>請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
