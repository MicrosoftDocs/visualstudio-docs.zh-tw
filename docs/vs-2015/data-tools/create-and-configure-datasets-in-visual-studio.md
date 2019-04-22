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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a2930acee9e187f14b87e28190a88195b0bea7a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656242"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>在 Visual Studio 中建立和設定資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A*資料集*是一組儲存在記憶體中的資料庫中的資料，並且支援變更追蹤啟用之物件的建立、 讀取、 更新和刪除 (CRUD) 作業，而不需要永遠連接到資料庫的資料。 資料集所設計的簡單*資料表單*商務應用程式。 對於新的應用程式，請考慮使用 Entity Framework 來儲存和模型化記憶體中的資料。 若要使用的資料集，您應該使用資料庫概念的基本知識。

 您建立具型別<xref:System.Data.DataSet>在 Visual Studio 在設計階段使用的類別**資料來源組態精靈**。 如需以程式設計方式建立資料集的詳細資訊，請參閱[建立資料集](http://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc)。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>使用資料來源組態精靈 建立新的資料集

1.  在上**專案** 功能表中，按一下**加入新的資料來源**來啟動**資料來源組態精靈**。

2.  選擇您將會連接到的資料來源的類型。

     ![資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png "資料來源組態精靈")

3.  資料庫中，選擇將成為您的資料集的資料來源的資料庫。

     ![資料來源選擇的連接](../data-tools/media/data-source-choose-a-connection.png "資料來源選擇的連接")

4.  選擇 資料表 （或個別資料行），預存程序、 函數和檢視表從資料庫中，您想要將資料集來表示。

     ![選擇的資料庫物件](../data-tools/media/raddata-chose-objects.png "raddata 選擇物件")

5.  按一下 [ **完成**]。

6.  資料集會出現的節點**方案總管 中**:

     ![在 [方案總管] 中的資料集](../data-tools/media/dataset-in-solution-explorer.png "方案總管 中的資料集")

     按一下該節點，然後資料集會出現在**DataSet 設計工具**。 請注意，在資料集中的每個資料表相關聯的 TableAdapter 物件，表示在底部。 資料表配接器用來填入資料集，並選擇性地將命令傳送至資料庫。

     ![DataSet 設計工具](../data-tools/media/dataset-designer.png "DataSet 設計工具")

7.  連接的資料表的關聯性線條則代表資料表關聯性，因為資料庫中所定義。 根據預設，在資料庫中的 foreign key 條件約束統稱為僅，關聯的更新，並刪除規則設定為 none。 一般而言，這是您想要。 不過，您可以在其中按一下以顯示線條**關聯**對話方塊中，您可以在此變更的階層式更新行為。 如需詳細資訊，請參閱 <<c0> [ 中的資料集的關聯性](../data-tools/relationships-in-datasets.md)並[階層式更新](../data-tools/hierarchical-update.md)。

     ![資料集關聯性 對話方塊](../data-tools/media/raddata-relation-dialog.png "raddata 關聯性對話方塊")

8.  按一下以查看其屬性，在資料表、 資料表配接器或在資料表中的資料行名稱**屬性**視窗。 您可以修改部分的值。 只要記住您要修改資料集，而不是來源資料庫。

     ![資料集資料行屬性](../data-tools/media/dataset-column-properties.png "資料集資料行屬性")

9. 您可以將新的資料表或資料表配接器新增至資料集，或加入新的查詢，針對現有的資料表配接器，或指定這些項目從資料表之間的新關聯**工具箱** 索引標籤。時，會出現此索引標籤**DataSet 設計工具**會在成為焦點。

     ![資料集工具箱](../data-tools/media/raddata-dataset-toolbox.png "raddata 資料集 [工具箱]")

10. 接下來，您可能想要指定如何填入資料的資料集。 對此，您使用**TableAdapter 組態精靈**。 如需詳細資訊，請參閱 <<c0> [ 使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>將資料庫資料表或其他物件新增至現有的資料集
 此程序示範如何將資料表加入從相同資料庫中，您使用第一次建立資料集。

1.  在按一下資料集節點**方案總管 中**讓 DataSet 設計工具成為焦點。

2.  按一下 **資料來源**索引標籤的左邊界的 Visual Studio 中，或輸入`Data Sources`中**QuickLaunch**。

3.  以滑鼠右鍵按一下資料集節點，然後選取**使用精靈設定資料來源**。

     ![資料來源 內容功能表](../data-tools/media/data-source-context-menu.png "資料來源 內容功能表")

4.  您可以使用精靈來指定哪些額外的資料表或預存程序或其他資料庫物件，若要加入資料集。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>將獨立的資料表加入資料集

1.  在 [DataSet 設計工具] 中開啟資料集。

2.  拖曳<xref:System.Data.DataTable>類別從**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**。

3.  新增資料行來定義您的資料表。 如需詳細資訊，請參閱[如何：將資料行加入至 DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)。

4.  獨立的資料表需要實作`Fill`獨立的資料表中的邏輯，因此您可以填入資料。 如需有關填滿獨立資料資料表，請參閱[從 DataAdapter 填入 DataSet](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)。
