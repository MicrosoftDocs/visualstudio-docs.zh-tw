---
title: 在 Visual Studio 中建立和設定資料集
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bbf478424551e446ca9853dae77edb4e5b61d974
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756028"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>在 Visual Studio 中建立和設定資料集

資料集是一組儲存在記憶體中的資料庫中的資料，並且支援以啟用變更追蹤之物件的建立、 讀取、 更新和刪除 (CRUD) 作業，而不需要永遠連接到資料庫的資料。 資料集所設計的簡單*資料表單*商務應用程式。 對於新的應用程式，請考慮使用 Entity Framework 來儲存和模型化記憶體中的資料。 若要使用的資料集，您應該使用資料庫概念的基本知識。

您建立具型別<xref:System.Data.DataSet>在 Visual Studio 在設計階段使用的類別**資料來源組態精靈**。 如需以程式設計方式建立資料集的詳細資訊，請參閱[建立資料集 (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>使用資料來源組態精靈 建立新的資料集

1.  在上**專案** 功能表中，按一下**加入新的資料來源**來啟動**資料來源組態精靈**。

2.  選擇您將會連接到資料來源的類型。

     ![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)

3.  選擇將成為您的資料集的資料來源的資料庫。

     ![資料來源選擇的連接](../data-tools/media/data-source-choose-a-connection.png)

4.  選擇 資料表 （或個別資料行），預存程序、 函數和檢視表從資料庫中，您想要將資料集來表示。

     ![選擇的資料庫物件](../data-tools/media/raddata-chose-objects.png)

5.  按一下 [ **完成**]。

6.  資料集會出現的節點**方案總管 中**。

     ![在 [方案總管] 中的資料集](../data-tools/media/dataset-in-solution-explorer.png)

     按一下該節點，然後資料集會出現在**DataSet 設計工具**。 在資料集中的每個資料表都有相關聯的附註`TableAdapter`物件，表示在底部。 資料表配接器用來填入資料集，並選擇性地將命令傳送至資料庫。

     ![DataSet 設計工具](../data-tools/media/dataset-designer.png)

7.  連接的資料表的關聯性線條則代表資料表關聯性，因為資料庫中所定義。 根據預設，在資料庫中的 foreign key 條件約束統稱為僅，關聯的更新，並刪除規則設定為 none。 一般而言，這是您想要。 不過，您可以在其中按一下以顯示線條**關聯**對話方塊中，您可以在此變更的階層式更新行為。 如需詳細資訊，請參閱 <<c0> [ 中的資料集的關聯性](../data-tools/relationships-in-datasets.md)並[階層式更新](../data-tools/hierarchical-update.md)。

     ![資料集關聯性對話方塊](../data-tools/media/raddata-relation-dialog.png)

8.  按一下以查看其屬性，在資料表、 資料表配接器或在資料表中的資料行名稱**屬性**視窗。 您可以修改部分的值。 只要記住您要修改資料集，而不是來源資料庫。

     ![資料集資料行屬性](../data-tools/media/dataset-column-properties.png)

9. 您可以將新的資料表或資料表配接器新增至資料集，或加入新的查詢，針對現有的資料表配接器，或指定這些項目從資料表之間的新關聯**工具箱** 索引標籤。時，會出現此索引標籤**DataSet 設計工具**會在成為焦點。

     ![資料集 [工具箱]](../data-tools/media/raddata-dataset-toolbox.png)

10. 接下來，您可能想要指定如何填入資料的資料集。 對此，您使用**TableAdapter 組態精靈**。 如需詳細資訊，請參閱 <<c0> [ 使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>將資料庫資料表或其他物件新增至現有的資料集

此程序示範如何將資料表加入從相同資料庫中，您使用第一次建立資料集。

1.  在按一下資料集節點**方案總管 中**讓 dataset 設計工具成為焦點。

2.  按一下 **資料來源**索引標籤的左邊界的 Visual Studio 中，或輸入`Data Sources`中**快速啟動**。

3.  以滑鼠右鍵按一下資料集節點，然後選取**使用精靈設定資料來源**。

     ![資料來源 內容功能表](../data-tools/media/data-source-context-menu.png)

4.  您可以使用精靈來指定哪些額外的資料表或預存程序或其他資料庫物件，若要加入資料集。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>將獨立的資料表加入資料集

1.  開啟您的資料集，在**Dataset 設計工具**。

2.  拖曳<xref:System.Data.DataTable>類別從**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**。

3.  新增資料行來定義您的資料表。 以滑鼠右鍵按一下資料表，然後選擇 **新增** > **資料行**。 使用**屬性**視窗來設定資料行和一個索引鍵的資料類型，如有必要。

4.  獨立的資料表需要實作`Fill`獨立的資料表中的邏輯，因此您可以填入資料。 如需有關填滿獨立資料資料表，請參閱[從 DataAdapter 填入 DataSet](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)