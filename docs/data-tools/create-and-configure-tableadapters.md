---
title: 建立和設定 TableAdapter
description: 請參閱如何在 Visual Studio 中建立和設定 TableAdapter。 Tableadapter 可提供您的應用程式與資料庫之間的通訊。
ms.custom: SEO-VS-2020
ms.date: 09/01/2017
ms.topic: how-to
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9ab54b358125e45cfb0d6a4df30989cf679ab2d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867135"
---
# <a name="create-and-configure-tableadapters"></a>建立和設定 TableAdapter

Tableadapter 可提供您的應用程式與資料庫之間的通訊。 它們會連接到資料庫、執行查詢或預存程式，並傳回新的資料表，或 <xref:System.Data.DataTable> 以傳回的資料填入現有的資料表。 Tableadapter 也可以將更新的資料從您的應用程式傳送回資料庫。

當您執行下列其中一個動作時，系統會為您建立 Tableadapter：

- 將資料庫物件從 **伺服器總管** 拖曳至 **DataSet 設計工具**。

- 執行 [資料來源設定向導]，然後選取 [ **資料庫** ] 或 [ **Web 服務** ] 資料來源類型。

   ![Visual Studio 中的資料來源設定 Wizard](media/data-source-configuration-wizard.png)

您也可以使用資料來源來建立新的 TableAdapter，並將 TableAdapter 從 [ **工具箱** ] 拖曳至 **DataSet 設計工具** 介面中的空白區域。

