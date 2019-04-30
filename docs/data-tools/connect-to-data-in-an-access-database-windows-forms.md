---
title: 連線至 Access 資料庫中的資料 (Windows Forms)
ms.date: 02/12/2019
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9d4fcce4664483cd1d981f6a0b1233a6302c553b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568511"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>連線至 Access 資料庫中的資料 (Windows Forms)

您可以連接到 Access 資料庫 (任一 *.mdf*檔案或 *.accdb*檔案) 使用 Visual Studio。 在您定義連線後，資料就會出現在 [資料來源] 視窗中。 您可以從這個視窗將資料表或檢視表拖曳至表單上。

## <a name="prerequisites"></a>必要條件

若要使用這些程序，您需要 Windows Forms 應用程式專案，以及 Access 資料庫 (*.accdb* 檔案) 或 Access 2000-2003 資料庫 (*.mdb* 檔案) 任一項。 依照對應您的檔案類型的程序進行。

## <a name="create-a-dataset-for-an-accdb-file"></a>為.accdb 檔案建立資料集

您可以連接到使用下列程序建立透過 Access 2013、 Office 365、 Access 2010 或 Access 2007 的資料庫。

1. 開啟資料要連線的 Windows Forms 應用程式。

2. 若要開啟 **資料來源**視窗，請在**檢視**功能表上，選取**其他 Windows** > **Zdroje dat**。

   ![檢視其他視窗資料來源](../data-tools/media/viewdatasources.png)

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

   [資料來源組態精靈] 隨即開啟。

4. 選取 [**資料庫**上**選擇資料來源類型**頁面，然後再選取**下一步]**。

5. 選取 [**資料集**上**選擇資料庫模型**頁面，然後再選取**下一步]**。

6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。

   [新增連線] 對話方塊隨即開啟。

7. 如果**資料來源**未設定為**Microsoft Access 資料庫檔案 (OLE DB)**，選取**變更** 按鈕。

   **變更資料來源**對話方塊隨即開啟。 在資料來源清單中，選擇**Microsoft Access 資料庫檔案**。 在 **資料提供者**下拉式清單中，選取 **.NET Framework Data Provider for OLE DB**，然後選擇 **確定**。

8. 選擇**瀏覽**旁**資料庫檔名**，然後瀏覽至您 *.accdb*檔案，然後選擇**開啟**。

9. 輸入使用者名稱和密碼 （如有必要），然後選擇**確定**。

10. 選取 **下一步**上**選擇資料連接**頁面。

     您可能會收到對話方塊，告知您的資料檔案不在目前的專案。 選取 [是]  或 [否] 。

11. 選取 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。

12. 在 [選擇您的資料庫物件] 頁面上，展開 [資料表] 節點。

13. 選取的資料表或檢視您想要包含在您的資料集，然後選取**完成**。

     資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。

## <a name="create-a-dataset-for-an-mdb-file"></a>為.mdb 檔案建立資料集

藉由執行**資料來源組態精靈**來建立資料集。

1. 開啟資料要連線的 Windows Forms 應用程式。

2. 在 **檢視**功能表上，選取**其他 Windows** > **Zdroje dat**。

   ![檢視其他視窗資料來源](../data-tools/media/viewdatasources.png)

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

    [資料來源組態精靈] 隨即開啟。

4. 選取 [**資料庫**上**選擇資料來源類型**頁面，然後再選取**下一步]**。

5. 選取 [**資料集**上**選擇資料庫模型**頁面，然後再選取**下一步]**。

6. 在 [資料連線] 頁面上，選取 [新增連線]，設定新的資料連線。

7. 如果資料來源不是**Microsoft Access 資料庫檔案 (OLE DB)**，選取**變更**以開啟**變更資料來源** 對話方塊中，然後選取**Microsoft存取資料庫檔案**，然後選取**確定**。

8. 在 [**資料庫檔名**，指定的路徑和名稱 *.mdb*您想要連線到]，然後選取的檔案 **[確定]**。

   ![加入連線存取資料庫檔案](../data-tools/media/add-connection-access-db.png)

9. 選取 **下一步**上**選擇資料連接**頁面。

10. 選取 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。

11. 在 [選擇您的資料庫物件] 頁面上，展開 [資料表] 節點。

12. 選取任何資料表或檢視您想要在您的資料集，然後選取**完成**。

    資料集會新增至專案中，而且資料表和檢視表會出現在 [資料來源] 視窗中。

## <a name="security"></a>安全性

儲存敏感資料 (如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](/dotnet/framework/data/adonet/protecting-connection-information)。

## <a name="next-steps"></a>後續步驟

您剛才建立的資料集現已推出**Zdroje dat**視窗。 現在您可以執行下列任一項工作：

- 選取中的項目**資料來源**視窗中將它們拖曳到您的表單 (請參閱[繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md))。

- 在 **DataSet 設計工具**中開啟資料來源，以新增或編輯組成資料集的物件。

- 將驗證邏輯加入<xref:System.Data.DataTable.ColumnChanging>或是<xref:System.Data.DataTable.RowChanging>事件的資料集內的資料表 (請參閱[驗證資料集中](../data-tools/validate-data-in-datasets.md))。

## <a name="see-also"></a>另請參閱

- [新增連線](../data-tools/add-new-connections.md)