---
title: 使用 TableAdapter DBDirect 方法儲存資料
description: 在這個逐步解說中，請使用 TableAdapter 的 DBDirect 方法，直接對資料庫執行 SQL 語句。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 00f508163dc039d5c29013538a78fa7dab6091fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858445"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>使用 TableAdapter DBDirect 方法儲存資料

本逐步解說提供使用 TableAdapter 的 DBDirect 方法直接對資料庫執行 SQL 語句的詳細指示。 TableAdapter 的 DBDirect 方法可讓您妥善控制您的資料庫更新。 您可以使用它們來執行特定的 SQL 語句和預存程式，方法是呼叫 `Insert` `Update` 您的 `Delete` 應用程式所需的個別、和方法 (而不是 `Update` 在一個呼叫) 中執行 UPDATE、INSERT 和 DELETE 子句的多載方法。

在這個逐步解說期間，您將了解如何：

- 建立新的 **Windows Forms 應用程式**。

- 使用 [ [資料來源設定] Wizard](../data-tools/media/data-source-configuration-wizard.png)建立及設定資料集。

- 從 [資料來源] 視窗拖曳項目時，選取要在表單上建立的控制項。 如需詳細資訊，請參閱 [設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

- 從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結表單。

- 新增方法以直接存取資料庫，並執行插入、更新和刪除。

## <a name="prerequisites"></a>必要條件

本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 **Visual Studio 安裝程式** 中，您可以安裝 SQL Server Express LocalDB 作為 **資料儲存和處理** 工作負載的一部分，或安裝為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (SQL Server 物件總管會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式

第一個步驟是建立 **Windows Forms 應用程式**。

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **Windows Forms 應用程式** ] 專案類型。

4. 將專案命名為 **TableAdapterDbDirectMethodsWalkthrough**，然後選擇 **[確定]**。

     隨即建立 **TableAdapterDbDirectMethodsWalkthrough** 專案，並將其新增至 [方案總管]。

## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源

此步驟使用 [資料來源組態精靈]，根據 Northwind 範例資料庫中的 `Region` 資料表建立資料來源。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱 [如何：安裝範例資料庫](../data-tools/installing-database-systems-tools-and-samples.md)。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 在 [ **資料** ] 功能表上，選取 [ **顯示資料來源**]。

   [資料來源] 視窗隨即開啟。

2. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

3. 在 [ **選擇資料來源類型** ] 畫面上，選取 [ **資料庫**]，然後選取 **[下一步]**。

4. 在 [ **選擇您的資料連線** ] 畫面上，執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    - 選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。

5. 如果您的資料庫需要密碼，請選取包含機密資料的選項，然後選取 **[下一步]**。

6. 在 [ **將連接字串儲存到應用程式佈建檔** ] 畫面上，選取 [ **下一步]**。

7. 在 [ **選擇您的資料庫物件** ] 畫面上，展開 [ **資料表]** 節點。

8. 選取 `Region` 資料表，然後選取 **[完成]**。

     **NorthwindDataSet** 隨即會新增至您的專案，且 `Region` 資料表會出現在 [資料來源] 視窗中。

## <a name="add-controls-to-the-form-to-display-the-data"></a>將控制項新增至表單以顯示資料

從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。

若要在 Windows form 上建立資料繫結控制項，請將主要 **區域** 節點從 [ **資料來源** ] 視窗拖曳到表單上。

<xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、、 `RegionTableAdapter` <xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 都會出現在元件匣中。

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>加入會呼叫個別 TableAdapter DbDirect 方法的按鈕

1. 從 [工具箱] 將三個 <xref:System.Windows.Forms.Button> 控制項拖曳至 **Form1** (位於 **RegionDataGridView** 下方)。

2. 在每個按鈕上，設定下列 [名稱] 及 [文字] 屬性。

    |名稱|Text|
    |----------|----------|
    |`InsertButton`|**插入**|
    |`UpdateButton`|**更新**|
    |`DeleteButton`|**刪除**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>加入程式碼以將新記錄插入至資料庫

1. 選取 [ **InsertButton** ] 以建立 click 事件的事件處理常式，並在程式碼編輯器中開啟您的表單。

2. 以下列程式碼取代 `InsertButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>加入程式碼以更新資料庫中的記錄

1. 按兩下 [UpdateButton] 建立 Click 事件的事件處理常式，並在程式碼編輯器中開啟表單。

2. 以下列程式碼取代 `UpdateButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>加入程式碼以從資料庫刪除記錄

1. 選取 [ **DeleteButton** ] 以建立 click 事件的事件處理常式，並在程式碼編輯器中開啟您的表單。

2. 以下列程式碼取代 `DeleteButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>執行應用程式

- 選取 **F5** 以執行應用程式。

- 選取 [ **插入** ] 按鈕，並確認新的記錄會出現在方格中。

- 選取 [ **更新** ] 按鈕，並確認方格中的記錄已更新。

- 選取 [ **刪除** ] 按鈕，並確認已從方格中移除該記錄。

## <a name="next-steps"></a>下一步

視您的應用程式需求而定，在建立資料系結表單之後，您可能會想要執行幾個步驟。 一些您可以加強這個逐步解說的部分包括：

- 將搜尋功能加入至表單。

- 在 [資料來源] 視窗中選取 [使用精靈設定資料集]，將其他資料表新增至資料集。 您可以藉由將關聯節點拖曳至表單，加入顯示關聯資料的控制項。 如需詳細資訊，請參閱 [資料集中的關聯](relationships-in-datasets.md)性。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
