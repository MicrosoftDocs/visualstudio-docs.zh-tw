---
title: 階層式更新 |Microsoft Docs
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99e19bce34c2bc8578a062c87aaef10302589075
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670027"
---
# <a name="hierarchical-update"></a>階層式更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

階層式更新 * 指的是將更新的資料（從包含兩個或多個相關資料表的資料集）傳回資料庫，同時維護參考完整性規則的程式。 *參考完整性*指的是資料庫中的條件約束所提供的一致性規則，可控制插入、更新和刪除相關記錄的行為。 例如，它的參考完整性會強制建立客戶記錄，然後才允許為該客戶建立訂單。  如需資料集中關聯性的詳細資訊，請參閱[資料集中的關聯](../data-tools/relationships-in-datasets.md)性

 階層式更新功能會使用 `TableAdapterManager` 來管理具型別資料集中的 `TableAdapter`s。 @No__t_0 元件是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 產生的類別，因此它不是 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的一部分。 當您從 [資料來源] 視窗將資料表拖曳至 Windows Form 或 WPF 頁面時，Visual Studio 會將 TableAdapterManager 類型的變數新增至表單或頁面，而您會在元件匣的設計工具中看到它。 如需有關 `TableAdapterManager` 類別的詳細資訊，請參閱[TableAdapterManager 總覽](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)的 TableAdapterManager 參考一節。

 根據預設，資料集會將相關的資料表視為「僅限關聯」，這表示它不會強制執行 foreign key 條件約束。 您可以在設計階段使用 DataSet 設計工具來修改該設定。 選取兩個數據表之間的關聯線，以顯示 [**關聯**] 對話方塊。 您在此所做的變更將決定 TableAdapterManager 在將相關資料表中的變更傳送回資料庫時的行為。

## <a name="enablehierarchical-update-in-a-dataset"></a>資料集中的 Enablehierarchical 更新
 根據預設，會針對在專案中新增或建立的所有新資料集啟用階層式更新。 在 DataSet 設計工具中將具類型資料集的**階層式更新**屬性設定為**True**或**False**，以開啟或關閉階層式更新：

 ![階層式更新設定](../data-tools/media/hierarchical-update-setting.png "階層式更新設定")

## <a name="create-a-new-relation-between-tables"></a>建立資料表之間的新關聯性
 若要建立兩個數據表之間的新關聯，請在 DataSet 設計工具中，選取每個資料表的標題列，然後按一下滑鼠右鍵並選取 **加入關聯**。

 ![階層式更新新增關聯功能表](../data-tools/media/hierarchical-update-add-relation-menu.png "階層式更新新增關聯功能表")

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>瞭解外鍵條件約束、串聯式更新和刪除
 請務必瞭解如何在產生的資料集程式碼中建立資料庫中的外鍵條件約束和串聯行為。

 根據預設，系統會使用符合資料庫中關聯性的關聯性（<xref:System.Data.DataRelation>）來產生資料集內的資料表。 不過，資料集中的關聯性不會產生為外鍵條件約束。 只有在沒有 <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> 或 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> 生效時，才會將 <xref:System.Data.DataRelation> 設定為**關聯**性。

 根據預設，即使資料庫關聯性是以串聯式更新和/或串聯式刪除功能來設定，串聯式更新和串聯刪除也會關閉。 例如，建立新的客戶和新的訂單，然後嘗試儲存資料，可能會與資料庫中定義的外鍵條件約束髮生衝突。 如需詳細資訊，請參閱[如何：設定資料集中的外鍵條件約束](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e)。

## <a name="set-the-order-to-perform-updates"></a>設定要執行更新的順序
 設定執行更新的順序會設定在資料集的所有資料表中儲存所有已修改資料所需的個別插入、更新和刪除的順序。 啟用階層式更新時，會先執行插入，然後再更新，然後再刪除。 @No__t_0 提供 `UpdateOrder` 屬性，可以設定為先執行更新，然後再插入，然後再刪除。

> [!NOTE]
> 請務必瞭解更新順序全都包含在內。 也就是說，當執行更新時，會針對資料集中的所有資料表執行插入，然後刪除。

 若要設定 `UpdateOrder` 屬性，請在將專案從 [[資料來源] 視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)拖曳至表單之後，選取元件匣中的 `TableAdapterManager`，然後在 [**屬性**] 視窗中設定 [`UpdateOrder`] 屬性。 如需詳細資訊，請參閱[如何：設定執行階層式更新時的順序](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83)。

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>執行階層式更新之前，請先建立資料集的備份複本
 當您儲存資料（藉由呼叫 `TableAdapterManager.UpdateAll()` 方法）時，`TableAdapterManager` 會嘗試在單一交易中更新每個資料表的資料。 如果任何資料表的更新有任何部分失敗，則會回復整個交易。 在大部分情況下，復原會將您的應用程式恢復為其原始狀態。

 不過，有時候您可能會想要從備份副本還原資料集。 當您使用自動遞增值時，可能會發生這種情況的其中一個範例。 例如，如果儲存作業不成功，就不會在資料集中重設自動遞增值，而且資料集會繼續建立自動遞增的值。這會導致您的應用程式中可能無法接受的編號間隔。 在發生這種問題的情況下，`TableAdapterManager` 會提供 `BackupDataSetBeforeUpdate` 屬性，以在交易失敗時，以備份複本取代現有的資料集。

