---
title: 建立和設定資料集
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
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631197"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>在 Visual Studio 中建立和設定資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*資料集*是一組物件，這些物件會將資料庫中的資料儲存在記憶體中，並支援變更追蹤以啟用對該資料的建立、讀取、更新和刪除 (CRUD) 作業，而不需要一律連接至資料庫。 資料集是針對資料商務應用程式的簡單 *表單* 所設計。 針對新的應用程式，請考慮使用 Entity Framework 在記憶體中儲存和建立資料模型。 若要使用資料集，您應該具備資料庫概念的基本知識。

 您可以 <xref:System.Data.DataSet> 使用 [ **資料來源設定] 嚮導**，在設計階段的 Visual Studio 中建立具類型的類別。 如需以程式設計方式建立資料集的詳細資訊，請參閱 [建立資料集](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc)。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>使用資料來源設定向導建立新的資料集

1. 在 [ **專案** ] 功能表上，按一下 [ **加入新資料來源** ] 以啟動 [ **資料來源設定向導]**。

2. 選擇您將連接的資料來源類型。

     ![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png "資料來源組態精靈")

3. 針對 [資料庫]，選擇將成為資料集之資料來源的資料庫。

     ![資料來源選擇連接](../data-tools/media/data-source-choose-a-connection.png "資料來源選擇連接")

4. 從資料庫中選擇您想要在資料集中呈現的資料表 (或個別資料行) 、預存程式、函數和 views。

     ![選擇資料庫物件](../data-tools/media/raddata-chose-objects.png "raddata 選擇的物件")

5. 按一下 [完成]  。

6. 資料集會顯示為 **方案總管**中的節點：

     ![方案總管中的資料集](../data-tools/media/dataset-in-solution-explorer.png "方案總管中的資料集")

     按一下該節點，資料集會出現在 [ **Dataset 設計**工具] 中。 請注意，資料集內的每個資料表都有相關聯的 TableAdapter 物件，其會在底部表示。 資料表配接器可用來填入資料集，並選擇性地將命令傳送至資料庫。

     ![DataSet 設計工具](../data-tools/media/dataset-designer.png "DataSet 設計工具")

7. 連接資料表的關聯線代表資料庫中定義的資料表關聯性。 根據預設，資料庫中的外鍵條件約束只會以關聯表示，而更新和刪除規則則設定為 [無]。 一般而言，這就是您想要的結果。 不過，您可以按一下行以顯示 [ **關聯** ] 對話方塊，您可以在其中變更階層式更新的行為。 如需詳細資訊，請參閱 [資料集](../data-tools/relationships-in-datasets.md) 和 [階層式更新](../data-tools/hierarchical-update.md)中的關聯性。

     ![資料集關聯對話方塊](../data-tools/media/raddata-relation-dialog.png "raddata 關聯對話方塊")

8. 按一下資料表中的資料表、資料表介面卡或資料行名稱，即可在 [ **屬性** ] 視窗中查看其屬性。 您可以在這裡修改部分值。 請記住，您正在修改資料集，而不是源資料庫。

     ![資料集資料行屬性](../data-tools/media/dataset-column-properties.png "資料集資料行屬性")

9. 您可以將新的資料表或資料表配接器加入至資料集，或為現有的資料表介面卡加入新的查詢，或從 [ **工具箱** ] 索引標籤拖曳這些專案，以指定資料表之間的新關聯。當 **資料集設計** 工具處於焦點時，就會出現此索引標籤。

     ![資料集工具箱](../data-tools/media/raddata-dataset-toolbox.png "raddata 資料集工具箱")

10. 接下來，您可能會想要指定如何將資料填入資料集。 針對這一點，您可以使用 **TableAdapter 設定 Wizard**。 如需詳細資訊，請參閱 [使用 Tableadapter 填滿資料集](../data-tools/fill-datasets-by-using-tableadapters.md) 。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>將資料庫資料表或其他物件新增至現有資料集
 此程式示範如何從您第一次用來建立資料集的相同資料庫加入資料表。

1. 按一下 **方案總管** 中的 [資料集] 節點，讓資料集設計工具成為焦點。

2. 在 Visual Studio 的左邊界中，按一下 [ **資料來源** ] 索引標籤，或 `Data Sources` 在 [ **快速啟動**] 中輸入。

3. 以滑鼠右鍵按一下 [資料集] 節點，然後選取 [ **使用 Wizard 設定資料來源]** 。

     ![資料來源內容功能表](../data-tools/media/data-source-context-menu.png "資料來源內容功能表")

4. 您可以使用嚮導來指定要加入至資料集的其他資料表或預存程式或其他資料庫物件。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>將獨立的資料表新增至資料集

1. 在 [DataSet 設計工具]**** 中開啟資料集。

2. 將 <xref:System.Data.DataTable> 類別從 [**工具箱**] 的 [**資料集**] 索引標籤拖曳至**DataSet 設計工具**。

3. 加入資料行以定義您的資料表。 如需詳細資訊，請參閱 [如何：將資料行加入至 DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)。

4. 獨立資料表需要 `Fill` 在獨立資料表中執行邏輯，讓您可以將資料填入資料。 如需填滿獨立資料表的詳細資訊，請參閱 [從 DataAdapter 填入資料集](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)。
