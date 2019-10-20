---
title: 將資料儲存至資料庫（多個資料表） |Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655454"
---
# <a name="save-data-to-a-database-multiple-tables"></a>將資料儲存至資料庫 (多個資料表)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在應用程式的開發過程中，最常見的一個情節是在 Windows 應用程式的表單上顯示資料並編輯資料，以及將更新的資料傳送回資料庫。 此逐步解說會建立表單，以顯示來自兩個關聯資料表的資料，並示範如何編輯記錄，以及將變更儲存回資料庫。 此範例使用 Northwind 範例資料庫的 `Customers` 和 `Orders` 資料表。

 您可以透過呼叫 TableAdapter 的 `Update` 方法，將應用程式的資料存回資料庫。 當您從 [**資料來源**] 視窗將資料表拖曳至表單時，會自動加入儲存資料所需的程式碼。任何新增至表單的其他資料表都需要手動加入此程式碼。 此逐步解說會示範如何加入程式碼，以儲存多個資料表的更新。

> [!NOTE]
> 您所看到的對話方塊和功能表命令可能會與 [說明] 中所述不同，視您使用的是作用中的設定或版本而定。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱在 Visual Studio 中自訂開發設定 [Walkthrough: Calling Code in an VSTO Add-in from VBA](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

 這個逐步解說中所述的工作包括：

- 建立新的**Windows 應用程式**專案。

- 使用[資料來源設定 Wizard](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)在應用程式中建立及設定資料來源。

- 在 [[資料來源] 視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)中設定專案的控制項。 如需詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

- 從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。

- 修改資料集內每個資料表中的一些記錄。

- 修改程式碼，以將資料集中更新的資料傳送回資料庫。

## <a name="prerequisites"></a>Prerequisites
 若要完成這個逐步解說，您將需要：

- Northwind 範例資料庫的存取權。

## <a name="create-the-windows-application"></a>建立 Windows 應用程式
 第一個步驟是建立**Windows 應用程式**。 在此步驟中，將名稱指派給專案是選擇性的，但我們會提供名稱，因為我們打算在稍後儲存它。

#### <a name="to-create-the-new-windows-application-project"></a>若要建立新的 Windows 應用程式專案

1. 在 [檔案] 功能表上，建立**新的專案**。

2. 將專案命名為 `UpdateMultipleTablesWalkthrough`。

3. 選取 [ **Windows 應用程式**]，然後選取 **[確定]** 。 如需詳細資訊，請參閱[用戶端應用程式](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。

     隨即建立 **UpdateMultipleTablesWalkthrough** 專案，並將其新增至 [方案總管]。

## <a name="create-the-data-source"></a>建立資料來源
 此步驟會使用 [資料來源組態精靈] 從 Northwind 資料庫建立資料來源。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。

#### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 在 [**資料**] 功能表上，選取 [**顯示資料來源**]。

2. 在 [**資料來源**] 視窗中，選取 [**新增新資料來源**] 以啟動 [**資料來源設定向導]** 。

3. 在 [**選擇資料來源類型**] 畫面上，選取 [**資料庫**]，然後選取 **[下一步]** 。

4. 在 [**選擇您的資料連線**] 畫面上，執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    - 選取 [新增連線]，以開啟 [新增/修改連線] 對話方塊。

5. 如果您的資料庫需要密碼，請選取選項以包含機密資料，然後選取 **[下一步]** 。

6. 在 [將**連接字串儲存到應用程式佈建檔**] 上，選取 **[下一步]** 。

7. 在 [**選擇您的資料庫物件**] 畫面上，展開 [**資料表]** 節點。

8. 選取 [ **Customers** ] 和 [ **Orders** ] 資料表，然後選取 **[完成]** 。

     **NorthwindDataSet** 會新增專案中，且資料表會出現在 [資料來源] 視窗中。

## <a name="set-the-controls-to-be-created"></a>設定要建立的控制項
 在此逐步解說中，`Customers` 資料表中的資料是在**詳細**資料配置中，其中的資料會顯示在個別控制項中。 @No__t_0 資料表中的資料是在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示的**方格**配置中。

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>在資料來源視窗中設定項目的卸除類型

1. 在 [**資料來源**] 視窗中，展開 [ **Customers** ] 節點。

2. 在 [ **customers** ] 節點上，從控制項清單中選取 [**詳細資料**]，將 [ **Customers** ] 資料表的控制項變更為個別控制項。 如需詳細資訊，請參閱[設定從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

## <a name="create-the-data-bound-form"></a>建立資料系結表單
 您可以從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。

#### <a name="to-create-data-bound-controls-on-the-form"></a>在表單上建立資料繫結控制項

1. 從 [資料來源] 視窗，將 [客戶] 主節點拖曳至 **Form1**。

     會在表單上顯示具有描述性的資料繫結控制項，以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>)。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。

2. 從 [資料來源] 視窗將關聯的 [Orders] 節點拖曳至 [Form1]。

    > [!NOTE]
    > 關聯的 [Orders] 節點位於 [Fax] 節點之下，而且是 [Customers] 節點的子節點。

     <xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 OrdersTableAdapter 和 <xref:System.Windows.Forms.BindingSource> 會出現在元件匣中。

## <a name="addcode-to-update-the-database"></a>Addcode 以更新資料庫
 您可以藉由呼叫 [Customers] 和 [Orders] TableAdapters 的 `Update` 方法以更新資料庫。 根據預設，<xref:System.Windows.Forms.BindingNavigator> 的 [**儲存**] 按鈕的事件處理常式會新增至表單的程式碼，以將更新傳送至資料庫。 此程式會修改程式碼，以正確的順序傳送更新。這可避免引發參考完整性錯誤的可能性。 程式碼也會藉由將 try-catch 區塊中的更新呼叫換行，以實作錯誤處理。 您可以修改程式碼，使其符合應用程式的需求。

> [!NOTE]
> 為了清楚起見，本逐步解說不會使用交易。不過，如果您要更新兩個或多個相關的資料表，請將所有更新邏輯包含在交易中。 交易是一種處理常式，可確保在認可任何變更之前，資料庫的所有相關變更都已成功。 如需詳細資訊，請參閱[交易和並行](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b)。

#### <a name="to-add-update-logic-to-the-application"></a>將更新邏輯加入至應用程式

1. 選取 <xref:System.Windows.Forms.BindingNavigator> 上的 **儲存** 按鈕。這會開啟 `bindingNavigatorSaveItem_Click` 事件處理常式的 程式碼編輯器。

2. 替換事件處理常式中的程式碼，以呼叫相關 TableAdapters 的 `Update` 方法。 下列程式碼會先建立三個暫存資料表，以保留 <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 及 <xref:System.Data.DataRowState>) 的更新資訊。 然後，更新會以正確的循序執行。 程式碼看起來應該如下所示：

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>測試應用程式

#### <a name="to-test-the-application"></a>若要測試應用程式

1. 選取**F5**。

2. 在每個資料表中，變更一個或多個記錄的資料。

3. 選取 [儲存] 按鈕。

4. 檢查資料庫中的值，確認已儲存變更。

## <a name="next-steps"></a>後續步驟
 視您的應用程式需求而定，在 Windows 應用程式中建立資料系結表單之後，您可能會想要執行幾個步驟。 一些您可以加強這個逐步解說的部分包括：

- 將搜尋功能加入至表單。 如需詳細資訊，請參閱[如何：將參數化查詢加入至 Windows Forms 應用程式](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)。

- 編輯資料來源，以加入或移除資料庫物件。 如需詳細資訊，請參閱[如何：編輯資料集](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3)。

## <a name="see-also"></a>請參閱
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
