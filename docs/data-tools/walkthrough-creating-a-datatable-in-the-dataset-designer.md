---
title: 在 DataSet 設計工具中建立 DataTable
description: 在這個逐步解說中，使用 DataSet 設計工具建立沒有 TableAdapter) 的 DataTable (。 建立新的 Windows Forms 應用程式，並在其中加入新的資料集。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: feec31fa0a9e34ad63e0b849d09084081e5710e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858172"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>逐步解說：在 DataSet 設計工具中建立 DataTable

本逐步解說將說明如何 <xref:System.Data.DataTable> 使用 **DataSet 設計工具** 建立沒有 TableAdapter) 的 (。 如需有關建立包含 Tableadapter 之資料表的詳細資訊，請參閱 [建立和設定 tableadapter](../data-tools/create-and-configure-tableadapters.md)。

## <a name="create-a-new-windows-forms-application"></a>建立新的 Windows Forms 應用程式

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **Windows Forms 應用程式** ] 專案類型。

4. 將專案命名為 **DataTableWalkthrough**，然後選擇 **[確定]**。

     會建立 **DataTableWalkthrough** 專案，並將其新增至 **方案總管**。

## <a name="add-a-new-dataset-to-the-application"></a>將新的資料集新增至應用程式

1. 在 [專案] 功能表上，選取 [新增項目]。

     [加入新項目]  對話方塊隨即出現。

2. 在左窗格中，選取 [ **資料**]，然後在中間窗格中選取 [資料 **集** ]。

3. 選擇 [新增]  。

     Visual Studio 會將名為 **DataSet1** 的檔案新增至專案，並在 **DataSet 設計工具** 中開啟。

## <a name="add-a-new-datatable-to-the-dataset"></a>將新的 DataTable 新增至資料集

1. 將 **DataTable** 從 [**工具箱**] 的 [**資料集**] 索引標籤拖曳至 **DataSet 設計工具**。

     名為 **DataTable1** 的資料表會加入至資料集。

2. 按一下 **DataTable1** 的標題列，並將其重新命名 `Music` 。

## <a name="add-columns-to-the-datatable"></a>將資料行加入至 DataTable

1. 以滑鼠右鍵按一下 [ **音樂** ] 資料表。 指向 [ **加入**]，然後按一下 [資料 **行**]。

2. 為數據行命名 `SongID` 。

3. 在 [屬性]  視窗中，將 <xref:System.Data.DataColumn.DataType%2A> 屬性設定為 <xref:System.Int16?displayProperty=fullName>。

4. 重複此程式，並新增下列資料行：

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>設定資料表的主要索引鍵

所有資料表都應該有主鍵。 主鍵可唯一識別資料表中的特定記錄。

若要設定主鍵，請以滑鼠右鍵按一下 [ **SongID** ] 資料行，然後按一下 [ **設定主鍵**]。 **SongID** 資料行旁邊會出現索引鍵圖示。

## <a name="save-your-project"></a>儲存您的專案

若要儲存 **DataTableWalkthrough** 專案，請在 **[檔案** ] 功能表上選取 [ **全部儲存**]。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [驗證資料](../data-tools/validate-data-in-datasets.md)
