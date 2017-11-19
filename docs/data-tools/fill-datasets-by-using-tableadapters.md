---
title: "使用 Tableadapter 填入資料集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f93a0d11435a060806a89db48b2c9e81efebe3f3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="fill-datasets-by-using-tableadapters"></a>使用 Tableadapter 填入資料集
TableAdapter 元件會填入資料集，根據一個或多個查詢或您指定的預存程序的資料庫中的資料。 也可以執行 Tableadapter 加入、 更新和刪除的資料庫來保存您對資料集的變更。 您也可以發出與任何特定資料表無關的通用命令。  
  
> [!NOTE]
>  Tableadapter 會由 Visual Studio 設計工具產生。 如果您要以程式設計方式建立資料集，然後使用資料配接器，這是.NET Framework 類別。  
  
 如需 TableAdapter 作業的詳細資訊，您可以略過直接以其中一個主題：  
  
|主題|說明|  
|-----------|-----------------|  
|[建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|如何使用設計工具來建立及設定 TableAdapters|  
|[建立參數型 TableAdapter 查詢](../data-tools/create-parameterized-tableadapter-queries.md)|如何讓使用者以引數提供給 TableAdapter 程序或查詢|  
|[以 TableAdapter 直接存取資料庫](../data-tools/directly-access-the-database-with-a-tableadapter.md)|如何使用 Tableadapter 的 Dbdirect 方法|  
|[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|如何更新資料時，使用 foreign key 條件約束|  
|[如何擴充 TableAdapter 的功能](../data-tools/fill-datasets-by-using-tableadapters.md)|如何將自訂程式碼加入至 Tableadapter|  
|[將 XML 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md)|如何使用 XML|  
  
<a name="tableadapter-overview"></a>  
  
## <a name="tableadapter-overview"></a>TableAdapter 概觀  
 Tableadapter 會連接到資料庫、 執行的查詢或預存程序，並使用傳回的資料填入其 DataTable 設計工具產生的元件。 Tableadapter 也會傳送更新的資料從您的應用程式資料庫。 您可以執行您希望在 TableAdapter 上，只要它們會傳回包含符合與 TableAdapter 相關聯之資料表的結構描述的查詢。 下圖顯示 Tableadapter 資料庫和記憶體中的其他物件之間的互動：  
  
 ![用戶端應用程式中的資料流程](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 雖然 Tableadapter 專搭配**Dataset 設計工具**，TableAdapter 類別不會產生為巢狀類別的<xref:System.Data.DataSet>。 它們位於專屬於每個資料集的個別命名空間中。 例如，如果您擁有名為的資料集`NorthwindDataSet`，相關聯的 Tableadapter<xref:System.Data.DataTable>中`NorthwindDataSet`就會產生`NorthwindDataSetTableAdapters`命名空間。 若要以程式設計方式存取特定的 TableAdapter，您必須宣告 TableAdapter 的新執行個體。 例如:   
  
 [!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
 [!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]  
  
## <a name="associated-datatable-schema"></a>相關聯的 DataTable 結構描述  
 當您建立的 TableAdapter，您使用初始查詢或預存程序來定義 TableAdapter 的結構描述的相關聯<xref:System.Data.DataTable>。 您執行這項初始查詢或預存程序，透過呼叫 TableAdapter 的`Fill`方法 (其中會填入 TableAdapter 的相關聯<xref:System.Data.DataTable>)。 TableAdapter 的主查詢所做的任何變更會反映在相關聯的資料資料表的結構描述。 例如，從主查詢移除資料行也會移除資料行從相關聯的資料表。 如果在 TableAdapter 上的任何其他查詢使用傳回主要查詢中的資料行的 SQL 陳述式，在設計工具會嘗試同步處理資料行之間的變更主查詢和其他查詢。 
  
## <a name="tableadapter-update-commands"></a>TableAdapter 更新命令  
 TableAdapter 的更新功能會相依於多少資訊會顯示在 [TableAdapter 精靈] 中的主查詢。 例如，設定為擷取值，從多個資料表 （聯結）、 純量值、 檢視或彙總函式的結果的 Tableadapter 不會一開始建立將更新送回基礎資料庫的能力。 不過，您可以設定的 INSERT、 UPDATE 和 DELETE 命令，以手動方式在**屬性**視窗。  
  
## <a name="tableadapter-queries"></a>TableAdapter 查詢  
 ![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Tableadapter 可以包含多個查詢，以填滿其相關聯的資料表格。 只要每個查詢會傳回相同的結構描述為其相關聯的資料的資料表符合的資料，您可以定義您的應用程式要求時，最多 TableAdapter 查詢。 此功能可讓您載入不同的結果，根據不同準則 TableAdapter。  
  
 比方說，如果您的應用程式包含客戶名稱的資料表，您可以建立位於相同的狀態中的所有客戶資料都填入資料表都填入每個客戶名稱開頭為特定字母，而另一個資料表的查詢。 填滿`Customers`資料表具有給定狀態中的客戶，您可以建立`FillByState`查詢參數的狀態的值，如下所示： `SELECT * FROM Customers WHERE State = @State`。 您執行查詢，藉由呼叫`FillByState`方法並傳遞參數值中的以這種方式： `CustomerTableAdapter.FillByState("WA")`。  
  
 除了新增傳回的相同 TableAdapter 的資料表結構描述資料的查詢，您可以加入傳回純量 （單一） 值的查詢。 例如，查詢所傳回的客戶計數 (`SELECT Count(*) From Customers`) 適用於`CustomersTableAdapter,`即使傳回的資料不符合資料表的結構描述。  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill 屬性  
 根據預設，每次您執行查詢以填入 TableAdapter 的資料表，清除現有的資料，並將查詢的結果載入資料表。 設定 TableAdapter 的`ClearBeforeFill`屬性`false`如果您想要新增或合併的資料查詢所傳回的資料表中現有的資料。 不論是否要清除資料，您需要明確地將更新送回資料庫，如果您想要將其保存。 所以，請記得在資料表中的資料儲存任何變更，然後再執行另一個填入資料表的查詢。 如需詳細資訊，請參閱[使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。  
  
## <a name="tableadapter-inheritance"></a>TableAdapter 繼承  
 Tableadapter 擴充功能的標準資料配接器藉由設定封裝<xref:System.Data.Common.DataAdapter>類別。 根據預設，繼承自 TableAdapter<xref:System.ComponentModel.Component>類別，而且無法轉換成<xref:System.Data.Common.DataAdapter>類別。 轉型至 TableAdapter<xref:System.Data.Common.DataAdapter>類別中的結果<xref:System.InvalidCastException>錯誤。 若要變更 TableAdapter 的基底類別，您可以指定的類別，衍生自<xref:System.ComponentModel.Component>中**基底類別**的 TableAdapter 屬性**Dataset 設計工具**。  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter 方法和屬性  
 TableAdapter 類別不是屬於[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 這表示您無法進行查詢文件中或**物件瀏覽器**。 它會建立在設計階段，當您使用其中一個先前所述精靈。 您在建立時指派給 TableAdapter 的名稱根據您正在使用的資料表名稱。 例如，當您建立的資料庫中的資料表為基礎的 TableAdapter `Orders`，名為 TableAdapter `OrdersTableAdapter`。 TableAdapter 的類別名稱可以使用變更**名稱**屬性**Dataset 設計工具**。  
  
 以下是常用的方法和 Tableadapter 的屬性：  
  
|成員|說明|  
|------------|-----------------|  
|`TableAdapter.Fill`|填入 TableAdapter 的相關聯的資料表格 TableAdapter 的 SELECT 命令的結果。|  
|`TableAdapter.Update`|將變更傳送回資料庫，並傳回整數，表示更新作業所影響的資料列數目。 如需詳細資訊，請參閱[使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。|  
|`TableAdapter.GetData`|傳回新<xref:System.Data.DataTable>填入資料。|  
|`TableAdapter.Insert`|資料表中的資料建立新的資料列。 如需詳細資訊，請參閱[新記錄插入資料庫](../data-tools/insert-new-records-into-a-database.md)。|  
|`TableAdapter.ClearBeforeFill`|判斷資料表是否會清空之前呼叫其中一種`Fill`方法。|  
  
## <a name="tableadapter-update-method"></a>TableAdapter update 方法  
 Tableadapter 會使用資料命令來讀取和寫入資料庫中。 TableAdapter 的初始`Fill`（主要） 查詢為基礎用來建立資料表的結構描述相關聯的資料，並將`InsertCommand`， `UpdateCommand`，和`DeleteCommand`相關聯的命令`TableAdapter.Update`方法。 呼叫 TableAdapter 的`Update`方法執行時 TableAdapter 原本所建立的陳述式設定，不是其中一個已新增的其他查詢**TableAdapter 查詢組態精靈**.  
  
 當您使用的 TableAdapter 時，實際上會執行相同的作業，您通常會執行的命令。 比方說，當您呼叫配接器的`Fill`方法時，配接器會執行資料命令其`SelectCommand`屬性，並使用資料讀取器 (例如， <xref:System.Data.SqlClient.SqlDataReader>) 載入結果集中的資料表。 同樣地，當您呼叫配接器的`Update`方法，它會執行適當的命令 (在`UpdateCommand`， `InsertCommand`，和`DeleteCommand`屬性) 針對每個變更資料表中的資料記錄。  
  
> [!NOTE]
>  如果沒有足夠的資訊，在主要的查詢中， `InsertCommand`， `UpdateCommand`，和`DeleteCommand`TableAdapter 產生時，依預設會建立命令。 如果 TableAdapter 的主要查詢多個單一資料表的 SELECT 陳述式，就可以在設計工具將無法再產生`InsertCommand`， `UpdateCommand`，和`DeleteCommand`。 這些命令不會產生，如果執行時，您可能會收到錯誤`TableAdapter.Update`方法。  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 除了`InsertCommand`， `UpdateCommand`，和`DeleteCommand`，可以直接對資料庫執行的方法以建立 TableAdapters。 這些方法 (`TableAdapter.Insert`， `TableAdapter.Update`，和`TableAdapter.Delete`) 可以呼叫直接操作資料庫中的資料。 這表示您可以呼叫這些個別的方法，從您的程式碼，而不是呼叫`TableAdapter.Update`來處理插入、 更新和刪除擱置中的資料表相關聯的資料。  
  
 如果您不想要建立這些直接的方法，設定 TableAdapter 的**GenerateDbDirectMethods**屬性`false`(在**屬性**視窗)。 會加入至 TableAdapter 的其他查詢都是獨立查詢-它們不會產生這些方法。  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter 支援可為 null 的型別  
 Tableadapter 支援可為 null 的型別`Nullable(Of T)`和`T?`。 如需 Visual Basic 可為 Null 型別的詳細資訊，請參閱[可為 Null 的實值類型](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)。 如需 C# 中的可為 null 類型的詳細資訊，請參閱[使用可為 Null 的型別](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)。  
  
<a name="tableadaptermanager-reference"></a>  
  
## <a name="tableadaptermanager-reference"></a>TableAdapterManager 參考  
 根據預設，`TableAdapterManager`當您建立包含相關的資料表的資料集時，會產生類別。 若要防止產生的類別，將變更的值`Hierarchical Update`屬性為 false 的資料集。 當您拖曳到設計介面上的 Windows Form 或 WPF 頁面產生關聯的資料表時，Visual Studio 會宣告類別的成員變數。 如果您不使用資料繫結，您必須以手動方式將變數宣告。  
  
 `TableAdapterManager`類別不是屬於[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 因此，您無法查詢文件中。 它會建立在設計階段做為資料集的建立程序的一部分。  
  
 以下是常用的方法和屬性的`TableAdapterManager`類別：  
  
|成員|描述|  
|------------|-----------------|  
|`UpdateAll` 方法|所有資料表的資料儲存所有資料。|  
|`BackUpDataSetBeforeUpdate` 屬性|決定是否要建立資料集的備份副本，再執行`TableAdapterManager.UpdateAll`方法。布林值。|  
|*tableName* `TableAdapter`屬性|代表`TableAdapter`。 產生`TableAdapterManager`屬性包含每個`TableAdapter`其所管理。 例如，與客戶和訂單資料表的資料集就會產生含有`TableAdapterManager`包含`CustomersTableAdapter`和`OrdersTableAdapter`屬性。|  
|`UpdateOrder` 屬性|控制個別 insert、 update 和 delete 命令的順序。 將此設定中的值的其中一個`TableAdapterManager.UpdateOrderOption`列舉型別。<br /><br /> 根據預設，`UpdateOrder`設**InsertUpdateDelete**。 這表示它會插入，則會更新，然後刪除執行中的資料集的所有資料表。|

## <a name="security"></a>安全性  
當 CommandType 屬性設定為使用資料命令<xref:System.Data.CommandType.Text>，仔細檢查之前將它傳遞給您的資料庫從用戶端傳送的資訊。 惡意使用者可能會嘗試傳送 （插入） 已修改或額外的 SQL 陳述式，來取得未經授權的存取，或資料庫損毀。 傳送至資料庫的使用者輸入之前，一定要驗證的資訊有效。 最佳做法是永遠使用參數型的查詢或預存程序時可能。  
  
## <a name="see-also"></a>請參閱
[資料集的工具](../data-tools/dataset-tools-in-visual-studio.md)