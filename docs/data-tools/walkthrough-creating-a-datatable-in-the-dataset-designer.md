---
title: 逐步解說：以 DataSet 設計工具建立 DataTable
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b5d359908a488e744a059f73a7ad058c249a6a40
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>逐步解說：以 DataSet 設計工具建立 DataTable

這個逐步解說說明如何建立<xref:System.Data.DataTable>（不含 TableAdapter) 使用**Dataset 設計工具**。 如需建立包含 Tableadapter 的資料表資訊，請參閱[建立及設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。

這個逐步解說中所述的工作包括：

-   建立新的 Windows Forms 應用程式專案

-   將新的資料集加入至應用程式

-   新的資料表加入資料集

-   資料行加入資料表

-   設定資料表的主索引鍵

## <a name="creating-a-new-windows-forms-application"></a>建立新的 Windows Form 應用程式

### <a name="to-create-a-new-windows-forms-application-project"></a>若要建立新的 Windows Forms 應用程式專案

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，**專案...**.

2. 展開  **Visual C#** 或**Visual Basic**左窗格中，然後選取**的傳統 Windows 桌面**。

3. 在中間窗格中，選取**Windows Form 應用程式**專案類型。

4. 將專案命名**DataTableWalkthrough**，然後選擇 **確定**。

     **DataTableWalkthrough**專案時建立，並加入至**方案總管 中**。

## <a name="adding-a-new-dataset-to-the-application"></a>將新的資料集加入至應用程式

### <a name="to-add-a-new-dataset-item-to-the-project"></a>將新的資料集項目加入至專案

1.  在**專案**功能表上，選取**加入新項目...**.

     [加入新項目] 對話方塊隨即出現。

2.  在左窗格中，選取**資料**，然後選取**資料集**中間窗格內。

3.  選擇 [新增]。

     Visual Studio 會加入名為的檔案**DataSet1.xsd**至專案，並在開啟**Dataset 設計工具**。

## <a name="adding-a-new-datatable-to-the-dataset"></a>新的資料表加入資料集

### <a name="to-add-a-new-data-table-to-the-dataset"></a>若要將新的資料表加入至資料集

1.  拖曳**DataTable**從**資料集** 索引標籤**工具箱**到**Dataset 設計工具**。

     名為的資料表**DataTable1**加入資料集。

2.  按一下標題列**DataTable1**並將它重新命名`Music`。

## <a name="adding-columns-to-the-datatable"></a>將資料行加入至 DataTable

### <a name="to-add-columns-to-the-datatable"></a>若要將資料行加入至 DataTable

1.  以滑鼠右鍵按一下**音樂**資料表。 指向**新增**，然後按一下 **資料行**。

2.  名稱資料行`SongID`。

3.  在**屬性**視窗中，將<xref:System.Data.DataColumn.DataType%2A>屬性<xref:System.Int16?displayProperty=fullName>。

4.  重複此程序，並加入下列資料行：

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="setting-the-primary-key-for-the-table"></a>設定資料表的主索引鍵

所有資料的資料表應該都有主索引鍵。 主索引鍵會唯一識別特定的記錄資料表中的資料。

### <a name="to-set-the-primary-key-of-the-data-table"></a>若要設定資料表的主索引鍵

-   以滑鼠右鍵按一下**SongID**資料行，然後再按一下**設定主索引鍵**。

     索引鍵圖示旁會顯示**SongID**資料行。

## <a name="saving-your-project"></a>儲存您的專案

### <a name="to-save-the-datatablewalkthrough-project"></a>若要儲存 DataTableWalkthrough 專案

-   在**檔案**功能表上，按一下 **全部儲存**。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [驗證資料](../data-tools/validate-data-in-datasets.md)
- [儲存資料](../data-tools/saving-data.md)