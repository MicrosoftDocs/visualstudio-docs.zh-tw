---
title: 將資料儲存回資料庫
description: 使用資料集工具將資料儲存回資料庫。 資料集是記憶體中的資料複本，如果已修改，則應該儲存回資料庫。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: bdbfba867fd1fa898ff376d3d1e60f33f58c32a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866589"
---
# <a name="save-data-back-to-the-database"></a>將資料儲存回資料庫

資料集是記憶體中的資料複本。 如果您修改該資料，最好將這些變更儲存回資料庫。 您可以透過下列三種方式之一來執行此動作：

- 藉由呼叫 TableAdapter 的其中一個 `Update` 方法

- 藉由呼叫 TableAdapter 的其中一個 `DBDirect` 方法

- `UpdateAll`當資料集包含與資料集中其他資料表相關的資料表時，呼叫 TableAdapterManager 上 Visual Studio 為您產生的方法

當您將資料集資料表系結至 Windows Form 或 XAML 頁面上的控制項時，資料系結架構會為您執行所有工作。

如果您很熟悉 Tableadapter，可以直接跳到下列其中一個主題：

|主題|描述|
|-----------|-----------------|
|[在資料庫中插入新的記錄](../data-tools/insert-new-records-into-a-database.md)|如何使用 Tableadapter 或命令物件執行更新和插入|
|[使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)|如何使用 Tableadapter 執行更新|
|[階層式更新](../data-tools/hierarchical-update.md)|如何從包含兩個或多個相關資料表的資料集執行更新|
|[處理並行例外狀況](../data-tools/handle-a-concurrency-exception.md)|當兩位使用者同時嘗試變更資料庫中的相同資料時，如何處理例外狀況|
|[如何：使用交易儲存資料](../data-tools/save-data-by-using-a-transaction.md)|如何使用系統將資料儲存在交易中。 交易命名空間和 TransactionScope 物件|
|[儲存異動中的資料](../data-tools/save-data-in-a-transaction.md)|建立 Windows Forms 應用程式的逐步解說，以示範如何將資料儲存至交易內的資料庫|
|[將資料儲存至資料庫 (多個資料表)](../data-tools/save-data-to-a-database-multiple-tables.md)|如何編輯記錄，並將多個資料表中的變更儲存回資料庫|
|[從物件中將資料儲存至資料庫](../data-tools/save-data-from-an-object-to-a-database.md)|如何使用 TableAdapter DbDirect 方法，將資料從不在資料集內的物件傳遞至資料庫|
|[使用 TableAdapter DBDirect 方法儲存資料](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|如何使用 TableAdapter 將 SQL 查詢直接傳送至資料庫|
|[將資料集儲存為 XML](../data-tools/save-a-dataset-as-xml.md)|如何將資料集儲存至 XML 檔|

## <a name="two-stage-updates"></a>兩階段更新

更新資料來源的程式有兩個步驟。 第一個步驟是使用新的記錄、變更的記錄或已刪除的記錄來更新資料集。 如果您的應用程式永遠不會將這些變更傳送回資料來源，則您已經完成更新。

如果您將變更傳送回資料庫，則需要第二個步驟。 如果您不是使用資料繫結控制項，則必須手動呼叫 `Update` 相同 TableAdapter (的方法，或您用來填入資料集的資料配接器) 。 不過，您也可以使用不同的介面卡，例如，將資料從某個資料來源移動到另一個資料來源，或更新多個資料來源。 如果您不是使用資料系結，而且正在儲存相關資料表的變更，您必須手動具現化自動產生之類別的變數 `TableAdapterManager` ，然後呼叫其 `UpdateAll` 方法。

![資料集更新的概念圖](../data-tools/media/vbdatasetupdates.gif)

資料集包含資料表的集合，其中包含資料列集合。 如果您想要稍後更新基礎資料來源，則必須在 `DataTable.DataRowCollection` 加入或移除資料列時，對屬性使用方法。 這些方法會執行更新資料來源所需的變更追蹤。 如果您在 `RemoveAt` Rows 屬性上呼叫集合，則不會將刪除動作傳回到資料庫。

## <a name="merge-datasets"></a>合併資料集

您可以將資料集與另一個資料集 *合併* ，藉以更新資料集的內容。 這包括將 *源* 資料集的內容複寫到呼叫的資料集 (稱為 *目標* 資料集) 。 當您合併資料集時，源資料集中的新記錄會加入至目標資料集。 此外，也會將源資料集中的額外資料行加入至目標資料集。 當您有本機資料集，並從另一個應用程式取得第二個資料集時，合併資料集會很有用。 當您從元件（例如 XML web service）取得第二個資料集，或當您需要整合多個資料集的資料時，它也很有用。

合併資料集時，您可以傳遞布林值引數 (`preserveChanges`) ，告知 <xref:System.Data.DataSet.Merge%2A> 方法是否要在目標資料集中保留現有的修改。 因為資料集會維護多個版本的記錄，所以請務必記住，合併的記錄有多個版本。 下表顯示如何合併兩個資料集中的記錄：

|DataRowVersion|目標資料集|來源資料集|
| - | - | - |
|原始|James Wilson|James C. Wilson|
|目前|Jim Wilson|James C. Wilson|

在 <xref:System.Data.DataSet.Merge%2A> 上表中呼叫方法時，會 `preserveChanges=false targetDataset.Merge(sourceDataset)` 產生下列資料：

|DataRowVersion|目標資料集|來源資料集|
| - | - | - |
|原始|James C. Wilson|James C. Wilson|
|目前|James C. Wilson|James C. Wilson|

呼叫 <xref:System.Data.DataSet.Merge%2A> 方法時，會 `preserveChanges = true targetDataset.Merge(sourceDataset, true)` 產生下列資料：

|DataRowVersion|目標資料集|來源資料集|
| - | - | - |
|原始|James C. Wilson|James C. Wilson|
|目前|Jim Wilson|James C. Wilson|

> [!CAUTION]
> 在此 `preserveChanges = true` 案例中，如果在 <xref:System.Data.DataSet.RejectChanges%2A> 目標資料集中的記錄上呼叫方法，則會還原為 *源* 資料集的原始資料。 這表示，如果您嘗試以目標資料集更新原始資料來源，它可能找不到要更新的原始資料列。 您可以使用資料來源中的更新記錄來填滿另一個資料集，然後執行合併以防止平行存取違規，以防止平行存取違規。 當資料集填滿之後，當其他使用者修改資料來源中的記錄時，就會發生並行違規 (。 ) 

## <a name="update-constraints"></a>更新條件約束

若要對現有的資料列進行變更，請在個別資料行中新增或更新資料。 如果資料集包含 (之類的條件約束，例如外鍵或不可為 null 的條件約束) ，則當您更新記錄時，可能會暫時處於錯誤狀態。 也就是說，在您完成更新一個資料行之後，但在進入下一個資料行之前，它可能會處於錯誤狀態。

為了避免過早的條件約束違規，您可以暫時暫停更新條件約束。 這有兩個目的：

- 它可防止在您完成更新一個資料行，但尚未開始更新另一個資料行之後擲回錯誤。

- 它會防止某些更新事件被引發 (經常用於驗證) 的事件。

> [!NOTE]
> 在 Windows Forms 中，datagrid 內建的資料系結架構會暫停條件約束檢查，直到焦點移出資料列，而且您不需要明確地呼叫 <xref:System.Data.DataRow.BeginEdit%2A> 、 <xref:System.Data.DataRow.EndEdit%2A> 或 <xref:System.Data.DataRow.CancelEdit%2A> 方法。

在資料集上叫用方法時，會自動停用條件約束 <xref:System.Data.DataSet.Merge%2A> 。 當合併完成時，如果無法啟用的資料集有任何條件約束，則會擲回 <xref:System.Data.ConstraintException> 。 在這種情況下， <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性會設定為， `false,` 而且必須先解決所有條件約束違規，才能將屬性重設 <xref:System.Data.DataSet.EnforceConstraints%2A> 為 `true` 。

完成更新之後，您可以重新啟用條件約束檢查，這也會重新啟用 update 事件並引發它們。

如需暫停事件的詳細資訊，請參閱 [在填滿資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。

## <a name="dataset-update-errors"></a>資料集更新錯誤

當您更新資料集中的記錄時，可能發生錯誤。 例如，您可能會不小心將錯誤類型的資料寫入資料行，或資料太長，或是有其他完整性問題的資料。 或者，您可能有應用程式特定的驗證檢查，可能會在 update 事件的任何階段引發自訂錯誤。 如需詳細資訊，請參閱 [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)。

## <a name="maintain-information-about-changes"></a>維護變更的相關資訊

資料集中變更的相關資訊會以兩種方式進行維護：藉由標示指出這些變更 () 的資料列 <xref:System.Data.DataRow.RowState%2A> ，以及將記錄的多個複本保留 (<xref:System.Data.DataRowVersion>) 。 藉由使用這項資訊，處理常式可判斷資料集內的變更，並可將適當的更新傳送至資料來源。

### <a name="rowstate-property"></a>RowState 屬性

<xref:System.Data.DataRow.RowState%2A>物件的屬性 <xref:System.Data.DataRow> 是一個值，提供特定資料列狀態的相關資訊。

下表詳細說明列舉的可能值 <xref:System.Data.DataRowState> ：

|DataRowState 值|Description|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|資料列已加入做為的專案 <xref:System.Data.DataRowCollection> 。  (此狀態的資料列沒有對應的原始版本，因為在呼叫最後一個方法時，它不存在 <xref:System.Data.DataRow.AcceptChanges%2A>) 。|
|<xref:System.Data.DataRowState.Deleted>|使用物件的來刪除資料列 <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow> 。|
|<xref:System.Data.DataRowState.Detached>|資料列已建立，但它不屬於任何 <xref:System.Data.DataRowCollection>。 <xref:System.Data.DataRow>物件在建立之後、加入集合之前，以及從集合中移除之後，都會立即處於此狀態。|
|<xref:System.Data.DataRowState.Modified>|資料列中的資料行值已在某些方面變更。|
|<xref:System.Data.DataRowState.Unchanged>|資料列從上次呼叫 <xref:System.Data.DataRow.AcceptChanges%2A> 之後就未變更。|

### <a name="datarowversion-enumeration"></a>DataRowVersion 列舉

資料集會維護多個版本的記錄。 <xref:System.Data.DataRowVersion> <xref:System.Data.DataRow> 使用 <xref:System.Data.DataRow.Item%2A> 屬性或物件的方法來抓取中找到的值時，會使用這些欄位 <xref:System.Data.DataRow.GetChildRows%2A> <xref:System.Data.DataRow> 。

下表詳細說明列舉的可能值 <xref:System.Data.DataRowVersion> ：

|DataRowVersion 值|Description|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|記錄的目前版本包含自上次呼叫後對記錄執行的所有修改 <xref:System.Data.DataRow.AcceptChanges%2A> 。 如果資料列已刪除，則沒有目前的版本。|
|<xref:System.Data.DataRowVersion.Default>|記錄的預設值，如資料集架構或資料來源所定義。|
|<xref:System.Data.DataRowVersion.Original>|記錄的原始版本是上次在資料集中認可變更時的記錄複本。 實際上，這通常是從資料來源讀取的記錄版本。|
|<xref:System.Data.DataRowVersion.Proposed>|當您在更新期間（也就是在您呼叫方法和方法之間）暫時可用之記錄的建議版本 <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> 。 您通常會在事件（例如）的處理常式中，存取建議的記錄版本 <xref:System.Data.DataTable.RowChanging> 。 叫用 <xref:System.Data.DataRow.CancelEdit%2A> 方法會反轉變更，並刪除建議的資料列版本。|

當更新資訊傳送到資料來源時，原始和目前的版本會很有用。 一般來說，將更新傳送至資料來源時，資料庫的新資訊會在目前的記錄版本中。 原始版本的資訊會用來尋找要更新的記錄。

例如，在記錄的主鍵變更的情況下，您需要在資料來源中找出正確記錄的方法，以便更新變更。 如果沒有原始版本存在，則記錄最有可能附加至資料來源，而不只是在額外的不必要記錄中，而是在一筆記錄中不正確且過期。 這兩個版本也會用於並行控制中。 您可以將原始版本與資料來源中的記錄進行比較，以判斷記錄在載入資料集之後是否已變更。

當您需要先執行驗證，才能實際將變更提交至資料集時，建議的版本會很有用。

即使記錄已經變更，也不一定會有該資料列的原始或目前版本。 當您在資料表中插入新的資料列時，沒有任何原始版本，只有目前的版本。 同樣地，如果您藉由呼叫資料表的方法來刪除資料列 `Delete` ，則會有原始版本，但沒有目前的版本。

您可以藉由查詢資料列的方法，測試是否有特定版本的記錄存在 <xref:System.Data.DataRow.HasVersion%2A> 。 <xref:System.Data.DataRowVersion>當您要求資料行的值時，您可以將列舉值傳遞為選擇性引數，以存取任一版本的記錄。

## <a name="get-changed-records"></a>取得變更的記錄

不會更新資料集中的每一筆記錄，這是很常見的作法。 例如，使用者可能會使用 <xref:System.Windows.Forms.DataGridView> 顯示許多記錄的 Windows Forms 控制項。 不過，使用者可能只會更新一些記錄、刪除一個記錄，然後插入一個新的記錄。 資料集和資料表會提供方法 (`GetChanges`) ，以便只傳回已修改的資料列。

您可以使用 `GetChanges` 資料表格 (<xref:System.Data.DataTable.GetChanges%2A>) 或資料集 () 本身的方法，來建立已變更記錄的子集 <xref:System.Data.DataSet.GetChanges%2A> 。 如果您呼叫資料表的方法，它只會傳回一份資料表，其中包含已變更的記錄。 同樣地，如果您在資料集上呼叫方法，則會取得新的資料集，其中只包含變更的記錄。

`GetChanges` 本身會傳回所有變更的記錄。 相反地，藉由將所需的 <xref:System.Data.DataRowState> 參數傳遞至 `GetChanges` 方法，您可以指定想要的已變更記錄子集：新增的記錄、標示為刪除的記錄、卸離的記錄，或修改過的記錄。

當您想要將記錄傳送至另一個元件進行處理時，取得已變更記錄的子集會很有用。 與其傳送整個資料集，您可以藉由只取得元件所需的記錄來減少與其他元件通訊的額外負荷。

## <a name="commit-changes-in-the-dataset"></a>認可資料集中的變更

在資料集中進行變更時， <xref:System.Data.DataRow.RowState%2A> 會設定已變更資料列的屬性。 原始和目前版本的記錄是由屬性所建立、維護和提供給您 <xref:System.Data.DataRowView.RowVersion%2A> 。 將正確的更新傳送至資料來源時，需要儲存在這些變更資料列之屬性中的中繼資料。

如果變更反映資料來源的目前狀態，您就不再需要維護這項資訊。 一般而言，資料集和其來源同步時有兩次：

- 當您將資訊載入資料集後（例如從來源讀取資料時）。

- 將資料集的變更傳送到資料來源之後 (但不是之前，因為您會遺失將變更傳送至資料庫) 所需的變更資訊。

您可以藉由呼叫方法，將暫止的變更認可至資料集 <xref:System.Data.DataSet.AcceptChanges%2A> 。 通常 <xref:System.Data.DataSet.AcceptChanges%2A> 會在下列時間呼叫：

- 載入資料集之後。 如果您藉由呼叫 TableAdapter 的方法來載入資料集 `Fill` ，則介面卡會自動為您認可變更。 但是，如果您藉由將另一個資料集合併到其中來載入資料集，則您必須手動認可變更。

    > [!NOTE]
    > 您可以 `Fill` 將介面卡的屬性設定為，以防止介面卡在您呼叫方法時自動認可變更 `AcceptChangesDuringFill` `false` 。 如果設定為 `false` ，則在 <xref:System.Data.DataRow.RowState%2A> 填滿期間插入的每個資料列的都會設定為 <xref:System.Data.DataRowState.Added> 。

- 將資料集變更傳送到另一個進程之後，例如 XML web service。

    > [!CAUTION]
    > 以這種方式認可變更會清除任何變更資訊。 在您完成執行需要應用程式知道資料集內已進行變更的作業之前，請勿認可變更。

這個方法會完成下列動作：

- 將 <xref:System.Data.DataRowVersion.Current> 記錄的版本寫入至其 <xref:System.Data.DataRowVersion.Original> 版本，並覆寫原始版本。

- 移除屬性設為的任何資料列 <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> 。

- 將 <xref:System.Data.DataRow.RowState%2A> 記錄的屬性設定為 <xref:System.Data.DataRowState.Unchanged> 。

<xref:System.Data.DataSet.AcceptChanges%2A>方法可在三個層級上使用。 您可以在物件上呼叫它， <xref:System.Data.DataRow> 只認可該資料列的變更。 您也可以在物件上呼叫它 <xref:System.Data.DataTable> ，以認可資料表中的所有資料列。 最後，您可以在物件上呼叫它， <xref:System.Data.DataSet> 以在資料集的所有資料表的所有記錄中認可所有暫止的變更。

下表說明哪些變更會根據呼叫方法的物件來認可：

|方法|結果|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|只有特定資料列才會認可變更。|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|變更會在特定資料表中的所有資料列上認可。|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|變更是在資料集的所有資料表中的所有資料列上進行認可。|

> [!NOTE]
> 如果您藉由呼叫 TableAdapter 的方法來載入資料集 `Fill` ，就不需要明確地接受變更。 根據預設， `Fill` 方法 `AcceptChanges` 會在完成填入資料表之後呼叫方法。

相關的方法，會將 <xref:System.Data.DataSet.RejectChanges%2A> 版本複製回記錄的版本，以復原變更的效果 <xref:System.Data.DataRowVersion.Original> <xref:System.Data.DataRowVersion.Current> 。 它也會將 <xref:System.Data.DataRow.RowState%2A> 每一筆記錄的重新設定為 <xref:System.Data.DataRowState.Unchanged> 。

## <a name="data-validation"></a>資料驗證

為了確認您的應用程式中的資料符合傳遞給它的處理常式需求，您通常需要新增驗證。 這可能牽涉到檢查使用者的表單中的專案是否正確、驗證由另一個應用程式傳送給您應用程式的資料，或甚至是檢查元件中所計算的資訊是否落在資料來源和應用程式需求的條件約束中。

您可以透過數種方式來驗證資料：

- 在商務層中，將程式碼加入至您的應用程式以驗證資料。 資料集是您可以進行這項作業的一個地方。 資料集提供後端驗證的一些優點，例如在資料行和資料列值變更時驗證變更的能力。 如需詳細資訊，請參閱 [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)。

- 在展示層中，藉由將驗證新增至表單。 如需詳細資訊，請參閱 [Windows Forms 中的使用者輸入驗證](/dotnet/framework/winforms/user-input-validation-in-windows-forms)。

- 在資料後端中，將資料傳送到資料來源（例如資料庫），並允許它接受或拒絕資料。 如果您使用的資料庫具有精密的功能來驗證資料並提供錯誤資訊，這可能是一種實用的方法，因為不論資料位於何處，都可以驗證資料。 不過，這種方法可能無法容納應用程式特定的驗證需求。 此外，擁有資料來源驗證資料可能會導致大量往返資料來源，這取決於您的應用程式如何協助解決後端所引發的驗證錯誤。

   > [!IMPORTANT]
   > 使用具有 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 設定為之屬性的資料命令時 <xref:System.Data.CommandType.Text> ，請仔細檢查從用戶端傳送的資訊，再將其傳遞至您的資料庫。 惡意使用者可能會嘗試傳送 (插入) 修改過或額外的 SQL 陳述式，以獲得未授權的存取或破壞資料庫。 將使用者輸入傳送至資料庫之前，請務必確認該資訊是否有效。 盡可能一律使用參數化查詢或預存程式是最佳作法。

## <a name="transmit-updates-to-the-data-source"></a>將更新傳送至資料來源

在資料集中進行變更之後，您可以將變更傳送至資料來源。 最常見的作法是，呼叫 `Update` TableAdapter (或資料介面卡) 的方法。 方法會對資料表中的每一筆記錄進行迴圈，判斷需要何種類型的更新 (update、insert 或 delete) （如果有的話），然後執行適當的命令。

為了說明如何進行更新，假設您的應用程式使用包含單一資料表的資料集。 應用程式會從資料庫提取兩個數據列。 在抓取之後，記憶體中的資料表看起來像這樣：

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

您的應用程式會將林丹的狀態變更為「慣用」。 由於這項變更，該資料列的屬性值 <xref:System.Data.DataRow.RowState%2A> 會從變更 <xref:System.Data.DataRowState.Unchanged> 為 <xref:System.Data.DataRowState.Modified> 。 <xref:System.Data.DataRow.RowState%2A>第一個資料列的屬性值會保持不變 <xref:System.Data.DataRowState.Unchanged> 。 資料表現在看起來像這樣：

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

現在您的應用程式會呼叫 `Update` 方法將資料集傳送至資料庫。 方法會輪流檢查每個資料列。 針對第一個資料列，此方法不會將 SQL 語句傳送至資料庫，因為該資料列最初從資料庫提取以來尚未變更。

不過，在第二個數據列中，此 `Update` 方法會自動叫用正確的資料命令，並將它傳送至資料庫。 SQL 語句的特定語法取決於基礎資料存放區所支援的 SQL 方言。 但是，下列已傳送 SQL 語句的一般特性是值得注意的：

- 傳送的 SQL 語句是 UPDATE 語句。 介面卡知道要使用 UPDATE 語句，因為屬性的值 <xref:System.Data.DataRow.RowState%2A> 是 <xref:System.Data.DataRowState.Modified> 。

- 傳送的 SQL 語句包含 WHERE 子句，表示 UPDATE 語句的目標是在其中的資料列 `CustomerID = 'c400'` 。 SELECT 語句的這個部分會區分目標資料列與所有其他專案，因為 `CustomerID` 是目標資料表的主要索引鍵。 WHERE 子句的資訊衍生自記錄 () 的原始版本 `DataRowVersion.Original` ，以防識別資料列所需的值已變更。

- 傳送的 SQL 語句包含 SET 子句，以設定修改過之資料行的新值。

   > [!NOTE]
   > 如果 TableAdapter 的 `UpdateCommand` 屬性已設定為預存程式的名稱，則介面卡不會建立 SQL 語句。 相反地，它會使用傳入的適當參數叫用預存程式。

## <a name="pass-parameters"></a>傳遞參數

您通常會使用參數來傳遞即將在資料庫中更新之記錄的值。 當 TableAdapter 的 `Update` 方法執行 UPDATE 語句時，它需要填入參數值。 它會從集合中取得 `Parameters` 適當資料命令的這些值（在此案例中為 `UpdateCommand` TableAdapter 中的物件）。

如果您已經使用 Visual Studio 工具來產生資料介面卡，物件就 `UpdateCommand` 會包含參數的集合，這些參數會對應至語句中的每個參數預留位置。

<xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName>每個參數的屬性都會指向資料表中的資料行。 例如， `SourceColumn` `au_id` 和參數的屬性 `Original_au_id` 會設定為數據表中的任何資料行，其中包含作者識別碼。當介面卡的 `Update` 方法執行時，它會從正在更新的記錄讀取 [作者 id] 資料行，並將值填入語句中。

在 UPDATE 語句中，您必須指定新的值 (將會寫入記錄) 和舊值 (，以便在資料庫) 中找出記錄。 因此，每個值都有兩個參數：一個用於 SET 子句，另一個用於 WHERE 子句。 這兩個參數都會從正在更新的記錄讀取資料，但它們會根據參數的屬性取得不同版本的資料行值 <xref:System.Data.SqlClient.SqlParameter.SourceVersion> 。 SET 子句的參數會取得目前的版本，而 WHERE 子句的參數會取得原始版本。

> [!NOTE]
> 您也可以 `Parameters` 在程式碼中自行設定集合中的值，這通常會在資料配接器的事件的事件處理常式中進行 <xref:System.Data.DataTable.RowChanging> 。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [建立和設定 TableAdapter](create-and-configure-tableadapters.md)
- [使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [驗證資料](validate-data-in-datasets.md)
- [如何：新增、修改和刪除實體 (WCF 資料服務)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)
