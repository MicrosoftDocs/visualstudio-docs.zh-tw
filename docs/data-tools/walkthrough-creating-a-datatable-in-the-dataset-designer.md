---
title: 逐步解說：以 Dataset 設計工具建立 DataTable
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1126117cb1fc26c4f61bfb0f6ed0e19e86ce9323
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564918"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>逐步解說：以 Dataset 設計工具建立 DataTable

本逐步解說說明如何建立<xref:System.Data.DataTable>（不含 TableAdapter) 使用**Dataset 設計工具**。 如需建立包含 Tableadapter 的資料表資訊，請參閱[建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。

## <a name="create-a-new-windows-forms-application"></a>建立新的 Windows Forms 應用程式

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**的左側窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**DataTableWalkthrough**，然後選擇**確定**。

     **DataTableWalkthrough**建立專案並將其加入至**方案總管 中**。

## <a name="add-a-new-dataset-to-the-application"></a>將新的資料集新增至應用程式

1. 在 [專案] 功能表中，選取 [新增新項目]。

     [新增項目] 對話方塊隨即出現。

2. 在左側窗格中，選取**資料**，然後選取**DataSet**在中間窗格中。

3. 選擇 [新增]。

     Visual Studio 會加入名為的檔案**DataSet1.xsd**專案中開啟它並**Dataset 設計工具**。

## <a name="add-a-new-datatable-to-the-dataset"></a>將新的 DataTable 加入至資料集

1. 拖曳**DataTable**從**資料集**索引標籤**工具箱**拖曳至**Dataset 設計工具**。

     一個名為資料表**DataTable1**加入資料集。

2. 按一下標題列**DataTable1**並將它重新命名`Music`。

## <a name="add-columns-to-the-datatable"></a>將資料行加入至 DataTable

1. 以滑鼠右鍵按一下**音樂**資料表。 指向**新增**，然後按一下**資料行**。

2. 命名的資料行`SongID`。

3. 在 [屬性]  視窗中，將 <xref:System.Data.DataColumn.DataType%2A> 屬性設定為 <xref:System.Int16?displayProperty=fullName>。

4. 重複此程序，並新增下列資料行：

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>設定資料表的主索引鍵

所有資料的資料表應該都有主索引鍵。 主索引鍵可唯一識別資料表中的特定記錄。

若要設定的主索引鍵，以滑鼠右鍵按一下**SongID**資料行，然後再按一下**設定主索引鍵**。 索引鍵圖示旁會出現**SongID**資料行。

## <a name="save-your-project"></a>儲存您的專案

若要儲存**DataTableWalkthrough**專案中，在**檔案**功能表上，選取**全部儲存**。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [驗證資料](../data-tools/validate-data-in-datasets.md)