> [!NOTE]
> 只有在 `TableAdapterManager.UpdateAll` 方法正在執行時，備份副本才會在記憶體中。 因此，不會以程式設計方式存取此備份資料集，因為它會在 `TableAdapterManager.UpdateAll` 方法完成執行之後，取代原始資料集或移出範圍。

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>修改產生的儲存程式碼以執行階層式更新
 呼叫 `TableAdapterManager.UpdateAll` 方法並傳入包含關聯資料表的資料集名稱，可將資料集內關聯資料表的變更儲存至資料庫。 例如，執行 `TableAdapterManager.UpdateAll(NorthwindDataset)` 方法，以將 NorthwindDataset 中所有資料表的更新傳送至後端資料庫。

 從 [資料來源] 視窗置放項目後，程式碼會自動新增至 `Form_Load` 事件，以填入每個資料表 (`TableAdapter.Fill` 方法)。 程式碼也會新增至 <xref:System.Windows.Forms.BindingNavigator> 的 [儲存] 按鈕 Click 事件，以將資料集的資料存回資料庫 (`TableAdapterManager.UpdateAll` 方法)。

 產生的儲存程式碼也包含一行會呼叫 `CustomersBindingSource.EndEdit` 方法的程式碼。 更具體來說，它會呼叫第一個 <xref:System.Windows.Forms.BindingSource>that 新增至表單的 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法。 換句話說，只會針對從 [**資料來源**] 視窗拖曳至表單上的第一個資料表產生此程式碼。 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼叫會認可目前正在編輯的所有資料繫結控制項中，所有正在進行的變更。 因此，當資料繫結控制項還有焦點時，您可以按一下 [儲存] 按鈕，就會在實際儲存 (`TableAdapterManager.UpdateAll` 方法) 之前，先認可該控制項中所有暫止的編輯項目。

> [!NOTE]
> DataSet 設計工具只會針對第一個放入表單上的資料表加入 `BindingSource.EndEdit` 程式碼。 因此，您必須對表單上每個關聯資料表，加入一行程式碼以呼叫 `BindingSource.EndEdit` 方法。 在此逐步說明中，這表示您必須加入 `OrdersBindingSource.EndEdit` 方法的呼叫。

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>更新程式碼以在儲存前認可關聯資料表的變更

1. 按兩下 <xref:System.Windows.Forms.BindingNavigator> 上的 [儲存] 按鈕，以在程式碼編輯器中開啟 **Form1**。

2. 在呼叫 `OrdersBindingSource.EndEdit` 方法的程式碼行後方，加入一行程式碼以呼叫 `CustomersBindingSource.EndEdit` 方法。 [儲存] 按鈕 Click 事件中的程式碼應與下列類似：

    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]

   除了將資料儲存至資料庫前，先認可關聯子資料表的變更外，您可能也必須先認可新建立的父記錄，才能將子記錄加入至資料集。 換言之，您可能必須先將新的父記錄 (Customer) 加入至資料集，外部索引鍵條件約束才會允許新的子記錄 (Orders) 加入至資料集。 若要完成此工作，您可以使用子 `BindingSource.AddingNew` 事件。

> [!NOTE]
> 您是否必須認可新的父記錄，取決於用來系結至資料來源的控制項類型。 在此逐步解說中，您會使用個別的控制項來系結至父資料表。 這需要額外的程式碼來認可新的父記錄。 如果父記錄改為顯示在複雜繫結控制項中，例如 <xref:System.Windows.Forms.DataGridView>，則不需要為父記錄進行這個額外的 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼叫。 因為控制項的基礎資料繫結功能會處理新記錄的認可。

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>加入程式碼以在新增子記錄前先認可資料集中的父記錄

1. 建立 `OrdersBindingSource.AddingNew` 事件的事件處理常式。

    - 在設計檢視中開啟**Form1** ，選取元件匣中的 [ **OrdersBindingSource** ]，選取 [**屬性**] 視窗中的 [**事件**]，然後按兩下 [ **AddingNew** ] 事件。

2. 將一行程式碼加入至呼叫 `CustomersBindingSource.EndEdit` 方法的事件處理常式。 `OrdersBindingSource_AddingNew` 事件處理常式中的程式碼應該與下列類似：

     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 參考
 根據預設，當您建立包含相關資料表的資料集時，會產生 `TableAdapterManager` 類別。 若要防止產生類別，請將資料集的 [`Hierarchical Update`] 屬性值變更為 [false]。 當您將具有關聯性的資料表拖曳至 Windows Form 或 WPF 頁面的設計介面時，Visual Studio 會宣告類別的成員變數。 如果您不使用資料系結，就必須手動宣告變數。

 @No__t_0 類別不是 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的一部分。 因此，您無法在檔中查閱。 它是在設計階段建立，做為資料集建立過程的一部分。

 以下是 `TableAdapterManager` 類別的常用方法和屬性：

|成員|描述|
|------------|-----------------|
|`UpdateAll` 方法|儲存所有資料表的所有資料。|
|`BackUpDataSetBeforeUpdate` 屬性|決定在執行 `TableAdapterManager.UpdateAll` 方法之前，是否要建立資料集的備份複本。True.|
|*tableName* `TableAdapter` 屬性|表示 `TableAdapter`。 產生的 `TableAdapterManager` 包含其所管理之每個 `TableAdapter` 的屬性。 例如，具有 Customers 和 Orders 資料表的資料集會使用包含 `CustomersTableAdapter` 和 `OrdersTableAdapter` 屬性的 `TableAdapterManager` 來產生。|
|`UpdateOrder` 屬性|控制個別 insert、update 和 delete 命令的順序。 將此設定為 `TableAdapterManager.UpdateOrderOption` 列舉中的其中一個值。<br /><br /> 根據預設，`UpdateOrder` 會設定為**InsertUpdateDelete**。 這表示會針對資料集內的所有資料表執行插入、更新和刪除作業。 如需詳細資訊，請參閱[如何：設定執行階層式更新時的順序](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83)。|

## <a name="see-also"></a>請參閱
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
