---
title: 建立及設定 TableAdapters
ms.date: 09/01/2017
ms.topic: conceptual
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 166b11eaa1e4899547e6bb0735b0a220adc6e694
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="create-and-configure-tableadapters"></a>建立及設定 TableAdapters
Tableadapter 會提供您的應用程式和資料庫之間的通訊。 這些連接到資料庫、 執行的查詢或預存程序，並傳回新的資料資料表，或將現有的填滿<xref:System.Data.DataTable>傳回資料。 Tableadapter 也可以從資料庫應用程式傳送更新的資料。

Tableadapter 會為您建立的當您執行下列動作之一：

-   執行[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)並選取 **資料庫**或**Web 服務**資料來源類型。

-   將資料庫物件從**伺服器總管**到**Dataset 設計工具**。

您也可以建立新的 TableAdapter，並將它與資料來源設定將 TableAdapter 從 [工具箱] 拖曳至空白區域中**Dataset 設計工具**介面。

Tableadapter 的簡介，請參閱[填滿資料集，使用 Tableadapter](../data-tools/fill-datasets-by-using-tableadapters.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>使用 TableAdapter 組態精靈
執行**TableAdapter 組態精靈**來建立或編輯 Tableadapter 以及與其關聯的 Datatable。 您可以設定現有的 TableAdapter，以滑鼠右鍵按一下它在**Dataset 設計工具**。

![raddata 資料表配接器組態精靈](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata 資料表配接器組態精靈")

如果您從工具箱拖曳新的 TableAdapter 時**Dataset 設計工具**焦點放精靈隨即啟動，並且提示您指定的資料來源的 TableAdapter 應該連接至處於。 在下一個頁面上，精靈會要求通訊使用資料庫時，SQL 陳述式或預存程序應該使用何種命令。 （將不會出現，如果您要設定已經與資料來源相關聯的 TableAdapter。）

-   您可以選擇在基礎資料庫中建立新的預存程序，如果您有正確的權限的資料庫。 如果您沒有這些權限，這不是一個選項。

-   您也可以選擇執行的現有預存程序**選取**，**插入**，**更新**，和**刪除**的命令TableAdapter。 指派給預存程序**更新**命令，例如，時，會執行`TableAdapter.Update()`方法呼叫。

從已選取預存程序將參數對應至資料表中對應的資料行。 比方說，如果您的預存程序接受參數，名為`@CompanyName`，就會傳遞至`CompanyName`資料表中的資料行集**來源資料行**的`@CompanyName`參數`CompanyName`。

> [!NOTE]
>  指派給 SELECT 命令的預存程序是由自行命名呼叫 TableAdapter 的方法，在精靈的下一個步驟中執行。 預設方法是`Fill`，因此通常用來執行 SELECT 程序的程式碼是`TableAdapter.Fill(tableName)`。 如果您變更預設名稱，從`Fill`，以取代`Fill`名稱指派，和 「 TableAdapter"取代為 TableAdapter 的實際名稱 (例如， `CustomersTableAdapter`)。

-   選取**建立方法，以將更新傳送至資料庫直接**選項相當於設定`GenerateDBDirectMethods`屬性設定為 true。 原始的 SQL 陳述式未提供足夠的資訊，或查詢不是可更新的查詢時，此選項為無法使用。 發生這種情況可以例如，在**聯結**查詢及傳回單一 （純量） 值的查詢。

**進階選項**精靈可讓您：
- 產生 INSERT、 UPDATE 和 DELETE 陳述式，根據定義的 SELECT 陳述式**產生 SQL 陳述式**頁面
- 使用開放式並行存取
- 指定是否要重新整理資料表之後插入，以及執行更新陳述式

## <a name="configure-a-tableadapters-fill-method"></a>設定 TableAdapter 的 Fill 方法
有時您可能想要變更的 TableAdapter 資料表的結構描述。 若要這樣做，您可以修改 TableAdapter 的主要`Fill`方法。 Tableadapter 會使用主要建立`Fill`定義相關聯的資料表的結構描述的方法。 主要`Fill`方法為基礎的查詢或預存程序輸入當您最初設定 TableAdapter。 它是第一個 （最上層） 方法，在 DataSet 設計工具中的資料表。

![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")

任何您所做變更至 TableAdapter 的主要`Fill`方法會反映在相關聯的資料資料表的結構描述。 例如，從主查詢中移除資料行`Fill`方法也會移除資料行相關聯的資料表。 此外，移除資料行，從主要`Fill`方法會移除資料行的任何其他查詢的 tableadapter。

您可以使用 TableAdapter 查詢組態精靈來建立和編輯其他查詢的 TableAdapter。 這些額外的查詢必須符合資料表的結構描述，除非它們會傳回純量值。  每個額外的查詢具有您指定的名稱。

下列範例會示範如何呼叫名為的其他查詢`FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>若要啟動 [TableAdapter 查詢組態精靈] 與新的查詢

1.  開啟您的資料集在**Dataset 設計工具**。

2.  如果您要建立新的查詢，拖曳**查詢**物件從**資料集** 索引標籤**工具箱**到<xref:System.Data.DataTable>，或選取**加入查詢**從 TableAdapter 的捷徑功能表。 您也可以拖曳**查詢**物件放到的空白區域**Dataset 設計工具**，這樣就可以建立不含相關聯的 TableAdapter <xref:System.Data.DataTable>。 這些查詢可以只傳回單一 （純量） 值或執行的更新、 插入或刪除對資料庫的命令。

3.  在**選擇資料連接**畫面上，選取或建立的查詢將使用的連接。

    > [!NOTE]
    >  當設計工具無法判斷適當的連接，若要使用，或沒有連線可供使用時，才會出現此畫面。

4.  在**選擇命令類型**畫面上，選取從下列擷取資料庫資料的方法：

    -   **使用 SQL 陳述式**可讓您輸入 SQL 陳述式，從資料庫選取的資料。

    -   **建立新的預存程序**您讓精靈建立新的啟用預存程序 （資料庫） 中指定的 SELECT 陳述式為基礎。

    -   **使用現有的預存程序**可讓您執行查詢時，執行現有的預存程序。

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>若要在現有的查詢上啟動 TableAdapter 查詢組態精靈

-   如果您正在編輯現有的 TableAdapter 查詢，以滑鼠右鍵按一下查詢，然後選擇 **設定**從捷徑功能表。

    > [!NOTE]
    >  以滑鼠右鍵按一下主查詢的 TableAdapter 會重新設定 TableAdapter 和<xref:System.Data.DataTable>結構描述。 不過，其他查詢的 TableAdapter 上按一下滑鼠右鍵，設定所選的查詢。 **TableAdapter 組態精靈**TableAdapter 查詢組態精靈重新設定所選的查詢時，會重新設定 TableAdapter 定義。

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>若要將全域查詢加入至 TableAdapter

-   *全域查詢*是傳回單一 （純量） 值或沒有值的 SQL 查詢。 一般而言，全域函式執行資料庫作業，例如插入、 更新、 刪除。 它們也彙總資訊，例如資料表或以特定順序的所有項目的總費用之客戶的計數。

     將全域查詢中拖曳**查詢**物件從**資料集** 索引標籤**工具箱**的空白區域上**Dataset 設計工具**.

-   提供查詢執行所需的工作，例如`SELECT COUNT(*) AS CustomerCount FROM Customers`。

    > [!NOTE]
    >  拖曳**查詢**物件直接放入**Dataset 設計工具**建立傳回純量 （單一） 值的方法。 當您選取的預存程序的查詢可能會傳回一個以上的單一值時，精靈所建立的方法只會傳回單一值。 例如，查詢可能會傳回所傳回資料的第一個資料列的第一個資料行。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)