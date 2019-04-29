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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eb1fdf57be1630468ee3990028a417565a914639
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566897"
---
# <a name="fill-datasets-by-using-tableadapters"></a>使用 TableAdapter 填入資料集

TableAdapter 元件會填入資料庫，並根據一或多個查詢或您指定的預存程序的資料的資料集。 也可以執行 Tableadapter 加入、 更新和刪除資料庫保存您對資料集的變更。 您也可以發出全域不到任何特定資料表相關的命令。

> [!NOTE]
> Visual Studio 設計工具會產生 TableAdapters。 如果您要以程式設計方式建立資料集，然後使用資料配接器，也就是.NET Framework 類別。

如需 TableAdapter 作業的詳細資訊，您可以直接跳到其中一個主題：

|主題|描述|
|-----------|-----------------|
|[建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|如何使用設計工具來建立和設定 Tableadapter|
|[建立參數型 TableAdapter 查詢](../data-tools/create-parameterized-tableadapter-queries.md)|如何讓使用者能夠引數提供給 TableAdapter 程序或查詢|
|[以 TableAdapter 直接存取資料庫](../data-tools/directly-access-the-database-with-a-tableadapter.md)|如何使用 Tableadapter 的 Dbdirect 方法|
|[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|如何更新資料時，使用 foreign key 條件約束|
|[如何擴充 TableAdapter 的功能](../data-tools/fill-datasets-by-using-tableadapters.md)|如何將自訂程式碼加入至 Tableadapter|
|[將 XML 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md)|如何使用 XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>TableAdapter 概觀

Tableadapter 會連接到資料庫、 執行的查詢或預存程序，並使用傳回的資料填入其 DataTable 設計工具所產生的元件。 Tableadapter 也會傳送更新的資料從您的應用程式回到資料庫。 您可以執行您想要在 TableAdapter 上，只要它們會傳回符合的資料與 TableAdapter 相關聯之資料表的結構描述的查詢。 下圖顯示 TableAdapters 資料庫與記憶體中的其他物件互動的方式：

![用戶端應用程式中的資料流程](../data-tools/media/clientdatadiagram.gif)

雖然 TableAdapters 的設計是以**Dataset 設計工具**，做為巢狀類別的不會產生的 TableAdapter 類別<xref:System.Data.DataSet>。 它們位於不同的命名空間專屬於每個資料集。 比方說，如果您擁有名為資料集`NorthwindDataSet`，相關聯的 TableAdapters<xref:System.Data.DataTable>中的 s`NorthwindDataSet`會在`NorthwindDataSetTableAdapters`命名空間。 若要以程式設計方式存取特定的 TableAdapter，您必須宣告 TableAdapter 的新執行個體。 例如: 

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>相關聯的 DataTable 結構描述

當您建立的 TableAdapter，您使用初始的查詢或預存程序來定義 TableAdapter 的結構描述的相關聯<xref:System.Data.DataTable>。 您執行此初始查詢，或藉由呼叫 TableAdapter 的預存程序`Fill`方法 (這會填滿 TableAdapter 的相關聯<xref:System.Data.DataTable>)。 TableAdapter 的主要查詢所做的任何變更都會反映在相關聯的資料表的結構描述中。 例如，從主查詢移除資料行也會移除資料行相關聯的資料表。 如果在 TableAdapter 上任何額外的查詢會使用傳回不在主要的查詢中的資料行的 SQL 陳述式，設計工具會嘗試同步處理主要查詢和其他查詢之間的資料行變更。

## <a name="tableadapter-update-commands"></a>TableAdapter 更新命令

TableAdapter 的更新功能是取決於主要查詢中有多少資訊**TableAdapter 精靈**。 例如，設定為從多個資料表擷取值的 Tableadapter (使用`JOIN`)、 純量值、 檢視或彙總函式的結果不會一開始建立能夠將更新送回基礎資料庫。 不過，您可以設定`INSERT`， `UPDATE`，並`DELETE`命令以手動方式在**屬性**視窗。

## <a name="tableadapter-queries"></a>TableAdapter 查詢

![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif)

Tableadapter 可以包含多個查詢，以填滿其相關聯的資料表。 只要每個查詢會傳回相同的結構描述及其相關聯的資料表符合的資料，您可以定義您的應用程式要求時，多個 TableAdapter 查詢。 這項功能可讓載入不同的結果，根據不同準則 TableAdapter。

例如，如果您的應用程式包含客戶名稱的資料表，您可以建立所有客戶都位於相同的狀態，以填滿資料表填入每個客戶名稱開頭為特定的字元，而另一個資料表的查詢。 若要填滿`Customers`資料表與給定狀態中的客戶，您可以建立`FillByState`會針對採用參數的狀態值，如下所示的查詢： `SELECT * FROM Customers WHERE State = @State`。 您會執行查詢，藉由呼叫`FillByState`方法並傳入參數的值如下所示： `CustomerTableAdapter.FillByState("WA")`。

除了新增傳回的 TableAdapter 的資料表相同的結構描述資料的查詢，您可以加入傳回純量 （單一） 值的查詢。 例如，可傳回的客戶計數的查詢 (`SELECT Count(*) From Customers`) 無效，`CustomersTableAdapter,`即使傳回的資料不符合資料表的結構描述。

## <a name="clearbeforefill-property"></a>ClearBeforeFill 屬性

根據預設，每次您執行查詢以填入 TableAdapter 的資料表時，清除現有的資料，並查詢的結果載入至資料表。 設定 TableAdapter`ClearBeforeFill`屬性設`false`如果您想要新增或將資料表中的現有資料的查詢傳回的資料合併。 不論是否要清除的資料，您必須明確地將更新送回資料庫中，如果您想要將其保存。 因此請務必儲存任何變更之前先執行另一個查詢，以填滿資料表的資料表中的資料。 如需詳細資訊，請參閱 <<c0> [ 使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。

## <a name="tableadapter-inheritance"></a>TableAdapter 繼承

Tableadapter 會擴充功能的標準資料配接器藉由將封裝設定<xref:System.Data.Common.DataAdapter>類別。 根據預設，TableAdapter 所繼承<xref:System.ComponentModel.Component>類別，並無法轉換成<xref:System.Data.Common.DataAdapter>類別。 轉型至 TableAdapter<xref:System.Data.Common.DataAdapter>類別中的結果<xref:System.InvalidCastException>時發生錯誤。 若要變更 TableAdapter 的基底類別，您可以指定衍生自類別<xref:System.ComponentModel.Component>中**基底類別**屬性中的 tableadapter **Dataset 設計工具**。

## <a name="tableadapter-methods-and-properties"></a>TableAdapter 方法和屬性

TableAdapter 類別不是屬於[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 這表示您無法進行查詢文件中的**物件瀏覽器**。 它會建立在設計階段，當您使用其中一個先前所述精靈。 當您在建立時指派給 TableAdapter 的名稱根據您正在使用之資料表的名稱。 例如，當您建立名為資料庫中的資料表為基礎的 TableAdapter `Orders`，名為 TableAdapter `OrdersTableAdapter`。 可以使用變更類別名稱的 TableAdapter**名稱**中的屬性**Dataset 設計工具**。

以下是常用的方法和 Tableadapter 的屬性：

|成員|描述|
|------------|-----------------|
|`TableAdapter.Fill`|TableAdapter 的相關的資料的 TableAdapter 的結果資料表中填入`SELECT`命令。|
|`TableAdapter.Update`|會將變更傳送回資料庫，並傳回整數，表示更新作業所影響的資料列數目。 如需詳細資訊，請參閱 <<c0> [ 使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。|
|`TableAdapter.GetData`|傳回新<xref:System.Data.DataTable>填入資料。|
|`TableAdapter.Insert`|建立新的資料列，資料表中的資料。 如需詳細資訊，請參閱 <<c0> [ 將新記錄插入資料庫](../data-tools/insert-new-records-into-a-database.md)。|
|`TableAdapter.ClearBeforeFill`|判斷資料表是否會清空，然後再呼叫其中一個`Fill`方法。|

## <a name="tableadapter-update-method"></a>TableAdapter 更新方法

Tableadapter 會使用資料命令，來讀取和寫入資料庫中。 使用 TableAdapter 的初始`Fill`(main) 查詢作為基礎建立的資料表結構描述相關聯的資料，以及`InsertCommand`， `UpdateCommand`，以及`DeleteCommand`相關聯的命令`TableAdapter.Update`方法。 呼叫 TableAdapter`Update`方法執行 TableAdapter 原先設定時所建立的陳述式，而不是其中一個其他查詢您加**TableAdapter 查詢組態精靈**.

當您使用的 TableAdapter 時，它實際上會執行相同的作業，您通常會執行的命令。 比方說，當您呼叫的介面卡`Fill`方法中，配接器執行的資料中的命令及其`SelectCommand`屬性，並使用資料讀取器 (比方說， <xref:System.Data.SqlClient.SqlDataReader>) 載入結果集中的資料表。 同樣地，當您呼叫的介面卡`Update`方法，它會執行適當的命令 (在`UpdateCommand`， `InsertCommand`，和`DeleteCommand`屬性) 針對每個變更資料表中的記錄。

> [!NOTE]
> 如果沒有足夠的資訊，在主要的查詢中， `InsertCommand`， `UpdateCommand`，和`DeleteCommand`TableAdapter 產生時，將會建立預設的命令。 如果 TableAdapter 的主要查詢是單一的資料表超過`SELECT`陳述式，就可以在設計工具將無法產生`InsertCommand`， `UpdateCommand`，和`DeleteCommand`。 如果不產生這些命令，執行時，您可能會收到錯誤`TableAdapter.Update`方法。

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

除了`InsertCommand`， `UpdateCommand`，和`DeleteCommand`，您可以直接對資料庫執行的方法以建立 TableAdapters。 您可以呼叫這些方法 (`TableAdapter.Insert`， `TableAdapter.Update`，和`TableAdapter.Delete`) 直接到操作資料庫中的資料。 這表示您可以呼叫這些個別的方法，從您的程式碼，而不是呼叫`TableAdapter.Update`處理插入、 更新和刪除擱置中的資料表相關聯的資料。

如果您不想要建立這些直接方法，設定 TableAdapter **GenerateDbDirectMethods**屬性設`false`(在**屬性**視窗)。 會加入至 TableAdapter 的其他查詢是獨立的查詢 — 它們不會產生這些方法。

## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter 支援可為 null 的型別

Tableadapter 支援可為 null 的型別`Nullable(Of T)`和`T?`。 如需 Visual Basic 可為 Null 型別的詳細資訊，請參閱[可為 Null 的實值類型](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)。 如需 C# 中的可為 null 類型的詳細資訊，請參閱[使用可為 null 的型別](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)。

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 參考

根據預設，當您建立包含相關的資料表的資料集時，會產生 TableAdapterManager 類別。 若要防止產生的類別，將變更的值`Hierarchical Update`屬性為 false 的資料集。 當您拖曳到設計介面上的 Windows Form 或 WPF 頁面產生關聯的資料表時，Visual Studio 會宣告類別成員變數。 如果您不使用資料繫結，您必須以手動方式將變數宣告。

TableAdapterManager 類別不是屬於[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 因此，您無法查詢文件中。 它會建立在設計階段資料集的建立程序的一部分。

以下是常用的方法和屬性`TableAdapterManager`類別：

|成員|描述|
|------------|-----------------|
|`UpdateAll` 方法|所有資料表的資料會儲存所有資料。|
|`BackUpDataSetBeforeUpdate` 屬性|決定是否要建立資料集的備份副本，然後再執行`TableAdapterManager.UpdateAll`方法。布林值。|
|*tableName* `TableAdapter`屬性|代表 TableAdapter。 產生的 TableAdapterManager 包含每個屬性`TableAdapter`其所管理。 例如，Customers 和 Orders 資料表的資料集會產生具有 TableAdapterManager 包含`CustomersTableAdapter`和`OrdersTableAdapter`屬性。|
|`UpdateOrder` 屬性|控制個別的 insert、 update 和 delete 命令的順序。 將此設定中的值的其中一個`TableAdapterManager.UpdateOrderOption`列舉型別。<br /><br /> 根據預設，`UpdateOrder`設定為**InsertUpdateDelete**。 這表示插入、 更新，然後再刪除將會在資料集中的所有資料表。|

## <a name="security"></a>安全性

當您使用資料命令 CommandType 屬性設為<xref:System.Data.CommandType.Text>，仔細檢查，然後將它傳遞到您的資料庫用戶端傳來的資訊。 惡意使用者可能會嘗試傳送 (插入) 修改過或額外的 SQL 陳述式，以獲得未授權的存取或破壞資料庫。 傳送至資料庫的使用者輸入之前，請務必確認資訊有效。 最佳做法是一律使用參數化的查詢或預存程序，可能的話。

## <a name="see-also"></a>另請參閱

- [資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
