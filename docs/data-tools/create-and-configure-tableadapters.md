---
title: 建立和設定 TableAdapter
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 7f43cbd8e9002d026fba632046907dfee969884d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948358"
---
# <a name="create-and-configure-tableadapters"></a>建立和設定 TableAdapter

Tableadapter 會提供您的應用程式與資料庫之間的通訊。 它們連接到資料庫、 執行的查詢或預存程序，並傳回新的資料資料表，或將現有的填滿<xref:System.Data.DataTable>使用傳回的資料。 Tableadapter 也可以從您的應用程式回到資料庫傳送更新的資料。

Tableadapter 會為您建立的當您執行下列動作之一：

- 將資料庫物件從拖曳**伺服器總管**成**Dataset 設計工具**。

- 執行資料來源組態精靈，然後選取**資料庫**或是**Web 服務**資料來源類型。

   ![在 Visual Studio 中的資料來源組態精靈](media/data-source-configuration-wizard.png)

您可以建立新的 TableAdapter，並設定它與資料來源，藉由拖曳從 TableAdapter**工具箱**空區域**Dataset 設計工具**介面。

Tableadapter 的簡介，請參閱 <<c0> [ 使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>使用 TableAdapter 組態精靈

執行**TableAdapter 組態精靈**來建立或編輯 Tableadapter 以及與其關聯的 Datatable。 您可以設定現有的 TableAdapter，以滑鼠右鍵按一下它**Dataset 設計工具**。

![raddata 資料表配接器組態精靈](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

如果您從 [工具箱] 拖曳新的 TableAdapter 時**Dataset 設計工具**焦點，精靈隨即啟動並提示您指定的資料來源的 TableAdapter 應該連接到位於。 在下一步 頁面上，精靈會要求它應該使用何種命令與 SQL 陳述式或預存程序的資料庫進行通訊。 （您不會看到這如果您要設定與資料來源相關聯的 TableAdapter。）

- 您可以選擇在基礎資料庫中建立新的預存程序，如果您有正確的權限的資料庫。 如果您沒有這些權限，這不是一個選項。

- 您也可以選擇執行現有的預存程序，如**選取**，**插入**， **UPDATE**，以及**刪除**的命令TableAdapter。 指派給預存程序**更新**命令，例如，時，會執行`TableAdapter.Update()`呼叫方法。

從已選取預存程序將參數對應至資料表中對應的資料行。 例如，如果您的預存程序會接受名為的參數`@CompanyName`它傳遞給`CompanyName`資料表中的資料行集**來源資料行**的`@CompanyName`參數`CompanyName`。

> [!NOTE]
> 指派給 SELECT 命令的預存程序是由呼叫 TableAdapter 的方法命名，在精靈的下一個步驟中執行。 預設方法是`Fill`，因此通常用來執行 SELECT 程序的程式碼是`TableAdapter.Fill(tableName)`。 如果您變更預設名稱，從`Fill`，替代`Fill`名稱指派和"TableAdapter"取代為 TableAdapter 的實際名稱 (例如`CustomersTableAdapter`)。

- 選取**建立將更新傳送至資料庫的直接方法**選項相當於設定`GenerateDBDirectMethods`屬性設為 true。 當原始 SQL 陳述式未提供足夠的資訊，或查詢不是可更新的查詢時，就無法使用此選項。 發生這種情況可以例如，在**聯結**查詢及傳回單一 （純量） 值的查詢。

**進階選項**精靈可讓您：

- 產生 INSERT、 UPDATE 和 DELETE 陳述式定義的 SELECT 陳述式為基礎**產生的 SQL 陳述式**頁面
- 使用開放式並行存取
- 指定是否要重新整理資料表之後插入，以及執行 UPDATE 陳述式

## <a name="configure-a-tableadapters-fill-method"></a>設定 TableAdapter 的 Fill 方法

有時候您可能要變更的 TableAdapter 資料表的結構描述。 若要這樣做，您會修改 TableAdapter 的主要`Fill`方法。 Tableadapter 會建立具有主要`Fill`定義相關聯的資料表的結構描述的方法。 主要`Fill`方法為基礎的查詢或預存程序中輸入當您最初設定 TableAdapter。 它是第一個 （最上層） 方法在 DataSet 設計工具中的資料表。

![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif)

任何您所做變更至 TableAdapter 的主要`Fill`方法會反映在相關聯的資料的資料表結構描述。 例如，從主要查詢移除資料行`Fill`方法也會移除資料行相關聯的資料表。 此外，移除資料行，從主要`Fill`方法移除資料行從任何其他查詢的 TableAdapter。

您可以使用 TableAdapter 查詢組態精靈來建立和編輯其他查詢的 TableAdapter。 這些額外的查詢必須符合資料表的結構描述，除非它們會傳回純量值。  每個額外的查詢具有您指定的名稱。

下列範例會示範如何呼叫名為其他查詢`FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>若要開始使用新的查詢的 TableAdapter 查詢組態精靈

1.  在 **DataSet 設計工具**中開啟資料集。

2.  如果您要建立新的查詢，拖曳**查詢**物件**資料集**索引標籤**工具箱**拖曳至<xref:System.Data.DataTable>，或選取**加入查詢**TableAdapter 的快顯功能表中。 您也可以拖曳**查詢**物件上的空白區域**Dataset 設計工具**，這會建立有關聯的 TableAdapter <xref:System.Data.DataTable>。 這些查詢只能傳回單一 （純量） 值或執行的更新、 插入或刪除對資料庫的命令。

3.  在 **選擇資料連接**畫面上，選取或建立查詢將使用的連接。

    > [!NOTE]
    > 設計工具無法判斷適當的連接，若要使用，或沒有連線可供使用時，才會出現此畫面。

4.  在 **選擇命令類型**畫面上，選取從資料庫擷取資料的下列方法：

    - **使用 SQL 陳述式**可讓您輸入 SQL 陳述式，從您的資料庫選取的資料。

    - **建立新的預存程序**您讓精靈建立新的啟用預存程序 （資料庫） 中指定的 SELECT 陳述式為基礎。

    - **使用現有的預存程序**可讓您執行查詢時，執行現有的預存程序。

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>若要在現有的查詢上啟動 TableAdapter 查詢組態精靈

- 如果您要編輯現有的 TableAdapter 查詢，以滑鼠右鍵按一下查詢，然後選擇**設定**從捷徑功能表。

    > [!NOTE]
    > 以滑鼠右鍵按一下主查詢的 TableAdapter 會重新設定 TableAdapter 和<xref:System.Data.DataTable>結構描述。 其他查詢的 TableAdapter 上按一下滑鼠右鍵，不過，設定所選的查詢。 **TableAdapter 組態精靈**重新設定 TableAdapter 定義中，雖然**TableAdapter 查詢組態精靈**重新設定所選的查詢。

### <a name="to-add-a-global-query-to-a-tableadapter"></a>若要將全域查詢新增至 TableAdapter

- 全域查詢是傳回單一 （純量） 值或沒有值的 SQL 查詢。 一般而言，全域函式會執行資料庫作業，例如插入、 更新和刪除。 它們也彙總資訊，例如資料表或所有項目以特定順序的總費用的客戶數目。

     將全域查詢中拖曳**查詢**物件**資料集**索引標籤**工具箱**拖曳到空白區域**Dataset 設計工具**.

- 提供查詢，以執行所需的工作，例如`SELECT COUNT(*) AS CustomerCount FROM Customers`。

    > [!NOTE]
    > 拖曳**查詢**物件直接放入**Dataset 設計工具**建立傳回純量 （單一） 值的方法。 當您選取的預存程序的查詢可能會傳回一個以上的單一值時，由精靈建立的方法只會傳回單一值。 例如，查詢可能會傳回所傳回資料的第一個資料列的第一個資料行。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)