如需 Tableadapter 的簡介，請參閱 [使用 Tableadapter 填滿資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>使用 TableAdapter 設定向導

執行 **TableAdapter 設定向導** ，以建立或編輯 tableadapter 及其相關聯的 datatable。 您可以在 **DataSet 設計工具** 中，以滑鼠右鍵按一下現有的 TableAdapter 來設定它。

![raddata 資料表介面卡設定向導](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

當 **DataSet 設計工具** 焦點時，如果您從 [工具箱] 拖曳新的 TableAdapter，則嚮導會啟動，並提示您指定 TableAdapter 應連接的資料來源。 在下一個頁面上，嚮導會詢問它應該用來與資料庫通訊的命令類型，不論是 SQL 語句或預存程式。  (如果您正在設定已與資料來源建立關聯的 TableAdapter，就不會看到此情況。 ) 

- 如果您有資料庫的正確許可權，您可以選擇在基礎資料庫中建立新的預存程式。 如果您沒有這些許可權，這將不會是選項。

- 您也可以選擇針對 TableAdapter 的 **SELECT**、 **INSERT**、 **UPDATE** 和 **DELETE** 命令執行現有的預存程式。 例如，在呼叫方法時，會執行指派給 **Update** 命令的預存程式 `TableAdapter.Update()` 。

從已選取預存程序將參數對應至資料表中對應的資料行。 例如，如果您的預存程式接受名為 `@CompanyName` 的參數，它會傳遞給 `CompanyName` 資料表中的資料行，請將參數的 **來源資料行** 設定 `@CompanyName` 為 `CompanyName` 。

> [!NOTE]
> 指派給 SELECT 命令的預存程式是藉由呼叫您在嚮導的下一個步驟中所命名之 TableAdapter 的方法來執行。 預設方法是 `Fill` ，因此通常用來執行選取程式的程式碼為 `TableAdapter.Fill(tableName)` 。 如果您從變更預設名稱 `Fill` ，請 `Fill` 以您指派的名稱取代，並將 "tableadapter" 取代為 TableAdapter 的實際名稱 (例如， `CustomersTableAdapter`) 。

- 選取 [ **建立方法以直接將更新傳送至資料庫** ] 選項，相當於將 `GenerateDBDirectMethods` 屬性設為 true。 當原始 SQL 陳述式未提供足夠的資訊，或查詢不是可更新的查詢時，就無法使用此選項。 例如，在 **聯結** 查詢和傳回單一 (純量) 值的查詢中，可能會發生這種情況。

Wizard 中的 [ **Advanced] 選項** 可讓您：

- 根據 [ **產生 SQL 語句]** 頁面上定義的 SELECT 語句來產生 INSERT、UPDATE 和 DELETE 子句。
- 使用開放式並行存取
- 指定是否在執行 INSERT 和 UPDATE 語句之後重新整理資料表

## <a name="configure-a-tableadapters-fill-method"></a>設定 TableAdapter 的 Fill 方法

有時候您可能會想要變更 TableAdapter 資料表的架構。 若要這樣做，請修改 TableAdapter 的主要 `Fill` 方法。 Tableadapter 是以 `Fill` 定義關聯資料表架構的主要方法來建立。 主要 `Fill` 方法是以您最初設定 TableAdapter 時所輸入的查詢或預存程式為基礎。 它是資料集設計工具中資料表下的第一個 (最上層) 方法。

![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif)

您對 TableAdapter 的 main 方法所做的任何變更， `Fill` 都會反映在相關聯資料表的架構中。 例如，從 main 方法中的查詢移除資料行時， `Fill` 也會從相關聯的資料表中移除資料行。 此外，從 main 方法中移除資料行， `Fill` 會從該 TableAdapter 的任何其他查詢中移除該資料行。

您可以使用 [TableAdapter 查詢設定向導] 來建立和編輯 TableAdapter 的其他查詢。 這些額外的查詢必須符合資料表架構，除非它們傳回純量值。  每個額外的查詢都有您指定的名稱。

下列範例示範如何呼叫名為的其他查詢 `FillByCity` ：

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>使用新查詢啟動 TableAdapter 查詢設定向導

1. 在 [DataSet 設計工具] 中開啟資料集。

2. 如果您要建立新的查詢，請從 [**工具箱**] 的 [**資料集**] 索引標籤拖曳 **查詢** 物件至 <xref:System.Data.DataTable> ，或從 TableAdapter 的快捷方式功能表中選取 [**加入查詢**]。 您也可以將 **查詢** 物件拖曳到 **DataSet 設計工具** 的空白區域，以建立沒有相關聯的 TableAdapter <xref:System.Data.DataTable> 。 這些查詢只能傳回單一 (純量) 值，或是對資料庫執行 UPDATE、INSERT 或 DELETE 命令。

3. 在 [ **選擇您的資料連線** ] 畫面上，選取或建立查詢將使用的連接。

    > [!NOTE]
    > 只有當設計工具無法判斷要使用的適當連接，或沒有可用的連接時，才會出現此畫面。

4. 在 [ **選擇命令類型** ] 畫面上，選取下列從資料庫提取資料的方法：

    - **使用 sql 語句** 可讓您輸入 sql 語句，以從資料庫中選取資料。

    - **建立新的預存** 程式可讓您讓 wizard 根據指定的 SELECT 語句，在資料庫) 中建立新的預存程式 (。

    - **使用現有的預存程式** ，可讓您在執行查詢時執行現有的預存程式。

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>在現有的查詢上啟動 TableAdapter 查詢設定 wizard

- 如果您正在編輯現有的 TableAdapter 查詢，請以滑鼠右鍵按一下查詢，然後從快捷方式功能表中選擇 [ **設定** ]。

    > [!NOTE]
    > 以滑鼠右鍵按一下 TableAdapter 的主要查詢，會重新配置 TableAdapter 和 <xref:System.Data.DataTable> 架構。 但是，以滑鼠右鍵按一下 TableAdapter 上的其他查詢，只會設定選取的查詢。 **Tableadapter 設定 wizard** 會重新設定 tableadapter 定義，而 **Tableadapter 查詢設定 wizard** 只會重新設定選取的查詢。

### <a name="to-add-a-global-query-to-a-tableadapter"></a>將全域查詢加入至 TableAdapter

- 全域查詢是傳回單一 (純量) 值或沒有值的 SQL 查詢。 一般情況下，全域函式會執行資料庫作業，例如插入、更新和刪除。 它們也會匯總資訊，例如資料表中的客戶計數，或特定訂單中所有專案的總費用。

     您可以從 [**工具箱**] 的 [**資料集**] 索引標籤，將 **查詢** 物件拖曳到 **DataSet 設計工具** 的空白區域，藉以新增全域查詢。

- 提供執行所需工作（例如）的查詢 `SELECT COUNT(*) AS CustomerCount FROM Customers` 。

    > [!NOTE]
    > 直接將 **查詢** 物件拖曳到 **DataSet 設計工具** 會建立只傳回純量 (單一) 值的方法。 當您選取的查詢或預存程式可能會傳回一個以上的值時，由 wizard 建立的方法只會傳回單一值。 例如，查詢可能會傳回所傳回資料中第一個資料列的第一個資料行。

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
