---
title: 建立和設定 Tableadapter |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a2136960dfcbbbcf63fbefeb16d527793d4b939
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631042"
---
# <a name="create-and-configure-tableadapters"></a>建立和設定 TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tableadapter 會提供您的應用程式與資料庫之間的通訊。 它們會連接到資料庫、執行查詢或預存程式，並傳回新的資料表，或在現有的 <xref:System.Data.DataTable> 中填入傳回的資料。 Tableadapter 也可以將更新的資料從您的應用程式傳送回資料庫。

 當您執行下列其中一個動作時，系統會為您建立 Tableadapter：

- 執行 [[資料來源設定]](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) [設定]，然後選取 [**資料庫**] 或 [ **Web 服務**] 資料來源類型。

- 將資料庫物件從[伺服器總管](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)拖曳至**DataSet 設計工具**。

  您可以使用資料來源來建立新的 TableAdapter，並將 TableAdapter 從 [工具箱] 拖曳至**DataSet 設計工具**介面中的空白區域。

  如需 Tableadapter 的簡介，請參閱[使用 Tableadapter 填滿資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>使用 TableAdapter Configuration Wizard
 執行 [ **TableAdapter 設定向導]** 來建立或編輯 tableadapter 及其相關聯的 datatable。 您可以在 [ **DataSet 設計工具**] 中，以滑鼠右鍵按一下現有的 TableAdapter 來加以設定。

 ![raddata 表格介面卡設定向導](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata 表格介面卡設定向導")

 當焦點在**DataSet 設計工具**時，如果您從 [工具箱] 拖曳新的 TableAdapter，則此 wizard 會提示您指定 TableAdapter 應連接的資料來源，以及應該用來與資料庫通訊的命令類型（SQL）語句或預存程式。 如果您要設定已與資料來源相關聯的 TableAdapter，就不會看到此情況。

- 使用 [**建立方法直接將更新傳送至資料庫**] 選項相當於將 [`GenerateDBDirectMethods`] 屬性設定為 [true]。 當原始 SQL 陳述式未提供足夠的資訊，或查詢不是可更新的查詢時，就無法使用此選項。 例如，在**聯結**查詢和傳回單一（純量）值的查詢中，可能會發生這種情況。

- 如果您有資料庫的正確許可權，則可以選擇在基礎資料庫中建立新的預存程式。 如果您沒有這些許可權，就無法使用此選項。

- 您也可以選擇針對 TableAdapter 的**SELECT**、 **INSERT**、 **UPDATE**和**DELETE**命令執行現有的預存程式。 例如，指派給**Update**命令的預存程式會在呼叫 `TableAdapter.Update()` 方法時執行。

     從已選取預存程序將參數對應至資料表中對應的資料行。 例如，如果您的預存程式接受名為 `@CompanyName` 的參數，並將它傳遞給資料表中的 `CompanyName` 資料行，請將 `@CompanyName` 參數的**Source 資料行**設定為 `CompanyName`。

    > [!NOTE]
    > 指派給 SELECT 命令的預存程式，是藉由呼叫您在 wizard 的下一個步驟中命名的 TableAdapter 方法來執行。 預設方法是 `Fill`，因此通常用來執行 SELECT 程式的程式碼是 `TableAdapter.Fill(tableName)`。 如果您從 `Fill` 變更預設名稱，請將 `Fill` 替換為您指派的名稱，並以 TableAdapter 的實際名稱取代 "TableAdapter" （例如，`CustomersTableAdapter`）。

- Wizard 中的**Advanced 選項**可讓您根據 [**產生 SQL 語句]** 頁面上定義的 SELECT 語句，產生 INSERT、UPDATE 和 DELETE 子句。 使用開放式平行存取，並指定是否要在執行 INSERT 和 UPDATE 語句之後重新整理資料表。

## <a name="configure-a-tableadapters-fill-method"></a>設定 TableAdapter 的 Fill 方法
 有時候，您可能會想要變更 TableAdapter 資料表的架構。 若要這樣做，您可以修改 TableAdapter 的主要 `Fill` 方法。 Tableadapter 是使用定義相關聯資料表之架構的主要 `Fill` 方法所建立。 主要 `Fill` 方法是以您原先設定 TableAdapter 時輸入的查詢或預存程式為基礎。 這是 DataSet 設計工具中資料表下的第一個（最上層）方法。

 ![具有多個查詢的 TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")

 您對 TableAdapter 的主要 `Fill` 方法所做的任何變更，都會反映在相關聯之資料表的架構中。 例如，從 main `Fill` 方法中的查詢中移除資料行，也會從相關聯的資料表中移除資料行。 此外，從 main `Fill` 方法中移除資料行，會從該 TableAdapter 的任何額外查詢中移除該資料行。

 您可以使用 [TableAdapter 查詢設定] Wizard 來建立和編輯 TableAdapter 的其他查詢。 這些額外的查詢必須符合資料表架構，除非它們傳回純量值。  其他查詢具有您指定的名稱（例如，`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`）。

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>使用新的查詢啟動 TableAdapter 查詢設定向導

1. 在 **DataSet 設計工具**中開啟資料集。

2. 如果您要建立新的查詢，請將**查詢**物件從 [**工具箱**] 的 [**資料集**] 索引標籤拖曳至 <xref:System.Data.DataTable>，或從 TableAdapter 的快捷方式功能表選取 [**加入查詢**]。 您也可以將**查詢**物件拖曳至**DataSet 設計工具**的空白區域，以建立沒有相關聯 <xref:System.Data.DataTable> 的 TableAdapter。 這些查詢只能傳回單一（純量）值，或對資料庫執行 UPDATE、INSERT 或 DELETE 命令。

3. 在 [**選擇您的資料連線**] 畫面上，選取或建立查詢將使用的連接。

    > [!NOTE]
    > 此畫面只會在設計工具無法判斷要使用的適當連接，或沒有可用的連接時出現。

4. 在 [**選擇命令類型**] 畫面上，從下列從資料庫提取資料的方法中選取：

    - **使用 sql 語句**可讓您輸入 sql 語句，以從您的資料庫中選取資料。

    - **建立新的預存**程式可讓您讓 wizard 根據指定的 SELECT 語句，建立新的預存程式（在資料庫中）。

    - **使用現有的預存程式**可讓您在執行查詢時執行現有的預存程式。

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>若要在現有的查詢上啟動 TableAdapter 查詢設定向導

- 如果您要編輯現有的 TableAdapter 查詢，請以滑鼠右鍵按一下查詢，然後從快捷方式功能表中選擇 [**設定**]。

    > [!NOTE]
    > 以滑鼠右鍵按一下 TableAdapter 的主要查詢，會重新配置 TableAdapter 和 <xref:System.Data.DataTable> 架構。 在 TableAdapter 上以滑鼠右鍵按一下其他查詢，不過，只會設定選取的查詢。 **Tableadapter 設定 wizard**會重新設定 tableadapter 定義，而 tableadapter 查詢設定 wizard 只會重新設定選取的查詢。

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>若要將全域查詢加入至 TableAdapter

- *全域查詢*是傳回單一（純量）值或無值的 SQL 查詢。 一般而言，全域函式會執行資料庫作業，例如插入、更新、刪除。 它們也會匯總資訊，例如資料表中的客戶計數，或特定訂單中所有專案的總費用。

     將**查詢**物件從 [**工具箱**] 的 [**資料集**] 索引標籤拖曳至**DataSet 設計工具**的空白區域，即可加入全域查詢。

- 提供查詢來執行所需的工作，例如 `SELECT COUNT(*) AS CustomerCount FROM Customers`。

    > [!NOTE]
    > 直接將**查詢**物件拖曳至**DataSet 設計工具**會建立只傳回純量（單一）值的方法。 雖然您選取的查詢或預存程式可能會傳回一個以上的值，但 wizard 所建立的方法只會傳回單一值。 例如，查詢可能會傳回所傳回資料第一列的第一個資料行。

## <a name="see-also"></a>另請參閱
 [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
