---
title: 建立和設定資料集
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 44023543f1f7b57352448755de942af1c0c712ac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642397"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>如何：在 Visual Studio 中建立和設定資料集

「資料集」是一組物件，可將資料庫中的資料儲存在記憶體中，並支援變更追蹤，以對該資料啟用建立、讀取、更新和刪除（CRUD）作業，而不需要永遠連接到資料庫。 Dataset 是針對資料商務應用程式的簡單*表單*所設計。 針對新的應用程式，請考慮使用 Entity Framework 在記憶體中儲存和模型資料。 若要使用資料集，您應該具備資料庫概念的基本知識。

您可以使用 [**資料來源設定] Wizard**，在設計階段的 Visual Studio 中建立具類型的 <xref:System.Data.DataSet> 類別。 如需以程式設計方式建立資料集的相關資訊，請參閱[建立資料集（ADO.NET）](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>使用資料來源設定向導建立新的資料集

1. 在 Visual Studio 中開啟您的專案，然後選擇 [**專案** > **加入新的資料來源**]，以啟動 [**資料來源設定向導]** 。

2. 選擇您要連接的資料來源類型。

     ![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)

3. 選擇將做為資料集資料來源的資料庫。

     ![資料來源選擇連接](../data-tools/media/data-source-choose-a-connection.png)

4. 從您想要在資料集中呈現的資料庫，選擇資料表（或個別資料行）、預存程式、函數和 views。

     ![選擇資料庫物件](../data-tools/media/raddata-chose-objects.png)

5. 按一下 [ **完成**]。

   資料集會顯示為**方案總管**中的節點。

   ![方案總管中的資料集](../data-tools/media/dataset-in-solution-explorer.png)

6. 按一下 **方案總管**中的 資料集 節點，在  **dataset 設計**工具 中開啟資料集。 資料集中的每個資料表都有相關聯的 `TableAdapter` 物件，在底部表示。 資料表介面卡是用來填入資料集，並選擇性地將命令傳送至資料庫。

   ![DataSet 設計工具](../data-tools/media/dataset-designer.png)

7. 連接資料表的關聯線代表資料表關聯性，如資料庫中所定義。 根據預設，資料庫中的外鍵條件約束只會以關聯性表示，而 update 和 delete 規則會設定為 none。 一般來說，這就是您想要的。 不過，您可以按一下這幾行來顯示 [**關聯**] 對話方塊，您可以在其中變更階層式更新的行為。 如需詳細資訊，請參閱[資料集](../data-tools/relationships-in-datasets.md)和[階層式更新](../data-tools/hierarchical-update.md)中的關聯性。

     ![資料集關聯對話方塊](../data-tools/media/raddata-relation-dialog.png)

8. 在資料表中按一下資料表、資料表介面卡或資料行名稱，即可在 [**屬性**] 視窗中查看其屬性。 您可以在這裡修改某些值。 請記住，您會修改資料集，而不是源資料庫。

     ![資料集資料行屬性](../data-tools/media/dataset-column-properties.png)

9. 您可以將新的資料表或資料表介面卡加入至資料集，或為現有的資料表介面卡加入新的查詢，或從 [**工具箱**] 索引標籤拖曳這些專案，以指定資料表之間的新關聯性。當**DataSet 設計**工具處於焦點時，就會出現此索引標籤。

     ![資料集工具箱](../data-tools/media/raddata-dataset-toolbox.png)

接下來，您可能會想要指定如何將資料填入資料集。 為此，您可以使用 [ **TableAdapter 設定向導]** 。 如需詳細資訊，請參閱[使用 Tableadapter 填滿資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>將資料庫資料表或其他物件加入至現有的資料集

此程式示範如何從您第一次用來建立資料集的相同資料庫中加入資料表。

1. 按一下**方案總管**中的 [資料集] 節點，將**dataset 設計**工具帶入焦點。

2. 按一下 Visual Studio 左邊界中的 [**資料來源**] 索引標籤，或在搜尋方塊中輸入**資料來源**。

3. 以滑鼠右鍵按一下資料集節點，然後選取 [**使用 Wizard 設定資料來源]** 。

     ![資料來源內容功能表](../data-tools/media/data-source-context-menu.png)

4. 使用 wizard 指定要加入至資料集的其他資料表、預存程式或其他資料庫物件。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>將獨立資料表加入至資料集

1. 在 [DataSet 設計工具] 中開啟資料集。

2. 將 [<xref:System.Data.DataTable>] 類別從 [**工具箱**] 的 [**資料集**] 索引標籤拖曳至 [ **DataSet 設計工具**]。

3. 加入資料行以定義您的資料表。 以滑鼠右鍵按一下資料表，然後選擇 [**加入** >  資料**行**]。 如有必要，請使用 [**屬性**] 視窗來設定資料行的資料類型和索引鍵。

獨立資料表必須在獨立資料表中執行 `Fill` 邏輯，讓您可以將資料填入其中。 如需填入獨立資料表的詳細資訊，請參閱[從 DataAdapter 填入資料集](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)。

## <a name="see-also"></a>請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [資料集中的關聯性](../data-tools/relationships-in-datasets.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)