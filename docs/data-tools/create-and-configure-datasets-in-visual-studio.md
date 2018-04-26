---
title: 建立和設定 Visual Studio 中的資料集
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
ms.openlocfilehash: 8cbe95887e9a29fa98932a18c240bc558201fc43
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>建立和設定 Visual Studio 中的資料集

A*資料集*是一組儲存在記憶體中的資料庫中的資料，並且支援變更追蹤，若要啟用之物件的建立、 讀取、 更新和刪除 (CRUD) 作業，而不需要永遠連接到資料庫的資料。 資料集所設計的簡單*表單 forms over data*商務應用程式。 對於新的應用程式，請考慮使用 Entity Framework 來儲存和記憶體中的資料模型。 若要使用的資料集，您應該有基本了解資料庫概念。

您建立具類型<xref:System.Data.DataSet>Visual Studio 中的類別在設計階段使用**資料來源組態精靈**。 如需以程式設計方式建立資料集資訊，請參閱[建立資料集 (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>使用資料來源組態精靈建立新的資料集

1.  在**專案**功能表上，按一下 **加入新資料來源**啟動**資料來源組態精靈**。

2.  選擇您要連接到資料來源的類型。

     ![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png "資料來源組態精靈")

3.  資料庫中，選擇將您的資料集的資料來源的資料庫。

     ![資料來源選擇連接](../data-tools/media/data-source-choose-a-connection.png "資料來源選擇的連接")

4.  選擇資料表 （或個別資料行），預存程序、 函數和檢視表從資料庫中，您想要在 dataset 中表示。

     ![選擇的資料庫物件](../data-tools/media/raddata-chose-objects.png "raddata 選擇物件")

5.  按一下 [ **完成**]。

6.  資料集會以節點形式出現**方案總管 中**:

     ![在 [方案總管] 中的資料集](../data-tools/media/dataset-in-solution-explorer.png "方案總管 中的資料集")

     按一下該節點，然後資料集會出現在**DataSet 設計工具**。 請注意，在資料集中的每個資料表相關聯的 TableAdapter 物件，表示底部。 資料表配接器用來填入資料集以及 （選擇性） 將命令傳送至資料庫。

     ![DataSet 設計工具](../data-tools/media/dataset-designer.png "DataSet 設計工具")

7.  連接的資料表的關聯性線條則代表資料表關聯性，因為資料庫中定義。 根據預設，在資料庫中的 foreign key 條件約束關聯，以表示更新和刪除規則設定為 none。 一般而言，這是您想要。 不過，您可以按一下以顯示線條**關聯**對話方塊中，您可以在其中變更階層式更新的行為。 如需詳細資訊，請參閱[集中的關聯性](../data-tools/relationships-in-datasets.md)和[階層式更新](../data-tools/hierarchical-update.md)。

     ![資料集的關聯性對話方塊](../data-tools/media/raddata-relation-dialog.png "raddata 關聯性對話方塊")

8.  按一下資料表、 資料表配接器或在資料表中的資料行名稱中查看其內容**屬性**視窗。 您可以修改部分的值。 請記得您要修改資料集，而不是來源資料庫。

     ![資料集資料行屬性](../data-tools/media/dataset-column-properties.png "資料集資料行屬性")

9. 您可以將新的資料表或資料表配接器加入至資料集，或加入新的查詢，現有的資料表配接器，或指定這些項目從資料表間的新關聯性**工具箱** 索引標籤。此索引標籤時會出現**DataSet 設計工具**進入焦點。

     ![資料集工具箱](../data-tools/media/raddata-dataset-toolbox.png "raddata 資料集 [工具箱]")

10. 接下來，您可能想要指定如何填入資料集的資料。 因此，您使用**TableAdapter 組態精靈**。 如需詳細資訊，請參閱[填滿資料集，使用 Tableadapter](../data-tools/fill-datasets-by-using-tableadapters.md)。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>將資料庫資料表或其他物件加入至現有的資料集

此程序示範如何將資料表加入從與您用來先建立資料集相同的資料庫。

1.  按一下中的資料集節點**方案總管 中**讓 dataset 設計工具成為焦點。

2.  按一下**資料來源**索引標籤的左邊界的 Visual Studio 中，或輸入`Data Sources`中**快速啟動**。

3.  以滑鼠右鍵按一下資料集節點，然後選取**使用精靈設定資料來源**。

     ![資料來源 內容功能表](../data-tools/media/data-source-context-menu.png "資料來源 內容功能表")

4.  使用精靈來指定哪些其他的資料表或預存程序或其他資料庫物件，若要加入至資料集。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>將獨立的資料表加入資料集

1.  開啟您的資料集在**Dataset 設計工具**。

2.  拖曳<xref:System.Data.DataTable>類別從**資料集** 索引標籤**工具箱**到**Dataset 設計工具**。

3.  加入資料行來定義您的資料表。 以滑鼠右鍵按一下資料表，然後選擇 **新增 > 資料行**。 使用**屬性**視窗來設定資料行和索引鍵的資料類型，如有必要。

4.  獨立的資料表必須實作`Fill`獨立資料表中的邏輯，讓您可以填入資料。 如需填滿獨立資料的資料表資訊，請參閱[填入資料集從 DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)