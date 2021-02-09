---
title: 使用 TableAdapter 填入資料集
description: 使用 Tableadapter 填滿資料集。 TableAdapter 元件會根據您指定的一或多個查詢或預存程式，以資料庫中的資料填入資料集。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 8037b8d19bad19485e9ed8f7926e6a3e45b8fef1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866901"
---
# <a name="fill-datasets-by-using-tableadapters"></a>使用 TableAdapter 填入資料集

TableAdapter 元件會根據您指定的一或多個查詢或預存程式，使用資料庫中的資料來填滿資料集。 Tableadapter 也可以在資料庫上執行新增、更新和刪除，以保存您對資料集所做的變更。 您也可以發出與任何特定資料表無關的全域命令。

> [!NOTE]
> Tableadapter 由 Visual Studio 的設計師產生。 如果您要以程式設計方式建立資料集，請使用 DataAdapter，也就是 .NET 類別。

如需有關 TableAdapter 作業的詳細資訊，您可以直接跳到下列其中一個主題：

|主題|描述|
|-----------|-----------------|
|[建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|如何使用設計工具來建立和設定 Tableadapter|
|[建立參數型 TableAdapter 查詢](../data-tools/create-parameterized-tableadapter-queries.md)|如何讓使用者提供引數給 TableAdapter 程式或查詢|
|[以 TableAdapter 直接存取資料庫](../data-tools/directly-access-the-database-with-a-tableadapter.md)|如何使用 Tableadapter 的 Dbdirect 方法|
|[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|如何在更新資料時使用外鍵條件約束|
|[如何擴充 TableAdapter 的功能](../data-tools/fill-datasets-by-using-tableadapters.md)|如何將自訂程式碼新增至 Tableadapter|
|[將 XML 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md)|如何使用 XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter 概觀

Tableadapter 是由設計工具產生的元件，可連接到資料庫、執行查詢或預存程式，並以傳回的資料填入其 DataTable。 Tableadapter 也會將更新的資料從您的應用程式傳送回資料庫。 您可以視需要在 TableAdapter 上執行多個查詢，只要它們傳回的資料符合與 TableAdapter 相關聯之資料表的架構。 下圖顯示 Tableadapter 如何與記憶體中的資料庫和其他物件互動：

![用戶端應用程式中的資料流程](../data-tools/media/clientdatadiagram.gif)

雖然 Tableadapter 是使用 **DataSet 設計工具** 所設計，但 TableAdapter 類別不會產生為的嵌套類別  <xref:System.Data.DataSet> 。 它們位於個別的命名空間中，每個資料集都有特定的命名空間。 例如，如果您有一個名為的資料集 `NorthwindDataSet` ，則中與的相關聯的 tableadapter 會  <xref:System.Data.DataTable> `NorthwindDataSet` 在 `NorthwindDataSetTableAdapters` 命名空間中。 若要以程式設計方式存取特定的 TableAdapter，您必須宣告 TableAdapter 的新實例。 例如：

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>相關聯的 DataTable 架構

當您建立 TableAdapter 時，您會使用初始查詢或預存程式來定義 TableAdapter 相關聯的架構 <xref:System.Data.DataTable> 。 您可以藉由呼叫 TableAdapter 的方法 (來執行此初始查詢或預存程式， `Fill` 以填滿 TableAdapter 的相關 <xref:System.Data.DataTable>) 。 對 TableAdapter 的主要查詢所做的任何變更，都會反映在相關聯資料表的架構中。 例如，從主要查詢移除資料行也會從相關聯的資料表中移除資料行。 如果 TableAdapter 上的任何額外查詢都使用傳回不在主要查詢中之資料行的 SQL 語句，則設計工具會嘗試同步處理主要查詢與其他查詢之間的資料行變更。

## <a name="tableadapter-update-commands"></a>TableAdapter 更新命令

TableAdapter 的更新功能取決於 **Tableadapter Wizard** 的主要查詢中有多少可用的資訊。 例如，設定為從多個資料表提取值 (使用) 、純量 `JOIN` 值、views 或彙總函式的結果的 tableadapter，最初不是以將更新傳送回基礎資料庫的能力來建立。 不過，您可以 `INSERT` `UPDATE` `DELETE` 在 [ **屬性** ] 視窗中手動設定、和命令。

## <a name="tableadapter-queries"></a>TableAdapter 查詢

![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif)

Tableadapter 可以包含多個查詢來填滿其相關聯的資料表。 只要每個查詢傳回的資料符合與關聯資料表相關聯的架構，您就可以定義應用程式所需之 TableAdapter 的查詢數目。 這項功能可讓 TableAdapter 根據不同的準則載入不同的結果。

例如，如果您的應用程式包含具有客戶名稱的資料表，則您可以建立一個查詢，以使用以特定字母開頭的每個客戶名稱來填滿資料表，然後使用另一個來填滿具有相同狀態之所有客戶的資料表。 若要 `Customers` 在特定狀態下填入客戶的資料表，您可以建立 `FillByState` 查詢來採用狀態值的參數，如下所示： `SELECT * FROM Customers WHERE State = @State` 。 您可以藉由呼叫 `FillByState` 方法並傳入參數值（如下所示）來執行查詢 `CustomerTableAdapter.FillByState("WA")` 。

除了加入傳回與 TableAdapter 資料表相同之資料的查詢，您還可以加入傳回純量 (單一) 值的查詢。 例如， `SELECT Count(*) From Customers` `CustomersTableAdapter,` 即使傳回的資料不符合資料表的架構，查詢會傳回 () 的客戶計數也是有效的。

## <a name="clearbeforefill-property"></a>ClearBeforeFill 屬性

根據預設，每當您執行查詢來填滿 TableAdapter 的資料表時，就會清除現有的資料，而且只會將查詢的結果載入資料表中。 `ClearBeforeFill` `false` 如果您想要將查詢所傳回的資料加入或合併至資料表中的現有資料，請將 TableAdapter 的屬性設定為。 無論您是否清除資料，如果您想要保存它們，都必須明確地將更新傳送回資料庫。 因此，請記得將任何變更儲存至資料表中的資料，然後再執行另一個填滿資料表的查詢。 如需詳細資訊，請參閱 [使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。

## <a name="tableadapter-inheritance"></a>TableAdapter 繼承

Tableadapter 藉由封裝已設定的類別，來擴充標準資料配接器的功能 <xref:System.Data.Common.DataAdapter> 。 根據預設，TableAdapter 繼承自 <xref:System.ComponentModel.Component> 類別，無法轉換成 <xref:System.Data.Common.DataAdapter> 類別。 將 TableAdapter 轉換成 <xref:System.Data.Common.DataAdapter> 類別會導致 <xref:System.InvalidCastException> 錯誤。 若要變更 TableAdapter 的基類，您可以在 <xref:System.ComponentModel.Component> **DataSet 設計工具** 中，于 TableAdapter 的 **基類** 屬性中指定衍生自的類別。

## <a name="tableadapter-methods-and-properties"></a>TableAdapter 方法和屬性

TableAdapter 類別不是 .NET 類型。 這表示您無法在檔或 **物件瀏覽器** 中查閱。 當您使用稍早所述的其中一個嚮導時，就會在設計階段建立它。 當您建立時，指派給 TableAdapter 的名稱是以您正在使用之資料表的名稱為基礎。 例如，當您根據名為的資料庫中的資料表建立 TableAdapter 時， `Orders` 會將 tableadapter 命名為 `OrdersTableAdapter` 。 您可以使用 **DataSet 設計工具** 中的 **name** 屬性來變更 TableAdapter 的類別名稱。

以下是 Tableadapter 的常用方法和屬性：

|member|描述|
|------------|-----------------|
|`TableAdapter.Fill`|以 TableAdapter 的命令結果填入 TableAdapter 的關聯資料表 `SELECT` 。|
|`TableAdapter.Update`|將變更傳送回資料庫，並傳回一個整數，代表受更新影響的資料列數目。 如需詳細資訊，請參閱 [使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。|
|`TableAdapter.GetData`|傳回 <xref:System.Data.DataTable> 填滿資料的新。|
|`TableAdapter.Insert`|在資料表中建立新的資料列。 如需詳細資訊，請參閱 [將新的記錄插入資料庫中](../data-tools/insert-new-records-into-a-database.md)。|
|`TableAdapter.ClearBeforeFill`|在您呼叫其中一個方法之前，判斷資料表是否已清空 `Fill` 。|

## <a name="tableadapter-update-method"></a>TableAdapter update 方法

Tableadapter 使用資料命令來讀取和寫入資料庫。 使用 TableAdapter 的初始 `Fill` (主要) 查詢作為基礎來建立相關聯之資料表的架構，以及 `InsertCommand` `UpdateCommand` `DeleteCommand` 與方法相關聯的、和命令 `TableAdapter.Update` 。 呼叫 TableAdapter 的 `Update` 方法會執行先前設定 tableadapter 時所建立的語句，而不是您使用 **tableadapter 查詢設定 Wizard** 加入的其他查詢之一。

當您使用 TableAdapter 時，它會有效地使用您通常會執行的命令來執行相同的作業。 例如，當您呼叫介面卡的 `Fill` 方法時，介面卡會在其屬性中執行資料命令 `SelectCommand` ，並使用資料讀取器 (例如， <xref:System.Data.SqlClient.SqlDataReader>) 將結果集載入資料表中。 同樣地，當您呼叫介面卡的方法時， `Update` 它會 `UpdateCommand` `InsertCommand` `DeleteCommand` 針對資料表中的每個變更記錄，在、和屬性中執行適當的命令 () 。

> [!NOTE]
> 如果主要查詢中有足夠的資訊，則在 `InsertCommand` `UpdateCommand` `DeleteCommand` 產生 TableAdapter 時，預設會建立、和命令。 如果 TableAdapter 的主要查詢多於單一 table `SELECT` 語句，則設計工具可能無法產生 `InsertCommand` 、 `UpdateCommand` 和 `DeleteCommand` 。 如果未產生這些命令，您可能會在執行方法時收到錯誤 `TableAdapter.Update` 。

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

除了 `InsertCommand` 、和以外 `UpdateCommand` `DeleteCommand` ，也會使用可直接對資料庫執行的方法來建立 tableadapter。 您可以直接呼叫這些方法 (`TableAdapter.Insert` 、 `TableAdapter.Update` 和 `TableAdapter.Delete`) ，以運算元據庫中的資料。 這表示您可以從程式碼呼叫這些個別的方法，而不是呼叫 `TableAdapter.Update` 來處理關聯資料表暫止的插入、更新和刪除。

如果您不想要建立這些直接方法，請將 TableAdapter 的 **GenerateDbDirectMethods** 屬性設定為 `false` [ **屬性** ] 視窗中 () 。 加入至 TableAdapter 的其他查詢是獨立的查詢，不會產生這些方法。

## <a name="tableadapter-support-for-nullable-types"></a>可為 null 類型的 TableAdapter 支援

Tableadapter 支援可為 null `Nullable(Of T)` 的類型和 `T?` 。 如需 Visual Basic 可為 Null 型別的詳細資訊，請參閱[可為 Null 的實值類型](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)。 如需 c # 中可為 null 型別的詳細資訊，請參閱 [使用可為 null 的類型](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)。

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 參考

依預設，當您建立包含相關資料表的資料集時，就會產生 TableAdapterManager 類別。 若要避免產生類別，請將 `Hierarchical Update` 資料集的屬性值變更為 false。 當您將具有關聯性的資料表拖曳至 Windows Form 或 WPF 頁面的設計介面時，Visual Studio 會宣告類別的成員變數。 如果您不使用資料系結，則必須手動宣告變數。

TableAdapterManager 類別不是 .NET 類型。 因此，您無法在檔中查閱。 它是在設計階段建立的，做為資料集建立過程的一部分。

以下是類別的常用方法和屬性 `TableAdapterManager` ：

|member|描述|
|------------|-----------------|
|`UpdateAll` 方法|儲存所有資料表中的所有資料。|
|`BackUpDataSetBeforeUpdate` 屬性|判斷是否要在執行方法之前建立資料集的備份副本 `TableAdapterManager.UpdateAll` 。布林。|
|*tableName* `TableAdapter` 財產|代表 TableAdapter。 產生的 TableAdapterManager 包含其所管理之每個的屬性 `TableAdapter` 。 例如，具有 Customers 和 Orders 資料表的資料集會以包含和屬性的 TableAdapterManager `CustomersTableAdapter` 產生 `OrdersTableAdapter` 。|
|`UpdateOrder` 屬性|控制個別 insert、update 和 delete 命令的順序。 將此值設定為列舉中的其中一個值 `TableAdapterManager.UpdateOrderOption` 。<br /><br /> 依預設， `UpdateOrder` 會設為 **InsertUpdateDelete**。 這表示會針對資料集中的所有資料表執行插入、更新和刪除作業。|

## <a name="security"></a>安全性

當您使用 CommandType 屬性設定為的資料命令時 <xref:System.Data.CommandType.Text> ，請仔細檢查從用戶端傳送的資訊，再將其傳遞至您的資料庫。 惡意使用者可能會嘗試傳送 (插入) 修改過或額外的 SQL 陳述式，以獲得未授權的存取或破壞資料庫。 將使用者輸入傳送至資料庫之前，請務必確認該資訊是否有效。 最佳做法是盡可能隨時使用參數化查詢或預存程式。

## <a name="see-also"></a>另請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
