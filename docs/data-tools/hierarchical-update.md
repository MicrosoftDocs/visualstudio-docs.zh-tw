---
title: 階層式更新
description: 請參閱階層式更新，包括將更新的資料從具有2個以上相關資料表的資料集 (儲存) 回到資料庫，同時保留參考完整性規則。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 05575e6cc75468a85a3dd410ea59bebca79eee0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858835"
---
# <a name="hierarchical-update"></a>階層式更新

*階層式更新* 指的是將更新的資料從具有兩個或多個相關資料表的資料集儲存 (的程式) 回資料庫，同時維持參考完整性規則。 *參考完整性* 指的是資料庫中的條件約束所提供的一致性規則，可控制插入、更新和刪除相關記錄的行為。 例如，它是參考完整性，會強制建立客戶記錄，然後才允許為該客戶建立訂單。  如需資料集中關聯性的詳細資訊，請參閱 [資料集中的關聯](../data-tools/relationships-in-datasets.md)性。

階層式更新功能使用來管理具型別 `TableAdapterManager` `TableAdapter` 資料集中的 s。 `TableAdapterManager`元件是 Visual Studio 產生的類別，而不是 .net 類型。 當您將資料表從 [ **資料來源** ] 視窗拖曳至 Windows FORM 或 WPF 頁面時，Visual Studio 會將 TableAdapterManager 類型的變數加入至表單或頁面，而且您會在元件匣的設計工具中看到它。 如需類別的詳細資訊 `TableAdapterManager` ，請參閱 [Tableadapter](../data-tools/create-and-configure-tableadapters.md)的 TableAdapterManager 參考一節。

根據預設，資料集會將相關的資料表視為「僅限關聯」，這表示它不會強制使用外鍵條件約束。 您可以使用 **DataSet 設計工具**，在設計階段修改該設定。 選取兩個數據表之間的關聯線，即可顯示 [ **關聯** 性] 對話方塊。 您在這裡所做的變更將會決定將 `TableAdapterManager` 相關資料表中的變更傳送回資料庫時的行為。

## <a name="enable-hierarchical-update-in-a-dataset"></a>啟用資料集中的階層式更新

依預設，會針對在專案中新增或建立的所有新資料集啟用階層式更新。 將資料集內具型別資料集的 **階層式更新** 屬性設為 **True** 或 **False**，以開啟或關閉階層式更新：

