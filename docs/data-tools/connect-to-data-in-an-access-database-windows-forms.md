---
title: 連線至 Access 資料庫中的資料
description: 瞭解如何連接到 Access 資料庫中的資料， (Visual Studio 中的 .mdb 檔或 .accdb 檔案) 。
ms.custom: SEO-VS-2020
ms.date: 07/18/2019
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: eeaafdca1a3a4d6fb73ca275c4fc97ce67094d8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867265"
---
# <a name="connect-to-data-in-an-access-database"></a>連線至 Access 資料庫中的資料

您可以使用 Visual Studio， (*.mdb* 檔或 *.accdb* 檔案連接到 Access 資料庫，) 。 在您定義連線後，資料就會出現在 [資料來源] 視窗中。 從該處，您可以將資料表或視圖拖曳至設計介面。

## <a name="prerequisites"></a>必要條件

若要使用這些程式，您需要 Windows Forms 或 WPF 專案，以及 Access 資料庫 (*.accdb* 檔案) 或 access 2000-2003 資料庫 (*.mdb* 檔案) 。 依照對應您的檔案類型的程序進行。

## <a name="create-a-dataset-for-an-accdb-file"></a>建立 .accdb 檔案的資料集

使用下列程式，連接到使用 Microsoft 365、存取2013、存取2010或存取2007建立的資料庫。

1. 在 Visual Studio 中開啟 Windows Forms 或 WPF 應用程式專案。

2. 若要開啟 [**資料來源**] 視窗，請在 [ **View** ] 功能表上選取 [**其他 Windows**  >  **資料來源**]。

   ![檢視其他視窗資料來源](../data-tools/media/viewdatasources.png)

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

   [ **資料來源設定]** 設定會開啟。

4. 在 [**選擇資料來源類型**] 頁面上選取 [**資料庫**]，然後選取 **[下一步]**。

5. 在 [**選擇資料庫模型**] 頁面上選取 [**資料集**]，然後選取 **[下一步]**。

6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。

   [新增連線] 對話方塊隨即開啟。

7. 如果 [ **資料來源** ] 未設定為 [ **Microsoft Access 資料庫** 檔案]，請選取 [ **變更** ] 按鈕。

   [ **變更資料來源** ] 對話方塊隨即開啟。 在資料來源清單中，選擇 [ **Microsoft Access 資料庫** 檔案]。 在 [ **資料提供者** ] 下拉式清單中，選取 **OLE DB 的 .NET Framework Data Provider**，然後選擇 **[確定]**。

8. 選擇 [**資料庫檔案名**] 旁的 **[流覽]** ，然後流覽至您的 *.Accdb* 檔案並選擇 [**開啟**]。

9. 視需要輸入使用者名稱和密碼 () ，然後選擇 **[確定]**。

10. 在 [**選擇您的資料連線**] 頁面上選取 **[下一步]** 。

    您可能會看到一個對話方塊，告訴您資料檔案不在您目前的專案中。 選取 **[是] 或 [** **否**]。

11. 選取 [**將連接字串儲存到應用程式佈建檔**] 頁面上的 **[下一步]** 。

12. 展開 [**選擇您的資料庫物件**] 頁面上的 [**資料表]** 節點。

13. 選取您要包含在資料集中的資料表或視圖，然後選取 **[完成]**。

    資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。

## <a name="create-a-dataset-for-an-mdb-file"></a>建立 .mdb 檔案的資料集

使用下列程式，連接到使用存取2000-2003 建立的資料庫。

1. 在 Visual Studio 中開啟 Windows Forms 或 WPF 應用程式專案。

2. 在 [ **View** ] 功能表上，選取 [**其他 Windows**  >  **資料來源**]。

   ![檢視其他視窗資料來源](../data-tools/media/viewdatasources.png)

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

    [ **資料來源設定]** 設定會開啟。

4. 在 [**選擇資料來源類型**] 頁面上選取 [**資料庫**]，然後選取 **[下一步]**。

5. 在 [**選擇資料庫模型**] 頁面上選取 [**資料集**]，然後選取 **[下一步]**。

6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。

7. 如果資料來源不是 **Microsoft Access 資料庫檔案 (OLE DB)**，請選取 **[變更** ] 以開啟 [ **變更資料來源** ] 對話方塊，並選取 [ **Microsoft Access 資料庫** 檔案]，然後選取 **[確定]**。

8. 在 [ **資料庫檔案名**] 中，指定您要連接之 *.mdb* 檔案的路徑和名稱，然後選取 **[確定]**。

   ![加入連線存取資料庫檔案](../data-tools/media/add-connection-access-db.png)

9. 在 [**選擇您的資料連線**] 頁面上選取 **[下一步]** 。

10. 選取 [**將連接字串儲存到應用程式佈建檔**] 頁面上的 **[下一步]** 。

11. 展開 [**選擇您的資料庫物件**] 頁面上的 [**資料表]** 節點。

12. 選取您要在資料集中的任何資料表或視圖，然後選取 **[完成]**。

    資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。

## <a name="next-steps"></a>下一步

您剛才建立的資料集會出現在 [ **資料來源** ] 視窗中。 現在您可以執行下列任一項工作：

- 在 [**資料來源**] 視窗中選取專案，並將其拖曳至表單或設計介面 (請參閱將 Windows Forms 控制項系結至 Visual Studio 或 [WPF 資料](/dotnet/desktop-wpf/data/data-binding-overview)系結總覽) [中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。

- 在 **DataSet 設計工具** 中開啟資料來源，以新增或編輯組成資料集的物件。

- 將驗證邏輯加入至 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 資料集內資料表的或事件 (參閱 [驗證資料](../data-tools/validate-data-in-datasets.md) 集中的資料) 。

## <a name="see-also"></a>另請參閱

- [新增連線](../data-tools/add-new-connections.md)
- [WPF 資料系結總覽](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Forms 資料系結](/dotnet/framework/winforms/data-binding-and-windows-forms)
