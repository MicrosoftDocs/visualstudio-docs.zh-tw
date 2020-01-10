---
title: 將資料儲存回資料庫
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 64d46d4d662b7226dd2be15e6281a17e5b87e577
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586285"
---
# <a name="save-data-back-to-the-database"></a>將資料儲存回資料庫

此資料集是資料的記憶體中複本。 如果您修改該資料，則將這些變更儲存回資料庫是很好的作法。 您可以透過下列三種方式之一來執行此動作：

- 藉由呼叫 TableAdapter 的其中一個 `Update` 方法

- 藉由呼叫 TableAdapter 的其中一個 `DBDirect` 方法

- 藉由在 TableAdapterManager 上呼叫 `UpdateAll` 方法，當資料集包含與資料集中其他資料表相關的資料表時，Visual Studio 為您產生的

當您將資料集資料表系結至 Windows Form 或 XAML 頁面上的控制項時，資料系結架構會為您執行所有工作。

如果您很熟悉 Tableadapter，可以直接跳到下列其中一個主題：

|主題|描述|
|-----------|-----------------|
|[在資料庫中插入新的資料錄](../data-tools/insert-new-records-into-a-database.md)|如何使用 Tableadapter 或命令物件來執行更新和插入|
|[使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)|如何使用 Tableadapter 執行更新|
|[階層式更新](../data-tools/hierarchical-update.md)|如何從包含兩個或多個相關資料表的資料集執行更新|
|[處理並行例外狀況](../data-tools/handle-a-concurrency-exception.md)|當兩個使用者同時嘗試在資料庫中變更相同的資料時，如何處理例外狀況|
|[如何：使用交易儲存資料](../data-tools/save-data-by-using-a-transaction.md)|如何使用系統將資料儲存在交易中。 交易命名空間和 TransactionScope 物件|
|[儲存異動中的資料](../data-tools/save-data-in-a-transaction.md)|建立 Windows Forms 應用程式的逐步解說，以示範如何將資料儲存至交易內的資料庫|
|[儲存資料至資料庫 (多個資料表)](../data-tools/save-data-to-a-database-multiple-tables.md)|如何編輯記錄，並將多個資料表中的變更儲存回資料庫|
|[從物件中將資料儲存至資料庫](../data-tools/save-data-from-an-object-to-a-database.md)|如何使用 TableAdapter DbDirect 方法，將資料從不在資料集中的物件傳遞至資料庫|
|[使用 TableAdapter DBDirect 方法儲存資料](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|如何使用 TableAdapter 直接將 SQL 查詢傳送至資料庫|
|[將資料集儲存為 XML](../data-tools/save-a-dataset-as-xml.md)|如何將資料集儲存至 XML 檔|

## <a name="two-stage-updates"></a>兩階段更新

更新資料來源是一個兩個步驟的程式。 第一個步驟是使用新的記錄、變更的記錄或已刪除的記錄來更新資料集。 如果您的應用程式永遠不會將這些變更傳送回資料來源，則表示您已完成更新。

如果您將變更傳送回資料庫，則需要第二個步驟。 如果您未使用資料繫結控制項，則必須手動呼叫您用來填入資料集之相同 TableAdapter （或資料介面卡）的 `Update` 方法。 不過，您也可以使用不同的介面卡，例如，將資料從某個資料來源移至另一個，或更新多個資料來源。 如果您未使用資料系結，而且要儲存相關資料表的變更，您必須手動將自動產生之 `TableAdapterManager` 類別的變數具現化，然後再呼叫其 `UpdateAll` 方法。

![資料集更新的概念圖](../data-tools/media/vbdatasetupdates.gif)

資料集包含資料表的集合，其中包含資料列的集合。 如果您稍後想要更新基礎資料來源，則在加入或移除資料列時，您必須在 `DataTable.DataRowCollection` 屬性上使用方法。 這些方法會執行更新資料來源所需的變更追蹤。 如果您在 Rows 屬性上呼叫 `RemoveAt` 集合，則不會將刪除動作傳回到資料庫。

## <a name="merge-datasets"></a>合併資料集

您可以藉由將資料集與另一個資料集*合併*，來更新其內容。 這牽涉到將*源*資料集的內容複寫到呼叫的資料集（稱為「*目標*資料集」）。 當您合併資料集時，源資料集中的新記錄會新增至目標資料集。 此外，源資料集內的額外資料行也會加入至目標資料集。 當您有本機資料集，並從另一個應用程式取得第二個資料集時，合併資料集會很有用。 當您從元件（例如 XML web service）取得第二個資料集，或當您需要整合來自多個資料集的資料時，此功能也很有用。

合併資料集時，您可以傳遞布林值引數（`preserveChanges`），告訴 <xref:System.Data.DataSet.Merge%2A> 方法是否要在目標資料集中保留現有的修改。 因為資料集會維護多個版本的記錄，所以請務必記住，有一個以上的記錄版本會合並。 下表顯示兩個資料集中的記錄合併的方式：

|DataRowVersion|目標資料集|來源資料集|
| - | - | - |
|原始|James Wilson|James C. Wilson|
|目前|Jim Wilson|James C. Wilson|

使用 `preserveChanges=false targetDataset.Merge(sourceDataset)` 在上表中呼叫 <xref:System.Data.DataSet.Merge%2A> 方法，會產生下列資料：

|DataRowVersion|目標資料集|來源資料集|
| - | - | - |
|原始|James C. Wilson|James C. Wilson|
|目前|James C. Wilson|James C. Wilson|

使用 `preserveChanges = true targetDataset.Merge(sourceDataset, true)` 呼叫 <xref:System.Data.DataSet.Merge%2A> 方法，會產生下列資料：

|DataRowVersion|目標資料集|來源資料集|
| - | - | - |
|原始|James C. Wilson|James C. Wilson|
|目前|Jim Wilson|James C. Wilson|

> [!CAUTION]
> 在 `preserveChanges = true` 案例中，如果在目標資料集的記錄上呼叫 <xref:System.Data.DataSet.RejectChanges%2A> 方法，則它會還原為*源*資料集的原始資料。 這表示如果您嘗試使用目標資料集來更新原始資料來源，它可能找不到要更新的原始資料列。 您可以使用資料來源中的更新記錄來填滿另一個資料集，然後執行合併以避免發生並行違規，以避免發生並行違規。 （已填入資料集之後，另一位使用者修改資料來源中的記錄時，就會發生並行違規）。

## <a name="update-constraints"></a>更新條件約束

若要對現有的資料列進行變更，請在個別資料行中加入或更新資料。 如果資料集包含條件約束（例如外鍵或不可為 null 的條件約束），則當您更新記錄時，可能會暫時處於錯誤狀態。 也就是說，在您完成更新一個資料行之後，但是在到達下一個資料行之前，它可能會處於錯誤狀態。

若要防止過早的條件約束違規，您可以暫時暫停更新條件約束。 這有兩個目的：

- 當您完成更新一個資料行但尚未開始更新另一個資料行之後，它會防止擲回錯誤。

- 它會防止引發特定的更新事件（通常用於驗證的事件）。

> [!NOTE]
> 在 Windows Forms 中，內建于 datagrid 的資料系結架構會暫停條件約束檢查，直到焦點移出資料列為止，而且您不需要明確地呼叫 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A>或 <xref:System.Data.DataRow.CancelEdit%2A> 方法。

在資料集上叫用 <xref:System.Data.DataSet.Merge%2A> 方法時，會自動停用條件約束。 當合併完成時，如果無法啟用的資料集有任何條件約束，則會擲回 <xref:System.Data.ConstraintException>。 在此情況下，<xref:System.Data.DataSet.EnforceConstraints%2A> 屬性會設定為 `false,` 而且必須解決所有條件約束違規，才能將 <xref:System.Data.DataSet.EnforceConstraints%2A> 屬性重設為 `true`。

完成更新之後，您可以重新啟用條件約束檢查，這也會重新啟用更新事件並加以引發。

如需暫停事件的詳細資訊，請參閱[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。

## <a name="dataset-update-errors"></a>資料集更新錯誤

當您更新資料集中的記錄時，可能會發生錯誤。 例如，您可能會不小心將錯誤類型的資料寫到資料行，或是太長的資料，或有其他完整性問題的資料。 或者，您可能有應用程式特定的驗證檢查，可以在 update 事件的任何階段引發自訂錯誤。 如需詳細資訊，請參閱[驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)。

## <a name="maintain-information-about-changes"></a>維護變更的相關資訊

資料集中變更的相關資訊會以兩種方式進行維護：藉由標記表示其已變更（<xref:System.Data.DataRow.RowState%2A>）的資料列，以及保留記錄的多個複本（<xref:System.Data.DataRowVersion>）。 藉由使用這項資訊，處理常式可以判斷資料集內已變更的內容，並且可以將適當的更新傳送至資料來源。

### <a name="rowstate-property"></a>RowState 屬性

<xref:System.Data.DataRow> 物件的 <xref:System.Data.DataRow.RowState%2A> 屬性是提供特定資料列狀態相關資訊的值。

下表詳細說明 <xref:System.Data.DataRowState> 列舉的可能值：

|DataRowState 值|描述|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|已將資料列新增為 <xref:System.Data.DataRowCollection>的專案。 （處於此狀態的資料列沒有對應的原始版本，因為在呼叫最後一個 <xref:System.Data.DataRow.AcceptChanges%2A> 方法時，它並不存在）。|
|<xref:System.Data.DataRowState.Deleted>|已使用 <xref:System.Data.DataRow> 物件的 <xref:System.Data.DataRow.Delete%2A> 刪除資料列。|
|<xref:System.Data.DataRowState.Detached>|資料列已建立，但它不屬於任何 <xref:System.Data.DataRowCollection>。 <xref:System.Data.DataRow> 物件在建立之後，會立即處於此狀態，然後將它加入集合中，以及從集合中移除之後。|
|<xref:System.Data.DataRowState.Modified>|資料列中的資料行值已經以某種方式變更。|
|<xref:System.Data.DataRowState.Unchanged>|資料列從上次呼叫 <xref:System.Data.DataRow.AcceptChanges%2A> 之後就未變更。|

### <a name="datarowversion-enumeration"></a>DataRowVersion 列舉

資料集會維護多個版本的記錄。 使用 <xref:System.Data.DataRow.Item%2A> 屬性或 <xref:System.Data.DataRow> 物件的 <xref:System.Data.DataRow.GetChildRows%2A> 方法來抓取 <xref:System.Data.DataRow> 中找到的值時，會使用 <xref:System.Data.DataRowVersion> 欄位。

下表詳細說明 <xref:System.Data.DataRowVersion> 列舉的可能值：

|DataRowVersion 值|描述|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|記錄的目前版本包含自上一次呼叫 <xref:System.Data.DataRow.AcceptChanges%2A> 之後，已在記錄上執行的所有修改。 如果已刪除資料列，則沒有目前的版本。|
|<xref:System.Data.DataRowVersion.Default>|記錄的預設值，如資料集架構或資料來源所定義。|
|<xref:System.Data.DataRowVersion.Original>|記錄的原始版本是記錄的複本，與上次在資料集中認可變更時相同。 實際上，這通常是從資料來源讀取的記錄版本。|
|<xref:System.Data.DataRowVersion.Proposed>|建議的記錄版本，當您在更新過程中暫時可用，也就是您呼叫 <xref:System.Data.DataRow.BeginEdit%2A> 方法與 <xref:System.Data.DataRow.EndEdit%2A> 方法之間的情況。 您通常會在事件的處理常式中存取建議的記錄版本，例如 <xref:System.Data.DataTable.RowChanging>。 叫用 <xref:System.Data.DataRow.CancelEdit%2A> 方法會反轉變更，並刪除所建議的資料列版本。|

當更新資訊傳輸至資料來源時，原始和目前的版本很有用。 一般來說，將更新傳送至資料來源時，資料庫的新資訊就會在目前的記錄版本中。 原始版本的資訊可用來尋找要更新的記錄。

例如，在記錄的主鍵變更的情況下，您需要一種方法來找出資料來源中的正確記錄，以便更新變更。 如果原始版本不存在，則記錄最可能會附加至資料來源，而不只是在額外的垃圾記錄中，而是在一筆不正確且已過期的記錄中。 這兩個版本也會用於並行控制中。 您可以比較原始版本與資料來源中的記錄，以判斷記錄是否已經在載入資料集後變更。

當您需要先執行驗證，才能實際將變更認可至資料集時，建議的版本會很有用。

即使記錄已經變更，也不一定會有該資料列的原始或目前版本。 當您在資料表中插入新的資料列時，沒有原始版本，只有目前的版本。 同樣地，如果您藉由呼叫資料表的 `Delete` 方法來刪除資料列，則會有原始版本，但沒有目前的版本。

您可以藉由查詢資料列的 <xref:System.Data.DataRow.HasVersion%2A> 方法，來測試是否有特定版本的記錄存在。 當您要求資料行的值時，您可以藉由傳遞 <xref:System.Data.DataRowVersion> 列舉值做為選擇性引數，來存取任一版本的記錄。

## <a name="get-changed-records"></a>取得變更的記錄

這是一個常見的作法，就是不要更新資料集中的每一筆記錄。 例如，使用者可能會使用顯示許多記錄的 Windows Forms <xref:System.Windows.Forms.DataGridView> 控制項。 不過，使用者可能只會更新幾筆記錄，刪除一個，然後插入一個新的。 資料集和資料表提供方法（`GetChanges`），只傳回已修改的資料列。

您可以使用資料資料表（<xref:System.Data.DataTable.GetChanges%2A>）或資料集（<xref:System.Data.DataSet.GetChanges%2A>）本身的 `GetChanges` 方法，來建立已變更記錄的子集。 如果您針對資料表呼叫方法，它只會傳回包含已變更記錄的資料表複本。 同樣地，如果您在資料集上呼叫方法，就會取得新的資料集，其中只包含變更的記錄。

`GetChanges` 本身會傳回所有已變更的記錄。 相反地，藉由將所需的 <xref:System.Data.DataRowState> 做為參數傳遞至 `GetChanges` 方法，您可以指定所要的已變更記錄子集：新增的記錄、標記為刪除的記錄、已卸離的記錄，或修改過的記錄。

當您想要將記錄傳送至另一個元件進行處理時，取得已變更記錄的子集會很有用。 除了傳送整個資料集之外，您也可以只取得元件所需的記錄，減少與另一個元件通訊的額外負荷。

## <a name="commit-changes-in-the-dataset"></a>認可資料集中的變更

當資料集發生變更時，就會設定已變更之資料列的 <xref:System.Data.DataRow.RowState%2A> 屬性。 會建立、維護記錄的原始和目前版本，並由 <xref:System.Data.DataRowView.RowVersion%2A> 屬性提供給您。 將正確的更新傳送至資料來源時，必須要有儲存在這些已變更資料列之屬性中的中繼資料。

如果變更反映資料來源的目前狀態，您就不再需要維護這項資訊。 一般來說，資料集和其來源會同步處理兩次：

- 在您將資訊載入至資料集後（例如從來源讀取資料時）。

- 將資料集的變更傳送到資料來源之後（但不是之前），因為您會遺失將變更傳送至資料庫所需的變更資訊。

您可以藉由呼叫 <xref:System.Data.DataSet.AcceptChanges%2A> 方法，將暫止的變更認可至資料集。 通常會在下列時間呼叫 <xref:System.Data.DataSet.AcceptChanges%2A>：

- 載入資料集之後。 如果您藉由呼叫 TableAdapter 的 `Fill` 方法來載入資料集，則介面卡會自動為您認可變更。 不過，如果您藉由將另一個資料集合併到來載入資料集，則必須手動認可變更。

    > [!NOTE]
    > 當您呼叫 `Fill` 方法時，您可以將介面卡的 `AcceptChangesDuringFill` 屬性設定為 `false`，以防止介面卡自動認可變更。 如果設定為 [`false`]，則在填滿期間插入之每個資料列的 <xref:System.Data.DataRow.RowState%2A> 都會設定為 [<xref:System.Data.DataRowState.Added>]。

- 將資料集變更傳送至另一個進程之後，例如 XML web service。

    > [!CAUTION]
    > 以這種方式認可變更會清除任何變更資訊。 等到您完成執行需要應用程式的作業，以知道資料集內已做了哪些變更之後，才會認可變更。

這個方法會完成下列工作：

- 將記錄的 <xref:System.Data.DataRowVersion.Current> 版本寫入其 <xref:System.Data.DataRowVersion.Original> 版本，並覆寫原始版本。

- 移除 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRowState.Deleted>的任何資料列。

- 將記錄的 <xref:System.Data.DataRow.RowState%2A> 屬性設定為 <xref:System.Data.DataRowState.Unchanged>。

<xref:System.Data.DataSet.AcceptChanges%2A> 方法可在三個層級取得。 您可以在 <xref:System.Data.DataRow> 物件上呼叫它，只認可該資料列的變更。 您也可以在 <xref:System.Data.DataTable> 物件上呼叫它，以認可資料表中的所有資料列。 最後，您可以在 <xref:System.Data.DataSet> 物件上呼叫它，以認可資料集所有資料表之所有記錄中的所有暫止變更。

下表描述根據呼叫方法的物件，所認可的變更：

|方法|結果|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|變更只會在特定資料列上認可。|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|在特定資料表中的所有資料列上，會認可變更。|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|變更會在資料集的所有資料表的所有資料列上進行認可。|

> [!NOTE]
> 如果您藉由呼叫 TableAdapter 的 `Fill` 方法來載入資料集，則不需要明確接受變更。 根據預設，`Fill` 方法會在完成填入資料表之後，呼叫 `AcceptChanges` 方法。

<xref:System.Data.DataSet.RejectChanges%2A>的相關方法，會藉由將 <xref:System.Data.DataRowVersion.Original> 版本複製回記錄的 <xref:System.Data.DataRowVersion.Current> 版本，來復原變更的效果。 它也會將每一筆記錄的 <xref:System.Data.DataRow.RowState%2A> 設定回 <xref:System.Data.DataRowState.Unchanged>。

## <a name="data-validation"></a>資料驗證

若要驗證應用程式中的資料是否符合它所傳遞之進程的需求，您通常必須加入驗證。 這可能牽涉到檢查使用者在表單中的專案是否正確、驗證由另一個應用程式傳送至您的應用程式的資料，或甚至檢查元件中所計算的資訊是否落在資料來源的條件約束內和應用程式需求。

您可以透過數種方式來驗證資料：

- 在商務層中，藉由將程式碼加入至您的應用程式來驗證資料。 資料集是您可以執行這項工作的地方。 此資料集提供後端驗證的一些優點，例如，驗證資料行和資料列值時的變更是否已變更。 如需詳細資訊，請參閱[驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)。

- 在展示層中，將驗證新增至表單。 如需詳細資訊，請參閱[Windows Forms 中的使用者輸入驗證](/dotnet/framework/winforms/user-input-validation-in-windows-forms)。

- 在資料後端中，將資料傳送至資料來源（例如資料庫），並允許它接受或拒絕資料。 如果您使用的資料庫具有複雜的功能來驗證資料並提供錯誤資訊，這可能是個實用的方法，因為不論資料位於何處，您都可以進行驗證。 不過，這種方法可能無法配合應用程式特定的驗證需求。 此外，若要讓資料來源驗證資料，可能會因為您的應用程式如何協助解決後端所引發的驗證錯誤，而造成資料來源的大量往返。

   > [!IMPORTANT]
   > 搭配設定為 <xref:System.Data.CommandType.Text>的 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 屬性使用資料命令時，請仔細檢查從用戶端傳送的資訊，再將它傳遞至您的資料庫。 惡意使用者可能會嘗試傳送 (插入) 修改過或額外的 SQL 陳述式，以獲得未授權的存取或破壞資料庫。 將使用者輸入傳送至資料庫之前，請務必確認該資訊是否有效。 最佳做法是一律盡可能使用參數化查詢或預存程式。

## <a name="transmit-updates-to-the-data-source"></a>將更新傳送至資料來源

在資料集內進行變更之後，您就可以將變更傳送至資料來源。 最常見的作法是呼叫 TableAdapter （或資料介面卡）的 `Update` 方法。 方法會對資料表中的每一筆記錄進行迴圈，判斷需要何種類型的更新（update、insert 或 delete）（如果有的話），然後執行適當的命令。

如需如何進行更新的說明，假設您的應用程式使用包含單一資料表的資料集。 應用程式會從資料庫提取兩個數據列。 在抓取之後，記憶體中的資料表看起來像這樣：

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

您的應用程式會將南張三的狀態變更為「慣用」。 由於這項變更的結果，該資料列的 <xref:System.Data.DataRow.RowState%2A> 屬性值會從 <xref:System.Data.DataRowState.Unchanged> 變更為 <xref:System.Data.DataRowState.Modified>。 第一個資料列的 <xref:System.Data.DataRow.RowState%2A> 屬性值仍然 <xref:System.Data.DataRowState.Unchanged>。 資料表現在看起來像這樣：

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

現在您的應用程式會呼叫 `Update` 方法將資料集傳送至資料庫。 方法會輪流檢查每個資料列。 在第一個資料列中，方法不會將任何 SQL 語句傳送至資料庫，因為它原本從資料庫提取以來，該資料列尚未變更。

不過，在第二個數據列中，`Update` 方法會自動叫用正確的 data 命令，並將它傳送至資料庫。 SQL 語句的特定語法取決於基礎資料存放區所支援的 SQL 方言。 但是，下列已傳輸之 SQL 語句的一般特性值得注意：

- 已傳送的 SQL 語句是 UPDATE 語句。 介面卡知道要使用 UPDATE 語句，因為 <xref:System.Data.DataRow.RowState%2A> 屬性的值是 <xref:System.Data.DataRowState.Modified>。

- 已傳送的 SQL 語句包含 WHERE 子句，表示 UPDATE 語句的目標是 `CustomerID = 'c400'`的資料列。 SELECT 語句的這個部分會區分目標資料列與所有其他專案，因為 `CustomerID` 是目標資料表的主要索引鍵。 WHERE 子句的資訊衍生自記錄的原始版本（`DataRowVersion.Original`），以防識別資料列所需的值已變更。

- 已傳送的 SQL 語句包含 SET 子句，用以設定已修改之資料行的新值。

   > [!NOTE]
   > 如果 TableAdapter 的 `UpdateCommand` 屬性已設定為預存程式的名稱，則介面卡不會建立 SQL 語句。 相反地，它會使用傳入的適當參數來叫用預存程式。

## <a name="pass-parameters"></a>傳遞參數

您通常會使用參數來傳遞將要在資料庫中更新之記錄的值。 當 TableAdapter 的 `Update` 方法執行 UPDATE 語句時，它需要填入參數值。 它會從適用于適當資料命令的 `Parameters` 集合中取得這些值，在此案例中為 TableAdapter 中的 `UpdateCommand` 物件。

如果您已使用 Visual Studio 工具來產生資料介面卡，則 `UpdateCommand` 物件會包含對應至語句中每個參數預留位置的參數集合。

每個參數的 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> 屬性會指向資料表中的資料行。 例如，`au_id` 和 `Original_au_id` 參數的 `SourceColumn` 屬性會設定為數據表中的任何資料行，其中包含作者識別碼。當介面卡的 `Update` 方法執行時，它會從正在更新的記錄讀取 author id 資料行，並將值填滿至語句。

在 UPDATE 語句中，您必須指定新的值（將寫入記錄的值）以及舊值（如此一來，記錄可以位於資料庫中）。 因此，每個值都有兩個參數：一個用於 SET 子句，另一個用於 WHERE 子句。 這兩個參數都會從正在更新的記錄中讀取資料，但它們會根據參數的 <xref:System.Data.SqlClient.SqlParameter.SourceVersion> 屬性，取得不同版本的資料行值。 SET 子句的參數會取得目前的版本，而 WHERE 子句的參數會取得原始版本。

> [!NOTE]
> 您也可以在程式碼中自行設定 `Parameters` 集合中的值，您通常會在資料介面卡的 <xref:System.Data.DataTable.RowChanging> 事件的事件處理常式中執行此動作。

## <a name="see-also"></a>請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [建立和設定 TableAdapter](create-and-configure-tableadapters.md)
- [使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [驗證資料](validate-data-in-datasets.md)
- [如何：新增、修改和刪除實體 (WCF 資料服務)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)