![階層式更新設定](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>建立資料表之間的新關聯

若要建立兩個數據表之間的新關聯，請在 [DataSet 設計工具中，選取每個資料表的標題列，然後以滑鼠右鍵按一下並選取 [ **加入關聯**]。

![階層式更新新增關聯功能表](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>瞭解外鍵條件約束、串聯式更新和刪除

請務必瞭解在產生的資料集程式碼中，如何建立資料庫中的外鍵條件約束和串聯行為。

根據預設，會產生資料集中的資料表，且關聯性 (<xref:System.Data.DataRelation>) 符合資料庫中的關聯性。 不過，資料集中的關聯性不會產生為外鍵條件約束。 <xref:System.Data.DataRelation>**只有** 在沒有 <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> 或作用中的情況下，才會設定為關聯 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> 。

根據預設，即使已開啟串聯更新和/或串聯式刪除設定資料庫關聯性，串聯式更新和串聯刪除也會關閉。 例如，建立新客戶和新訂單，然後嘗試儲存資料，可能會與資料庫中定義的外鍵條件約束髮生衝突。 如需詳細資訊，請參閱 [在填滿資料集時關閉條件約束](turn-off-constraints-while-filling-a-dataset.md)。

## <a name="set-the-order-to-perform-updates"></a>設定執行更新的順序

設定要執行更新的順序，會設定在資料集的所有資料表中儲存所有修改過的資料時所需的個別插入、更新和刪除順序。 啟用階層式更新時，會先執行插入，然後再更新，然後再刪除。 `TableAdapterManager`提供 `UpdateOrder` 屬性，可以設定為先執行更新，然後插入然後刪除。

> [!NOTE]
> 請務必瞭解更新順序全都包含在內。 也就是說，當執行更新時，會針對資料集中的所有資料表執行插入和刪除作業。

若要設定 `UpdateOrder` 屬性，將專案從 [ [資料來源] 視窗](add-new-data-sources.md#data-sources-window) 拖曳至表單之後，請在元件匣中選取，然後在 `TableAdapterManager` `UpdateOrder` [ **屬性** ] 視窗中設定屬性。

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>執行階層式更新之前，請先建立資料集的備份複本

當您) 呼叫方法來儲存資料 (時 `TableAdapterManager.UpdateAll()` ， `TableAdapterManager` 會嘗試在單一交易中更新每個資料表的資料。 如果任何資料表的更新有任何部分失敗，則會回復整個交易。 在大部分情況下，復原會將您的應用程式傳回至其原始狀態。

但是，有時候您可能會想要從備份複本還原資料集。 當您使用自動遞增值時，可能會發生這種情況的其中一個範例。 例如，如果儲存作業不成功，就不會在資料集中重設自動遞增值，而且資料集會繼續建立自動遞增值。 這會導致您的應用程式中可能不接受的編號間距。 如果發生這種情況，則會 `TableAdapterManager` 提供 `BackupDataSetBeforeUpdate` 屬性，以便在交易失敗時，以備份複本取代現有的資料集。

> [!NOTE]
> 當方法執行時，備份複本只會在記憶體中 `TableAdapterManager.UpdateAll` 。 因此，不會以程式設計方式存取此備份資料集，因為它會取代原始資料集，或在方法執行完成時立即離開範圍 `TableAdapterManager.UpdateAll` 。

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>修改產生的儲存程式碼以執行階層式更新

呼叫 `TableAdapterManager.UpdateAll` 方法並傳入包含關聯資料表的資料集名稱，可將資料集內關聯資料表的變更儲存至資料庫。 例如，執行 `TableAdapterManager.UpdateAll(NorthwindDataset)` 方法，以將 NorthwindDataset 中所有資料表的更新傳送至後端資料庫。

從 [資料來源] 視窗置放項目後，程式碼會自動新增至 `Form_Load` 事件，以填入每個資料表 (`TableAdapter.Fill` 方法)。 程式碼也會新增至 <xref:System.Windows.Forms.BindingNavigator> 的 [儲存] 按鈕 Click 事件，以將資料集的資料存回資料庫 (`TableAdapterManager.UpdateAll` 方法)。

產生的儲存程式碼也包含一行會呼叫 `CustomersBindingSource.EndEdit` 方法的程式碼。 更具體來說，它會呼叫 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> 新增至表單的第一個方法。 換言之，只會針對從 [ **資料來源** ] 視窗拖曳至表單上的第一個資料表產生此程式碼。 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼叫會認可目前正在編輯的所有資料繫結控制項中，所有正在進行的變更。 因此，當資料繫結控制項還有焦點時，您可以按一下 [儲存] 按鈕，就會在實際儲存 (`TableAdapterManager.UpdateAll` 方法) 之前，先認可該控制項中所有暫止的編輯項目。

> [!NOTE]
> **DataSet 設計工具** 只 `BindingSource.EndEdit` 會為放置在表單上的第一個資料表加入程式碼。 因此，您必須對表單上每個關聯資料表，加入一行程式碼以呼叫 `BindingSource.EndEdit` 方法。 在此逐步說明中，這表示您必須加入 `OrdersBindingSource.EndEdit` 方法的呼叫。

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>更新程式碼以在儲存前認可關聯資料表的變更

1. 按兩下 <xref:System.Windows.Forms.BindingNavigator> 上的 [儲存] 按鈕，以在程式碼編輯器中開啟 **Form1**。

2. 在呼叫 `OrdersBindingSource.EndEdit` 方法的程式碼行後方，加入一行程式碼以呼叫 `CustomersBindingSource.EndEdit` 方法。 [儲存] 按鈕 Click 事件中的程式碼應與下列類似：

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

除了將資料儲存至資料庫前，先認可關聯子資料表的變更外，您可能也必須先認可新建立的父記錄，才能將子記錄加入至資料集。 換句話說，您可能必須先將新的父記錄 () 加入 `Customer` 至資料集，然後 foreign key 條件約束才會啟用新的子記錄 (`Orders`) 加入至資料集。 若要完成此工作，您可以使用子 `BindingSource.AddingNew` 事件。

> [!NOTE]
> 您是否必須認可新的父記錄，視用來系結至資料來源的控制項類型而定。 在這個逐步解說中，您會使用個別控制項來系結至父資料表。 這需要額外的程式碼來認可新的父記錄。 如果父記錄顯示在複雜繫結控制項中 <xref:System.Windows.Forms.DataGridView> ，例如，就 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 不需要對父記錄進行額外的呼叫。 因為控制項的基礎資料繫結功能會處理新記錄的認可。

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>加入程式碼以在新增子記錄前先認可資料集中的父記錄

1. 建立 `OrdersBindingSource.AddingNew` 事件的事件處理常式。

    - 在設計檢視中開啟 [ **Form1** ]，選取元件匣中的 [ **OrdersBindingSource** ]，在 [**屬性**] 視窗中選取 [**事件**]，然後按兩下 [ **AddingNew** ] 事件。

2. 在呼叫方法的事件處理常式中加入一行程式碼 `CustomersBindingSource.EndEdit` 。 `OrdersBindingSource_AddingNew` 事件處理常式中的程式碼應該與下列類似：

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 參考

依預設， `TableAdapterManager` 當您建立包含相關資料表的資料集時，就會產生一個類別。 若要避免產生類別，請將 `Hierarchical Update` 資料集的屬性值變更為 false。 當您將具有關聯性的資料表拖曳至 Windows Form 或 WPF 頁面的設計介面時，Visual Studio 會宣告類別的成員變數。 如果您不使用資料系結，則必須手動宣告變數。

`TableAdapterManager`類別不是 .net 類型。 因此，您無法在檔中查閱。 它是在設計階段建立的，做為資料集建立過程的一部分。

以下是類別的常用方法和屬性 `TableAdapterManager` ：

|member|描述|
|------------|-----------------|
|`UpdateAll` 方法|儲存所有資料表中的所有資料。|
|`BackUpDataSetBeforeUpdate` 屬性|判斷是否要在執行方法之前建立資料集的備份副本 `TableAdapterManager.UpdateAll` 。布林。|
|*tableName* `TableAdapter` 財產|表示 `TableAdapter` 。 產生的 `TableAdapterManager` 會包含其所管理之每個的屬性 `TableAdapter` 。 例如，具有 Customers 和 Orders 資料表的資料集會以 `TableAdapterManager` 包含和屬性的來 `CustomersTableAdapter` 產生 `OrdersTableAdapter` 。|
|`UpdateOrder` 屬性|控制個別 insert、update 和 delete 命令的順序。 將此值設定為列舉中的其中一個值 `TableAdapterManager.UpdateOrderOption` 。<br /><br /> 依預設， `UpdateOrder` 會設為 **InsertUpdateDelete**。 這表示會針對資料集中的所有資料表執行插入、更新和刪除作業。|

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
