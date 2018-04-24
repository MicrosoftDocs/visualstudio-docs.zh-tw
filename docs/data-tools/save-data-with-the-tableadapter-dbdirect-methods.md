---
title: 使用 TableAdapter DBDirect 方法儲存資料
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aae296898bfcddfa451875fe78b29f2ae95fc9df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>使用 TableAdapter DBDirect 方法儲存資料
本逐步解說提供詳細的指示，直接對資料庫執行 SQL 陳述式，使用 TableAdapter 的 DBDirect 方法。 TableAdapter 的 DBDirect 方法提供資料庫更新的控制層的級。 您可以使用它們來執行特定 SQL 陳述式和預存程序的呼叫`Insert`， `Update`，和`Delete`方法視您的應用程式 (而不是多載`Update`執行更新的方法INSERT 和 DELETE 陳述式，在一個呼叫中的)。

 在這個逐步解說期間，您將了解如何：

-   建立新**Windows Forms 應用程式**。

-   建立及設定與資料集[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)。

-   選取要拖曳的項目時，表單上建立的控制項**資料來源**視窗。 如需詳細資訊，請參閱[設定要從資料來源視窗拖曳時建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

-   建立資料繫結表單項目從**資料來源**視窗拖曳至表單。

-   加入方法以直接存取資料庫並執行插入、 更新和刪除...

## <a name="prerequisites"></a>必要條件
本逐步解說會使用 SQL Server Express LocalDB 與 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，將其安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份**資料儲存和處理**工作負載，或做為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中安裝的一部份**資料儲存和處理**在 Visual Studio 安裝程式工作負載。)展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢...**.

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       在一段時間之後, 查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式
 第一個步驟是建立**Windows Forms 應用程式**。

#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，**專案...**.

2. 展開  **Visual C#** 或**Visual Basic**左窗格中，然後選取**的傳統 Windows 桌面**。

3. 在中間窗格中，選取**Windows Form 應用程式**專案類型。

4. 將專案命名**命名為 TableAdapterDbDirectMethodsWalkthrough**，然後選擇 **確定**。

     **命名為 TableAdapterDbDirectMethodsWalkthrough**建立專案並將其加入**方案總管 中**。

## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源
 這個步驟會使用**資料來源組態精靈**來建立資料來源為基礎`Region`Northwind 範例資料庫中的資料表。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 Northwind 範例資料庫設定的詳細資訊，請參閱[如何： 安裝範例資料庫](../data-tools/installing-database-systems-tools-and-samples.md)。

#### <a name="to-create-the-data-source"></a>若要建立資料來源

1.  在**資料**功能表上，選取**顯示資料來源**。

2.  在**資料來源**視窗中，選取**加入新資料來源**啟動**資料來源組態精靈**。

3.  在**選擇資料來源類型**畫面上，選取**資料庫**，然後選取**下一步**。

4.  在**選擇資料連線**畫面上，執行下列其中一項：

    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    -   選取**新連線**啟動**新增/修改連接** 對話方塊。

5.  如果您的資料庫需要密碼，選取選項來加入敏感性資料，然後選取**下一步**。

6.  在**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步**。

7.  在**選擇您的資料庫物件**畫面上，依序展開**資料表**節點。

8.  選取`Region`資料表，，然後選取**完成**。

     **NorthwindDataSet**加入至您的專案和`Region`資料表會出現在**資料來源**視窗。

## <a name="add-controls-to-the-form-to-display-the-data"></a>將控制項加入表單以顯示資料
 建立資料繫結控制項項目從**資料來源**視窗拖曳至表單。

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>若要建立資料繫結 Windows form 上的控制項

-   將主要**區域**節點從**資料來源**視窗拖曳至表單。

     <xref:System.Windows.Forms.DataGridView> 控制項以及用於巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， `RegionTableAdapter`， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>出現在元件匣中。

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>加入會呼叫個別 TableAdapter DbDirect 方法的按鈕

1.  將三個<xref:System.Windows.Forms.Button>控制從**工具箱**到**Form1** (下面**RegionDataGridView**)。

2.  設定下列**名稱**和**文字**每個按鈕上的屬性。

    |名稱|Text|
    |----------|----------|
    |`InsertButton`|**插入**|
    |`UpdateButton`|**更新**|
    |`DeleteButton`|**刪除**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>加入程式碼以將新記錄插入至資料庫

1.  選取**InsertButton**以建立按一下事件的事件處理常式，並在程式碼編輯器中開啟表單。

2.  以下列程式碼取代 `InsertButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>加入程式碼以更新資料庫中的記錄

1.  按兩下**UpdateButton**以建立按一下事件的事件處理常式，並在程式碼編輯器中開啟表單。

2.  以下列程式碼取代 `UpdateButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>加入程式碼以從資料庫刪除記錄

1.  選取**DeleteButton**以建立按一下事件的事件處理常式，並在程式碼編輯器中開啟表單。

2.  以下列程式碼取代 `DeleteButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>執行應用程式

#### <a name="to-run-the-application"></a>若要執行應用程式

-   選取**F5**執行應用程式。

-   選取**插入**按鈕，並確認新的記錄，會顯示在方格中。

-   選取**更新**按鈕，並確認更新的記錄時，會在方格中。

-   選取**刪除**按鈕，並確認該記錄移除時從方格。

## <a name="next-steps"></a>後續步驟
 根據您的應用程式需求，有幾個步驟，您可能想要在建立資料繫結表單後執行。 一些您可以加強這個逐步解說的部分包括：

-   將搜尋功能加入至表單。

-   選取將其他資料表加入資料集**以精靈設定資料集**從**資料來源**視窗。 您可以藉由將關聯節點拖曳至表單，加入顯示關聯資料的控制項。 如需詳細資訊，請參閱[集中的關聯性](relationships-in-datasets.md)。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)