---
title: TableAdapter 概觀 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1d5aabd4892011aa5c59abafc5d08840d1c8f5a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497476"
---
# <a name="tableadapter-overview"></a>TableAdapter 概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tableadapter 會連接到資料庫、 執行查詢或預存程序，並使用傳回的資料填入其 DataTable 設計工具所產生的元件。 Tableadapter 也會用來傳送更新的資料從您的應用程式回到資料庫。 您可以有多個查詢，因為您想要在 TableAdapter 上，只要它們會傳回符合的資料與 TableAdapter 相關聯之資料表的結構描述。 下圖顯示 TableAdapters 資料庫與記憶體中的其他物件互動的方式：  
  
 ![用戶端應用程式中的資料流程](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 雖然 TableAdapters 的設計是以**Dataset 設計工具**，產生的 TableAdapter 類別不會產生做為巢狀類別的<xref:System.Data.DataSet>。 它們位於不同的每個資料集的特定命名空間。 比方說，如果您擁有名為資料集`NorthwindDataSet`，與相關聯的 TableAdapters<xref:System.Data.DataTable>中的 s`NorthwindDataSet`會在`NorthwindDataSetTableAdapters`命名空間。 若要以程式設計方式存取特定的 TableAdapter，您必須宣告 TableAdapter 的新執行個體。 例如:   
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>相關聯的 DataTable 結構描述  
 當建立 TableAdapter、 初始查詢或預存程序用來定義 TableAdapter 的結構描述的相關聯<xref:System.Data.DataTable>。 您可以執行此初始查詢或預存程序藉由呼叫 TableAdapter`Fill`方法 (其填滿 TableAdapter 的相關聯<xref:System.Data.DataTable>)。 TableAdapter 的主要查詢所做的變更會反映在相關聯的資料的資料表結構描述。 比方說，從主查詢移除資料行移除資料行相關聯的資料表。 如果任何其他查詢的 TableAdapter 上使用 SQL 陳述式傳回不在主要的查詢中的資料行，則設計工具將嘗試同步處理主要查詢和任何其他的查詢之間的資料行變更。 如需詳細資訊，請參閱 <<c0> [ 如何： 編輯 Tableadapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)。  
  
## <a name="tableadapter-update-commands"></a>TableAdapter 更新命令  
 TableAdapter 的更新功能會相依於多少資訊都可以根據 TableAdapter 精靈中提供的主查詢。 比方說，設定為從多個資料表 （聯結） 的值、 純量值、 檢視或彙總函式的結果所擷取的 TableAdapters 不一開始建立能夠將更新送回基礎資料庫。 不過，您可以在其中設定 INSERT、 UPDATE 和 DELETE 命令中手動**屬性**視窗。  
  
## <a name="tableadapter-queries"></a>TableAdapter 查詢  
 ![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Tableadapter 可以包含多個查詢，以填滿其相關聯的資料表。 只要每個查詢會傳回相同的結構描述及其相關聯的資料表符合的資料，您可以定義您的應用程式要求時，多個 TableAdapter 查詢。 這可讓載入符合不同準則的資料。 例如，如果您的應用程式包含客戶資料表，您可以建立資料表中填入名稱開頭為特定的字母，每位客戶的查詢並填入資料表位於相同的狀態中的所有客戶的另一個查詢。 若要填滿`Customers`客戶，您可以建立給定狀態中的資料表`FillByState`查詢： 接受的狀態值的參數： `SELECT * FROM Customers WHERE State = @State`。 在執行查詢，藉由呼叫`FillByState`方法並傳入參數的值如下所示： `CustomerTableAdapter.FillByState("WA")`。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。  
  
 除了傳回的 TableAdapter 的資料表相同的結構描述資料的查詢，您可以加入傳回純量 （單一） 值的查詢。 例如，建立查詢會傳回客戶的數量 (`SELECT Count(*) From Customers`) 無效，`CustomersTableAdapter`即使不符合資料表的結構描述時，傳回的資料。  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill 屬性  
 根據預設，每次您執行查詢，以填滿 TableAdapter 的資料表時，會清除資料和查詢的結果載入至資料表。 設定 TableAdapter`ClearBeforeFill`屬性設`false`如果您想要新增或查詢所傳回的資料表中的現有資料的資料合併。 不論是否要清除的資料，您必須明確地將更新送回資料庫，如有需要。 因此請記得要儲存資料表中的資料填入資料表的另一個查詢在執行之前所做的變更。 如需詳細資訊，請參閱 <<c0> [ 使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。  
  
## <a name="tableadapter-inheritance"></a>TableAdapter 繼承  
 Tableadapter 會擴充功能的標準資料配接器藉由將封裝設定<xref:System.Data.Common.DataAdapter>。 根據預設，TableAdapter 所繼承<xref:System.ComponentModel.Component>而不能轉型成<xref:System.Data.Common.DataAdapter>類別。 轉型至 TableAdapter<xref:System.Data.Common.DataAdapter>導致<xref:System.InvalidCastException>。 若要變更 TableAdapter 的基底類別，您可以輸入的類別，衍生自<xref:System.ComponentModel.Component>中**基底類別**屬性中的 tableadapter **Dataset 設計工具**。  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter 方法和屬性  
 TableAdapter 類別不是屬於[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，因此您無法查詢其文件中或**物件瀏覽器**。 它會建立在設計階段，當您使用其中一個先前所述精靈。 當您在建立時指派至 TableAdapter 的名稱根據您正在使用之資料表的名稱。 比方說，當建立 TableAdapter 資料表為基礎的資料庫中`Orders`，就會命名為 TableAdapter `OrdersTableAdapter`。 可以使用變更類別名稱的 TableAdapter**名稱**中的屬性**Dataset 設計工具**。  
  
 以下是常用的方法和 Tableadapter 的屬性：  
  
|成員|描述|  
|------------|-----------------|  
|`TableAdapter.Fill`|填入 TableAdapter 的相關聯的資料表格 TableAdapter 的 SELECT 命令的結果。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用資料填入資料集](../data-tools/how-to-fill-a-dataset-with-data.md)。|  
|`TableAdapter.Update`|會將變更傳送回資料庫，並傳回整數，表示更新作業所影響的資料列數目。 如需詳細資訊，請參閱 <<c0> [ 使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。|  
|`TableAdapter.GetData`|傳回新<xref:System.Data.DataTable>填滿資料。|  
|`TableAdapter.Insert`|建立新的資料列，資料表中的資料。 如需詳細資訊，請參閱 <<c0> [ 如何： 加入資料列加入至 DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf)。|  
|`TableAdapter.ClearBeforeFill`|判斷資料表是否會清空，然後再呼叫其中一個`Fill`方法。|  
  
## <a name="tableadapter-update-method"></a>TableAdapter 更新方法  
 Tableadapter 會使用資料命令，來讀取和寫入資料庫中。 TableAdapter 的初始`Fill`（主要） 查詢作為基礎建立的資料表結構描述相關聯的資料，以及`InsertCommand`， `UpdateCommand`，以及`DeleteCommand`相關聯的命令`TableAdapter.Update`方法。 這表示該呼叫 TableAdapter`Update`方法執行陳述式時建立 TableAdapter 原先設定的而不是其中一個其他查詢加入與**TableAdapter 查詢組態精靈**.  
  
 當您使用的 TableAdapter 時，它實際上會執行相同的作業，您通常會執行的命令。 比方說，當您呼叫的介面卡`Fill`方法，在執行中的資料命令配接器及其`SelectCommand`屬性，並使用資料讀取器 (比方說， <xref:System.Data.SqlClient.SqlDataReader>) 載入結果集中的資料表。 同樣地，當您呼叫的介面卡`Update`方法，它會執行適當的命令 (在`UpdateCommand`， `InsertCommand`，和`DeleteCommand`屬性) 針對每個變更資料表中的資料記錄。  
  
> [!NOTE]
>  如果沒有足夠的資訊，在主要的查詢中， `InsertCommand`， `UpdateCommand`，和`DeleteCommand`TableAdapter 產生時，將會建立預設的命令。 如果 TableAdapter 的主要查詢多於單一資料表的 SELECT 陳述式，就可以在設計工具將無法產生`InsertCommand`， `UpdateCommand`，和`DeleteCommand`。 如果這些命令不會產生，執行時，您可能會收到錯誤`TableAdapter.Update`方法。  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 除了`InsertCommand`， `UpdateCommand`，和`DeleteCommand`，可以直接對資料庫執行的方法以建立 TableAdapters。 這些方法 (`TableAdapter.Insert`， `TableAdapter.Update`，和`TableAdapter.Delete`) 可以呼叫直接操作資料庫中的資料。 這表示您可以從您的程式碼，而不是呼叫 TableAdapter.Update 處理插入、 更新和刪除暫止呼叫這些個別的方法相關聯的資料表。  
  
 如果您不想要建立這些直接方法，設定 TableAdapter **GenerateDbDirectMethods**屬性設`false`(在**屬性**視窗)。 加入至 TableAdapter 的其他查詢是獨立的查詢 — 它們不會產生這些方法。  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter 支援可為 Null 的型別  
 Tableadapter 支援可為 null 的型別`Nullable(Of T)`和`T?`。 如需有關 Visual Basic 中的可為 null 類型的詳細資訊，請參閱[可為 Null 的實值型別](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)。 如需有關 C# 中的可為 null 類型的詳細資訊，請參閱[使用可為 Null 的型別](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)。  
  
## <a name="see-also"></a>另請參閱  
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [逐步解說： 連接至資料庫 (Windows Form) 中的資料](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)