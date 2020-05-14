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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302235"
---
# <a name="fill-datasets-by-using-tableadapters"></a>使用 TableAdapter 填入資料集

表配接器元件根據您指定的一個或多個查詢或預存程序，使用資料庫中的資料填充資料集。 表配接器還可以在資料庫上執行添加、更新和刪除，以保留對資料集所做的更改。 您還可以發出與任何特定表無關的全域命令。

> [!NOTE]
> 表配接器由視覺化工作室設計器生成。 如果要以程式設計方式創建資料集，請使用 DataAdapter，這是一個 .NET 類。

有關表配接器操作的詳細資訊，您可以直接跳到以下主題之一：

|主題|描述|
|-----------|-----------------|
|[建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|如何使用設計器創建和配置表配接器|
|[建立參數型 TableAdapter 查詢](../data-tools/create-parameterized-tableadapter-queries.md)|如何使使用者能夠向表配接器過程或查詢提供參數|
|[以 TableAdapter 直接存取資料庫](../data-tools/directly-access-the-database-with-a-tableadapter.md)|如何使用表配接器的 Dbdirect 方法|
|[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|更新資料時如何處理外鍵約束|
|[如何擴充 TableAdapter 的功能](../data-tools/fill-datasets-by-using-tableadapters.md)|如何向表配接器添加自訂代碼|
|[將 XML 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md)|如何使用 XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter 概觀

表配接器是設計器生成的元件，用於連接到資料庫、執行查詢或預存程序，並用返回的資料填充其 DataTable。 表配接器還會將更新的資料從應用程式發送回資料庫。 只要在表配接器上返回符合表配接器關聯的表的架構的資料，就可以在表配接器上運行所需的盡可能多的查詢。 下圖顯示了表配接器如何與記憶體中的資料庫和其他物件進行交互：

![用戶端應用程式中的資料流程](../data-tools/media/clientdatadiagram.gif)

雖然表配接器是使用**資料集設計器**設計的，但表配接器類不會生成為 嵌套類<xref:System.Data.DataSet>。 它們位於特定于每個資料集的單獨命名空間中。 例如，`NorthwindDataSet`如果資料集名為 ，則 與<xref:System.Data.DataTable>中的 s 關聯的表配接器`NorthwindDataSet`將位於命名空間中。 `NorthwindDataSetTableAdapters` 要以程式設計方式訪問特定的表配接器，必須聲明表配接器的新實例。 例如：

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>關聯的資料表架構

創建表配接器時，可以使用初始查詢或預存程序來定義表配接器關聯的<xref:System.Data.DataTable>架構。 通過調用表配接器`Fill`的方法（填充表配接器的關聯<xref:System.Data.DataTable>），運行此初始查詢或預存程序。 對表配接器的主查詢所做的任何更改都反映在關聯資料表的架構中。 例如，從主查詢中刪除列還會從關聯的資料表中刪除列。 如果表配接器上的任何其他查詢都使用返回不在主查詢中的列的 SQL 語句，則設計器將嘗試同步主查詢和其他查詢之間的列更改。

## <a name="tableadapter-update-commands"></a>表配接器更新命令

表配接器的更新功能取決於**表配接器嚮導**中主查詢中有多少資訊可用。 例如，配置為從多個表（使用`JOIN`）標量值、視圖或彙總函式的結果提取值的表配接器最初不會創建，並且能夠將更新發送回基礎資料庫。 但是，您可以在 **"屬性"** 視窗中`UPDATE`手動設定`DELETE``INSERT`和 命令。

## <a name="tableadapter-queries"></a>TableAdapter 查詢

![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif)

表配接器可以包含多個查詢來填充其關聯的資料表。 只要每個查詢返回與其關聯資料表相同的架構的資料，就可以根據應用程式的要求為表配接器定義盡可能多的查詢。 此功能使表配接器能夠根據不同的條件載入不同的結果。

例如，如果應用程式包含具有客戶名稱的表，則可以創建一個查詢，該查詢將表與以特定字母開頭的每個客戶名稱填充，另一個查詢將表與位於同一狀態的所有客戶填充。 要用給定`Customers`狀態的客戶填充表，可以創建一個`FillByState`查詢，該查詢獲取狀態值的參數，如下所示： `SELECT * FROM Customers WHERE State = @State`。 通過調用`FillByState`方法並傳入如下所示的參數值來執行查詢： `CustomerTableAdapter.FillByState("WA")`。

除了添加返回與表配接器的資料表相同的架構資料的查詢外，還可以添加返回標量（單個）值的查詢。 例如，返回客戶計數 （`SELECT Count(*) From Customers`） 的查詢對 有效，`CustomersTableAdapter,`即使返回的資料不符合表的架構。

## <a name="clearbeforefill-property"></a>清除之前填充屬性

預設情況下，每次執行查詢以填充表配接器的資料表時，都會清除現有資料，並且僅將查詢的結果載入到表中。 如果要將從查詢返回的資料`ClearBeforeFill`添加到資料`false`表中的現有資料，請將表配接器的屬性設置為。 無論您是否清除資料，如果需要保留更新，則需要顯式將更新發送回資料庫。 因此，請記住在運行另一個填充表的查詢之前保存對表中的資料的任何更改。 有關詳細資訊，請參閱[使用表配接器更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。

## <a name="tableadapter-inheritance"></a>表配接器繼承

表配接器通過封裝配置<xref:System.Data.Common.DataAdapter>的類來擴展標準資料配接器的功能。 預設情況下，表配接器從<xref:System.ComponentModel.Component>類繼承，不能強制轉換為<xref:System.Data.Common.DataAdapter>類。 將表配接器強制轉換到<xref:System.Data.Common.DataAdapter>類會導致錯誤<xref:System.InvalidCastException>。 要更改表配接器的基類，可以在<xref:System.ComponentModel.Component>**資料集設計器**中的表配接器**的基類**屬性中指定派生的類。

## <a name="tableadapter-methods-and-properties"></a>表配接器方法和屬性

表配接器類不是 .NET 類型。 這意味著您無法在文檔或**物件瀏覽器**中查找它。 它是在設計時創建的，當您使用前面提到的嚮導之一時。 創建表配接器時分配給它的名稱基於您正在使用的表的名稱。 例如，當您基於名為`Orders`的資料庫中的表時，表配接器名為`OrdersTableAdapter`。 可以使用**資料集設計器**中的**Name**屬性更改表配接器的類名稱。

以下是表配接器的常用方法和屬性：

|member|描述|
|------------|-----------------|
|`TableAdapter.Fill`|使用表配接器`SELECT`的命令結果填充表配接器的關聯資料表。|
|`TableAdapter.Update`|將更改發送回資料庫並返回表示受更新影響的行數的整數。 有關詳細資訊，請參閱[使用表配接器更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。|
|`TableAdapter.GetData`|返回充滿資料<xref:System.Data.DataTable>的新。|
|`TableAdapter.Insert`|在資料表中創建新行。 有關詳細資訊，請參閱[將新記錄插入資料庫](../data-tools/insert-new-records-into-a-database.md)。|
|`TableAdapter.ClearBeforeFill`|在調用其中一`Fill`種方法之前，確定資料表是否已清空。|

## <a name="tableadapter-update-method"></a>表配接器更新方法

表配接器使用資料命令從資料庫讀取和寫入。 使用 TableAdapter`Fill`的初始（主）查詢作為創建關聯資料表以及`InsertCommand`與`UpdateCommand``DeleteCommand``TableAdapter.Update`方法關聯的 的 的 和 命令的架構的基礎。 調用表配接器`Update`的方法運行最初配置表配接器時創建的語句，而不是使用**表配接器查詢設定精靈**添加的其他查詢之一。

使用表配接器時，它會使用通常執行的命令執行相同的操作。 例如，當您調用配接器`Fill`的方法時，配接器在其`SelectCommand`屬性中運行資料命令，<xref:System.Data.SqlClient.SqlDataReader>並使用資料讀取器（例如），將結果集載入到資料表中。 同樣，當您調用`Update`配接器的方法時，它會為數據表中的每個已更改的記錄運行相應的命令（`UpdateCommand`在`InsertCommand`和`DeleteCommand`屬性中）。

> [!NOTE]
> 如果主查詢中有足夠的資訊，則預設情況下生成表`InsertCommand`配接器`UpdateCommand`時將`DeleteCommand`創建 和 命令。 如果 TableAdapter 的主查詢不僅僅是單個`SELECT`表語句，則設計器可能無法生成`InsertCommand`和`UpdateCommand`。 `DeleteCommand` 如果未生成這些命令，則在運行`TableAdapter.Update`該方法時可能會收到錯誤。

## <a name="tableadapter-generatedbdirectmethods"></a>表配接器生成Dbdirect方法

除了`InsertCommand`，`UpdateCommand`和`DeleteCommand`， 表配接器是使用可以直接針對資料庫運行的方法創建的。 您可以直接調用這些方法 （`TableAdapter.Insert` `TableAdapter.Update`、`TableAdapter.Delete`和 ） 來運算元據庫中的資料。 這意味著可以從代碼調用這些單獨的方法，而不是調用`TableAdapter.Update`以處理關聯資料表掛起的插入、更新和刪除。

如果不想創建這些直接方法，請將表配接器的 **"生成DbDirect方法**"屬性設置為`false`（在 **"屬性"** 視窗中）。 添加到表配接器的其他查詢是獨立查詢 - 它們不會生成這些方法。

## <a name="tableadapter-support-for-nullable-types"></a>表配接器支援可消除類型

表配接器支援空類型`Nullable(Of T)`和`T?`。 如需 Visual Basic 可為 Null 型別的詳細資訊，請參閱[可為 Null 的實值類型](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)。 有關 C# 中可 null 類型的詳細資訊，請參閱[使用空類型](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)。

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>表配接器管理器引用

預設情況下，在創建包含相關表的資料集時，將生成表配接器管理器類。 為了防止生成類，將資料集`Hierarchical Update`的屬性的值更改為 false。 將具有關系的表拖動到 Windows 表單或 WPF 頁的設計介面上時，Visual Studio 將聲明類的成員變數。 如果不使用資料繫結，必須手動聲明變數。

表配接器管理器類不是 .NET 類型。 因此，您不能在文檔中查找它。 它是在設計時創建的，作為資料集創建過程的一部分。

以下是`TableAdapterManager`類的常用方法和屬性：

|member|描述|
|------------|-----------------|
|`UpdateAll` 方法|從所有資料表中保存所有資料。|
|`BackUpDataSetBeforeUpdate` 屬性|確定在執行`TableAdapterManager.UpdateAll`方法之前是否創建資料集的備份副本。布林。|
|*表名稱*`TableAdapter`屬性|代表 TableAdapter。 生成的表配接器管理器包含它管理的每個`TableAdapter`屬性。 例如，具有客戶和訂單表的資料集使用包含 和`CustomersTableAdapter``OrdersTableAdapter`屬性的表配接器管理器生成。|
|`UpdateOrder` 屬性|控制各個插入、更新和刪除命令的順序。 將此設置為枚舉中`TableAdapterManager.UpdateOrderOption`的值之一。<br /><br /> 預設情況下，`UpdateOrder`設置為**插入更新刪除**。 這意味著對資料集中的所有表執行插入、更新和刪除。|

## <a name="security"></a>安全性

將資料命令與 CommandType 屬性設置為<xref:System.Data.CommandType.Text>時，請仔細檢查從用戶端發送的資訊，然後再將其傳遞到資料庫。 惡意使用者可能會嘗試傳送 (插入) 修改過或額外的 SQL 陳述式，以獲得未授權的存取或破壞資料庫。 在將使用者輸入傳輸到資料庫之前，請始終驗證資訊是否有效。 最佳做法是盡可能始終使用參數化查詢或預存程序。

## <a name="see-also"></a>另請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
