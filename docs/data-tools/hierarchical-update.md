---
title: 階層式更新
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 442d6cd60597219c25b41f26ad8c2dc2151248ee
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747465"
---
# <a name="hierarchical-update"></a>階層式更新
*階層式更新*指儲存回資料庫的更新的資料 （從兩個或多個相關資料表的資料集），同時維護參考完整性規則的程序。 *參考完整性*指的是提供資料庫中的條件約束來控制插入、 更新和刪除相關的記錄行為的一致性規則。 比方說，它會建立客戶記錄，才能允許該客戶的訂單建立強制執行參考完整性。  如需在資料集中的關聯性的詳細資訊，請參閱[集中的關聯性](../data-tools/relationships-in-datasets.md)

 階層式更新功能會使用`TableAdapterManager`管理`TableAdapter`中具類型資料集。 `TableAdapterManager`元件是[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-產生類別，因此並不屬於[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 當您將資料表從資料來源視窗拖曳至 Windows Form 或 WPF 頁面時，Visual Studio 會將類型 TableAdapterManager 的變數加入至表單或頁面上，與您在元件匣中的設計工具中看到它。 如需詳細資訊`TableAdapterManager`類別，請參閱 TableAdapterManager 參考 > 一節[Tableadapter](../data-tools/create-and-configure-tableadapters.md)。

 根據預設，資料集視為相關的資料表 」，關聯性 」 這表示它不會強制執行 foreign key 條件約束。 您可以使用 Dataset 設計工具來修改在設計階段設定。 選取以顯示兩個資料表之間的關聯線**關聯** 對話方塊。 您所做的變更將決定 TableAdapterManager 的行為時它將變更相關的資料表中傳送回資料庫。

## <a name="enable-hierarchical-update-in-a-dataset"></a>啟用資料集內的階層式更新
 根據預設，會啟用階層式更新的新增或專案中建立的所有新資料集。 藉由設定開啟或關閉開啟的階層式更新**階層式更新**具類型的資料集，資料集屬性**True**或**False**:

 ![階層式更新設定](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>建立新的資料表之間的關聯性
 若要建立新的關聯性，兩個資料表之間，Dataset 設計工具中選取每個資料表的標題列，然後以滑鼠右鍵按一下並選取**加入關聯**。

 ![階層式更新將新增關聯功能表](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>了解 foreign key 條件約束、 階層的更新和刪除
 請務必了解如何 foreign key 條件約束和串聯資料庫中的行為會在產生的資料集程式碼中建立。

 根據預設，資料集中的資料表產生關聯性 (<xref:System.Data.DataRelation>)，符合資料庫中的關聯性。 不過，在資料集中的關聯性不會產生做為外部索引鍵條件約束。 <xref:System.Data.DataRelation>設定為**只關聯**沒有<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>或<xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>作用中。

 根據預設，階層式更新和串聯刪除已關閉，即使資料庫關聯性會以階層式更新來設定及/或串聯刪除。 例如，建立新的客戶和新的訂單，然後嘗試將資料儲存可能會造成衝突資料庫所定義的外部索引鍵條件約束。 如需詳細資訊，請參閱[填入 dataset 時關閉條件約束](turn-off-constraints-while-filling-a-dataset.md)。

## <a name="set-the-order-to-perform-updates"></a>設定執行更新的順序
 設定的順序來執行更新設定的個別訂單插入、 更新和刪除，才能儲存修改過的所有資料集的所有資料表中。 啟用階層式更新時，插入會執行第一次，然後更新，然後再刪除。 `TableAdapterManager`提供`UpdateOrder`屬性，可以是設定為第一次，執行更新，然後插入和刪除。

> [!NOTE]
>  請務必了解更新順序是包含所有角色。 也就是更新執行時，插入和刪除執行中的資料集的所有資料表。

 若要設定`UpdateOrder`屬性中，拖曳的項目之後[資料來源視窗](add-new-data-sources.md)到表單上，選取`TableAdapterManager`在元件匣中，並將其設定`UpdateOrder`中的屬性**屬性**視窗。

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>執行階層式更新之前先建立資料集的備份副本
 當您儲存資料時 (藉由呼叫`TableAdapterManager.UpdateAll()`方法)，則`TableAdapterManager`嘗試更新在單一交易中每個資料表的資料。 如果更新任何資料表的任何部分失敗，會回復整個交易。 在大部分情況下，復原會傳回您的應用程式至其原始狀態。

 不過，有時候您可能想要從備份副本還原資料集。 當您使用自動遞增值，可能會發生這樣的其中一個範例。 例如，如果儲存作業未順利完成，不會在資料集中，會重設自動遞增的值，而且資料集繼續建立自動遞增的值。這會保留中編號的可能無法使用應用程式中的間距。 中的情況下這是有問題，其中`TableAdapterManager`提供`BackupDataSetBeforeUpdate`若交易失敗，以備份取代現有的資料集的屬性。

> [!NOTE]
>  備份副本是只能在時記憶體中`TableAdapterManager.UpdateAll`方法是否執行。 因此，沒有任何以程式設計方式存取此備份的資料集，因為它會取代原始資料集，或超出範圍儘速`TableAdapterManager.UpdateAll`方法完成執行。

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>修改產生的儲存程式碼以執行階層式更新
 呼叫 `TableAdapterManager.UpdateAll` 方法並傳入包含關聯資料表的資料集名稱，可將資料集內關聯資料表的變更儲存至資料庫。 例如，執行 `TableAdapterManager.UpdateAll(NorthwindDataset)` 方法，以將 NorthwindDataset 中所有資料表的更新傳送至後端資料庫。

 您卸除的項目之後**資料來源**視窗中，程式碼會自動加入至`Form_Load`事件，以填入每個資料表 (`TableAdapter.Fill`方法)。 程式碼也會加入至**儲存**按鈕的 click 事件的<xref:System.Windows.Forms.BindingNavigator>，將資料從資料集儲存回資料庫 (`TableAdapterManager.UpdateAll`方法)。

 產生的儲存程式碼也包含一行會呼叫 `CustomersBindingSource.EndEdit` 方法的程式碼。 更具體來說，它會呼叫<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法的第一個<xref:System.Windows.Forms.BindingSource>加入至表單。 換句話說，此程式碼只會產生第一個資料表是指從拖曳**資料來源**視窗拖曳至表單。 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼叫會認可目前正在編輯的所有資料繫結控制項中，所有正在進行的變更。 因此，如果資料繫結控制項還有焦點時，您可以按一下**儲存**按鈕，所有暫止的編輯控制項之前，在實際儲存先認可，(`TableAdapterManager.UpdateAll`方法)。

> [!NOTE]
>  Dataset 設計工具只會加入`BindingSource.EndEdit`放置在表單的第一個資料表的程式碼。 因此，您必須對表單上每個關聯資料表，加入一行程式碼以呼叫 `BindingSource.EndEdit` 方法。 在此逐步說明中，這表示您必須加入 `OrdersBindingSource.EndEdit` 方法的呼叫。

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>更新程式碼以在儲存前認可關聯資料表的變更

1.  按兩下**儲存**按鈕<xref:System.Windows.Forms.BindingNavigator>開啟**Form1**在程式碼編輯器。

2.  在呼叫 `OrdersBindingSource.EndEdit` 方法的程式碼行後方，加入一行程式碼以呼叫 `CustomersBindingSource.EndEdit` 方法。 中的程式碼**儲存**按鈕 click 事件應該類似如下：

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

除了將資料儲存至資料庫前，先認可關聯子資料表的變更外，您可能也必須先認可新建立的父記錄，才能將子記錄加入至資料集。 換言之，您可能必須先將新的父記錄 (Customer) 加入至資料集，外部索引鍵條件約束才會允許新的子記錄 (Orders) 加入至資料集。 若要完成此工作，您可以使用子 `BindingSource.AddingNew` 事件。

> [!NOTE]
> 您是否必須認可新的父記錄取決於用來繫結至資料來源的控制項類型。 在本逐步解說中，您可以使用個別控制項繫結至父資料表。 這需要額外的程式碼來認可新的父記錄。 若父記錄改為顯示在複雜繫結控制項，例如<xref:System.Windows.Forms.DataGridView>、 額外<xref:System.Windows.Forms.BindingSource.EndEdit%2A>呼叫父記錄就不一定需要。 因為控制項的基礎資料繫結功能會處理新記錄的認可。

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>加入程式碼以在新增子記錄前先認可資料集中的父記錄

1.  建立 `OrdersBindingSource.AddingNew` 事件的事件處理常式。

    -   開啟**Form1**在設計檢視中，選取**OrdersBindingSource**在元件匣中，選取**事件**中**屬性**視窗中，並然後按兩下**AddingNew**事件。

2.  呼叫事件處理常式中加入一行程式碼`CustomersBindingSource.EndEdit`方法。 `OrdersBindingSource_AddingNew` 事件處理常式中的程式碼應該與下列類似：

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 參考
 根據預設，`TableAdapterManager`當您建立包含相關的資料表的資料集時，會產生類別。 若要防止產生的類別，將變更的值`Hierarchical Update`屬性為 false 的資料集。 當您拖曳到設計介面上的 Windows Form 或 WPF 頁面產生關聯的資料表時，Visual Studio 會宣告類別的成員變數。 如果您不使用資料繫結，您必須以手動方式將變數宣告。

 `TableAdapterManager`類別不是屬於[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 因此，您無法查詢文件中。 它會建立在設計階段做為資料集的建立程序的一部分。

 以下是常用的方法和屬性的`TableAdapterManager`類別：

|成員|描述|
|------------|-----------------|
|`UpdateAll` 方法|所有資料表的資料儲存所有資料。|
|`BackUpDataSetBeforeUpdate` 屬性|決定是否要建立資料集的備份副本，再執行`TableAdapterManager.UpdateAll`方法。布林值。|
|*tableName* `TableAdapter`屬性|代表`TableAdapter`。 產生`TableAdapterManager`屬性包含每個`TableAdapter`其所管理。 例如，與客戶和訂單資料表的資料集就會產生含有`TableAdapterManager`包含`CustomersTableAdapter`和`OrdersTableAdapter`屬性。|
|`UpdateOrder` 屬性|控制個別 insert、 update 和 delete 命令的順序。 將此設定中的值的其中一個`TableAdapterManager.UpdateOrderOption`列舉型別。<br /><br /> 根據預設，`UpdateOrder`設**InsertUpdateDelete**。 這表示它會插入，則會更新，然後刪除執行中的資料集的所有資料表。|

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)