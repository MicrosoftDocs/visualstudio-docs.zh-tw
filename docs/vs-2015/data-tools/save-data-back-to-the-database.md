---
title: 將資料儲存回資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b6fd99b2b1a41d6baa3a110b2a595afb1dd7e3f
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281845"
---
# <a name="save-data-back-to-the-database"></a>將資料儲存回資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
資料集是記憶體中資料的複本。 如果您修改該資料時，最好先將這些變更儲存回資料庫。 您可以執行這三種方式之一：  
  
- 透過呼叫其中一個`Update`的 TableAdapter 方法  
  
- 藉由呼叫其中一個 TableAdapter 的 DBDirect 方法  
  
- 藉由呼叫 UpdateAll 方法上`TableAdapterManager`Visual Studio 會為您產生資料集包含相關資料集中的其他資料表的資料表時，  
  
  當您的資料將資料集資料表繫結至 Windows Form 或 XAML 頁面上的控制項時，則在資料繫結架構會為您的所有工作。  
  
  如果您熟悉 TableAdapters，您可以直接跳到其中一個主題：  
  
|主題|描述|  
|-----------|-----------------|  
|[在資料庫中插入新的資料錄](../data-tools/insert-new-records-into-a-database.md)|如何執行更新，並將插入使用 Tableadapter 或命令的物件|  
|[使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)|如何執行與 Tableadapter 的更新|  
|[階層式更新](../data-tools/hierarchical-update.md)|如何從具有兩個或多個相關資料表的資料集執行的更新|  
|[處理並行例外狀況](../data-tools/handle-a-concurrency-exception.md)|如何處理例外狀況，當兩個使用者嘗試同時變更資料庫中相同的資料|  
|[使用異動儲存資料](../data-tools/save-data-by-using-a-transaction.md)|如何將資料儲存在使用 System.Transactions 命名空間和 TransactionScope 物件的交易|  
|[儲存異動中的資料](../data-tools/save-data-in-a-transaction.md)|如何將資料儲存在使用 System.Transactions 命名空間的交易|  
|[儲存資料至資料庫 (多個資料表)](../data-tools/save-data-to-a-database-multiple-tables.md)|如何編輯記錄，並將變更儲存回資料庫的多個資料表中|  
|[從物件中將資料儲存至資料庫](../data-tools/save-data-from-an-object-to-a-database.md)|如何將資料從物件，使用 TableAdapter DbDirect 方法不是資料庫的資料集傳遞|  
|[使用 TableAdapter DBDirect 方法儲存資料](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|如何使用 SQL 查詢直接傳送到資料庫的 TableAdapter|  
|[將資料集儲存為 XML](../data-tools/save-a-dataset-as-xml.md)|如何將資料集儲存至 XML 文件|  
  
## <a name="two-stage-updates"></a>兩階段更新  
 更新資料來源是兩個步驟的程序。 第一個步驟是使用新的記錄、 已變更的記錄或已刪除的記錄更新的資料集。 如果您的應用程式永遠不會傳送回資料來源的這些變更，您已完成的更新。  
  
 如果您不要將變更傳送回資料庫，第二個步驟是必要的。 如果您未使用資料繫結控制項，您就必須以手動方式呼叫的 Update 方法相同的 TableAdapter （或資料配接器），您用來填入資料集。 不過，您也可以使用不同的配接器，例如，若要將資料從一個資料來源移到另一個，或更新多個資料來源。 如果您未使用資料繫結，並儲存相關資料表的變更，您必須以手動方式具現化自動產生 TableAdapterManager 類別的變數，然後呼叫其 UpdateAll 方法。  
  
 ![Visual Basic 資料集更新](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
兩階段更新程序，而且在成功的更新中 DataRowVersion 的角色  
  
 資料集包含的資料表，其中包含的資料列集合的集合。 如果您想要更新基礎資料來源，您必須使用 DataTable.DataRowCollection 屬性時新增或移除資料列上的方法。 這些方法會執行變更追蹤所需更新資料來源。 如果您的資料列的屬性上呼叫 RemoveAt 集合，刪除不會傳送回資料庫。  
  
## <a name="merge-datasets"></a>合併資料集  
 您可以更新的資料集的內容*合併*它與另一個資料集。 這牽涉到複製的內容*來源*至呼叫端的資料集的資料集 (稱為*目標*資料集)。 當您合併資料集時，來源資料集內的新記錄會新增至目標資料集。 此外，在來源資料集的額外資料行加入目標資料集。 合併資料集時，您的本機資料集，而且您會從另一個應用程式的第二個資料集。 它也很有用的元件，例如 XML web service 中收到的第二個資料集時，或當您需要整合多個資料集的資料。  
  
 當合併資料集，您可以將傳遞布林值引數 (`preserveChanges`)，會告訴<xref:System.Data.DataSet.Merge%2A>方法是否要保留現有目標資料集內的修改。 因為資料集維護多個版本的記錄，很重要要牢記在心，正在合併多個版本的記錄。 下表顯示如何合併兩個資料集內的記錄：  
  
|DataRowVersion|目標資料集|來源資料集|  
|--------------------|--------------------|--------------------|  
|原始|James Wilson|James C.Wilson|  
|目前|Jim Wilson|James C.Wilson|  
  
 呼叫<xref:System.Data.DataSet.Merge%2A>方法的先前資料表上`preserveChanges=false targetDataset.Merge(sourceDataset)`產生下列結果：  
  
|DataRowVersion|目標資料集|來源資料集|  
|--------------------|--------------------|--------------------|  
|原始|James C.Wilson|James C.Wilson|  
|目前|James C.Wilson|James C.Wilson|  
  
 呼叫<xref:System.Data.DataSet.Merge%2A>方法使用`preserveChanges = true targetDataset.Merge(sourceDataset, true)`產生下列結果：  
  
|DataRowVersion|目標資料集|來源資料集|  
|--------------------|--------------------|--------------------|  
|原始|James C.Wilson|James C.Wilson|  
|目前|Jim Wilson|James C.Wilson|  
  
> [!CAUTION]
>  在 `preserveChanges = true`案例中，如果<xref:System.Data.DataSet.RejectChanges%2A>記錄，以在目標資料集上呼叫方法，則它會還原為原始資料，從*來源*資料集。 這表示，如果您嘗試更新原始資料來源與目標資料集，它可能無法以尋找要更新原始的資料列。 您可以防止並行存取違規，另一個資料集填入資料來源更新的記錄，然後再執行合併以防止並行存取違規。 （當另一位使用者已填入資料集之後，請修改資料來源中的記錄會發生並行存取違規）。  
  
## <a name="update-constraints"></a>更新限制式  
 若要變更現有的資料列，新增或更新個別資料行中的資料。 如果資料集包含條件約束 （例如外部索引鍵或非 null 的條件約束），它很有可能，記錄可以暫時處於錯誤狀態更新它。 也就是說，它可以處於錯誤狀態完成更新一個資料行後，但您前往下一個。  
  
 若要避免過早的條件約束違規，您可以暫時暫停更新條件約束。 這有兩種用途：  
  
- 它會防止您已完成更新一個資料行，但尚未啟動另一個更新之後，所擲回錯誤。  
  
- 它可防止特定更新的事件引發 （通常用於驗證的事件）。  
  
  完成更新之後，您可以重新啟用條件約束檢查，這也會重新啟用 更新事件，並引發它們。  
  
> [!NOTE]
>  在 Windows Forms 中，內建資料格的資料繫結架構暫止條件約束檢查焦點移出資料列，並沒有明確呼叫之前<xref:System.Data.DataRow.BeginEdit%2A>， <xref:System.Data.DataRow.EndEdit%2A>，或<xref:System.Data.DataRow.CancelEdit%2A>方法。  
  
 條件約束會自動停用時<xref:System.Data.DataSet.Merge%2A>資料集上叫用方法。 合併完成後，如果有任何條件約束，無法啟用資料集上的<xref:System.Data.ConstraintException>就會擲回。 在此情況下，<xref:System.Data.DataSet.EnforceConstraints%2A>屬性設定為`false,`，重設之前，必須解決所有的條件約束違規<xref:System.Data.DataSet.EnforceConstraints%2A>屬性設`true`。  
  
 完成更新之後，您可以重新啟用條件約束檢查，這也會重新啟用 更新事件，並引發它們。  
  
 如需暫停事件的詳細資訊，請參閱[填入 dataset 時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
## <a name="dataset-update-errors"></a>資料集更新錯誤  
 當您更新資料集內的記錄時，沒有錯誤的可能性。 比方說，您可能會不小心寫入資料的錯誤類型的資料行，或資料太長或具有其他完整性問題的資料。 或者，您可能可以在更新事件的任何階段期間引發自訂錯誤的特定應用程式的驗證檢查。 如需詳細資訊，請參閱 <<c0> [ 驗證資料集中](../data-tools/validate-data-in-datasets.md)。  
  
## <a name="maintaining-information-about-changes"></a>維護變更的相關資訊  
 資料集內變更的相關資訊會維護兩種方式： 藉由加上旗標，指出已變更的資料列 (<xref:System.Data.DataRow.RowState%2A>)，並藉由將多個複本的記錄保留 (<xref:System.Data.DataRowVersion>)。 使用這項資訊，處理程序可以判斷變更資料集，並將適當的更新傳送至資料來源。  
  
### <a name="rowstate-property"></a>RowState 屬性  
 <xref:System.Data.DataRow.RowState%2A>屬性<xref:System.Data.DataRow>物件會提供特定資料列的資料狀態的相關資訊的值。  
  
 下表詳細說明的可能值<xref:System.Data.DataRowState>列舉型別：  
  
|DataRowState 值|描述|  
|------------------------|-----------------|  
|<xref:System.Data.DataRowState>|資料列都已經加入項目成為<xref:System.Data.DataRowCollection>。 (此狀態中的資料列並未安裝對應的原始版本，因為它不存在時的最後一個<xref:System.Data.DataRow.AcceptChanges%2A>方法受呼叫時)。|  
|<xref:System.Data.DataRowState>|使用刪除資料列<xref:System.Data.DataRow.Delete%2A>的<xref:System.Data.DataRow>物件。|  
|<xref:System.Data.DataRowState>|資料列已建立，但不屬於任何<xref:System.Data.DataRowCollection>。 A<xref:System.Data.DataRow>立即建立它之後，之前它尚未加入至集合，以及從集合移除後，物件是處於此狀態。|  
|<xref:System.Data.DataRowState>|資料列中的資料行值已經以某種方式變更。|  
|<xref:System.Data.DataRowState>|資料列之後並未變更<xref:System.Data.DataRow.AcceptChanges%2A>一次呼叫。|  
  
### <a name="datarowversion-enumeration"></a>DataRowVersion 列舉  
 資料集維護多個版本的記錄。 <xref:System.Data.DataRowVersion>的列舉型別<xref:System.Data.DataRow>物件是一個值，可用來傳回特定版本的<xref:System.Data.DataRow>物件。  
  
 下表詳細說明的可能值<xref:System.Data.DataRowVersion>列舉型別：  
  
|DataRowVersion 值|描述|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|目前版本的一筆記錄包含已自上次執行記錄的所有修改<xref:System.Data.DataRow.AcceptChanges%2A>呼叫。 如果已刪除資料列，則沒有目前的版本。|  
|<xref:System.Data.DataRowVersion>|資料錄，如資料集結構描述或資料來源所定義的預設值。|  
|<xref:System.Data.DataRowVersion>|一筆資料錄的原始版本是一份記錄，因為它是最後一個時間的變更被認可的資料集。 實際上，這通常是一筆記錄的版本為已讀取之資料來源。|  
|<xref:System.Data.DataRowVersion>|建議的版本可用，您正在更新時，暫時的記錄，您所呼叫的時間也就是<xref:System.Data.DataRow.BeginEdit%2A>方法和<xref:System.Data.DataRow.EndEdit%2A>方法。 您通常會存取事件的處理常式中的記錄的建議的版本例如<xref:System.Data.DataTable.RowChanging>。 叫用<xref:System.Data.DataRow.CancelEdit%2A>方法會反轉所做的變更，並刪除資料列的建議的版本。|  
  
 更新資訊傳送至資料來源時，原始和目前的版本很有用。 一般而言，當更新傳送至資料來源時，新資料庫的資訊是記錄的在目前版本中。 與原始版本的資訊用來找出要更新的記錄。  
  
 比方說，在此案例中的一筆資料錄的主索引鍵變更的地方，您需要能夠在資料來源中找出正確的記錄，以更新所做的變更。 如果沒有原始的版本存在，則記錄會很有可能會附加至資料來源，產生的額外不必要的記錄，不僅會不準確且最新的一筆記錄中。 兩個版本也會用於並行存取控制。 您可以比較針對中的資料來源，以判斷記錄是否已變更，因為它已載入至資料集的資料錄的原始版本。  
  
 建議的版本時，您需要執行驗證，然後再實際將變更認可至資料集。  
  
 即使已變更的記錄，沒有一定的該資料列的原始或目前的版本。 當您將新的資料列插入資料表時，沒有任何原始的版本，只有目前的版本。 同樣地，如果您藉由呼叫的資料表刪除資料列`Delete`方法中，原始的版本，但沒有目前的版本。  
  
 您可以藉由查詢資料列的特定版本的一筆記錄是否已有測試<xref:System.Data.DataRow.HasVersion%2A>方法。 您可以存取任一版本的一筆記錄，藉由傳遞<xref:System.Data.DataRowVersion>做為選擇性的引數時要求的資料行值的列舉值。  
  
## <a name="getting-changed-records"></a>取得已變更的記錄  
 它是常見的做法，不是用來更新資料集內的每一筆記錄。 例如，使用者可能使用 Windows Form<xref:System.Windows.Forms.DataGridView>顯示多筆記錄的控制項。 不過，使用者可能會更新僅有少數的記錄、 刪除其中一個，並插入一個新。 資料集和資料的資料表提供的方法 (`GetChanges`) 傳回已修改的資料列。  
  
 您可以建立使用已變更的記錄的子集`GetChanges`方法的其中一個資料表 (<xref:System.Data.DataTable.GetChanges%2A>) 或資料集 (<xref:System.Data.DataSet.GetChanges%2A>) 本身。 如果您針對資料表中呼叫方法，它會傳回與已變更的記錄資料表的副本。 同樣地，如果您的資料集上呼叫方法，您就會取得新的資料集已變更的記錄。  
  
 `GetChanges` 本身會傳回所有已變更的記錄。 相反地，藉由傳遞所需<xref:System.Data.DataRowState>做為參數`GetChanges`方法中，您可以指定您想要變更的資料錄的哪些子集： 新加入的記錄，記錄會標示為刪除，卸離的記錄，或修改記錄。  
  
 取得已變更的記錄的子集時，您想要將記錄傳送至另一個元件進行處理。 而不是傳送整個資料集，您可以減少取得元件所需的記錄與其他元件通訊額外的負荷。 如需詳細資訊，請參閱 <<c0> [ 如何： 擷取變更資料列](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)。  
  
## <a name="committing-changes-in-the-dataset"></a>認可資料集中的變更  
 如果進行變更時，資料集中<xref:System.Data.DataRow.RowState%2A>屬性已變更的資料列的設定。 建立、 維護，而且可供您的資料錄的原始和目前版本<xref:System.Data.DataRowView.RowVersion%2A>屬性。 必須將正確的更新傳送至資料來源的中繼資料會儲存在這些變更的資料列的屬性。  
  
 如果所做的變更會反映資料來源的目前狀態，您不再需要維護這項資訊。 一般而言，有兩倍的資料集和其來源何時同步：  
  
- 緊接在後您已將資訊載入資料集，例如當您從來源讀取資料時。  
  
- 從資料集的變更傳送至資料來源之後, (而非之前，因為您會遺失變更傳送到資料庫所需的變更資訊)。  
  
  您也可以呼叫到資料集認可暫止的變更<xref:System.Data.DataSet.AcceptChanges%2A>方法。 一般而言，<xref:System.Data.DataSet.AcceptChanges%2A>會在您的應用程式中的下列時間期間呼叫。  
  
- 之後您載入資料集。 如果您載入資料集藉由呼叫 TableAdapter 的`Fill`方法，則配接器會自動為您認可變更。 不過，如果您載入資料集合併另一個資料集，然後您必須以手動方式認可的變更。  
  
  > [!NOTE]
  >  您可以避免配接器會自動認可變更，當您呼叫`Fill`方法，藉由設定`AcceptChangesDuringFill`屬性的介面卡`false`。 如果設定為`false`，則<xref:System.Data.DataRow.RowState%2A>填滿期間插入每個資料列會設為<xref:System.Data.DataRowState>。  
  
- 之後您的資料集將變更傳送至另一個處理序，例如 XML Web service。  
  
  > [!CAUTION]
  >  認可變更，如此一來，就會清除任何變更資訊。 不認可後的變更直到您完成執行作業，需要您的應用程式知道在資料集中進行哪些變更。  
  
  這個方法會產生下列結果：  
  
- 寫入<xref:System.Data.DataRowVersion>版本的一筆記錄到其<xref:System.Data.DataRowVersion>版本並覆寫原始的版本。  
  
- 移除任何資料列所在<xref:System.Data.DataRow.RowState%2A>屬性設定為<xref:System.Data.DataRowState>。  
  
- 設定組<xref:System.Data.DataRow.RowState%2A>要記錄的屬性<xref:System.Data.DataRowState>。  
  
  <xref:System.Data.DataSet.AcceptChanges%2A>方法會使用可在三個層級。 您可以對它呼叫<xref:System.Data.DataRow>物件，以認可變更該資料列。 您也可以呼叫它在<xref:System.Data.DataTable>認可資料表中的所有資料列的物件。 最後，您可以在呼叫它<xref:System.Data.DataSet>認可中的資料集的所有資料表的所有記錄的所有暫止變更的物件。  
  
  下表說明哪些會認可變更，根據內容物件上呼叫方法。  
  
|方法|結果|  
|------------|------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|只在特定的資料列上認可的變更。|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|認可上特定的資料表中的所有資料列的變更。|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|認可的資料集的所有資料表中的所有資料列上的變更。|  
  
> [!NOTE]
>  如果您載入資料集藉由呼叫 TableAdapter 的`Fill`方法，您不需要明確接受變更。 根據預設，`Fill`方法呼叫`AcceptChanges`完成填入資料表格之後的方法。  
  
 相關的方法， `RejectChanges`，藉由複製復原變更的影響<xref:System.Data.DataRowVersion>回版本<xref:System.Data.DataRowVersion>記錄版本。 它也會設定<xref:System.Data.DataRow.RowState%2A>每一個記錄備份至<xref:System.Data.DataRowState>。  
  
## <a name="data-validation"></a>資料驗證  
 若要確認您的應用程式中的資料符合傳遞至處理序的需求，您通常需要將驗證加入。 這可能需要檢查在表單中的使用者的項目正確，驗證資料傳送至您的應用程式，另一個應用程式，或甚至檢查 計算您的元件內的資訊，落在您的資料來源的限制範圍內和應用程式需求。  
  
 您可以驗證資料透過數種方式：  
  
- 在商務層中，將程式碼加入至您的應用程式，以驗證資料。 資料集是執行這項操作的一個位置。 資料集提供的一些後端驗證的優點，例如能夠驗證變更，因為資料行和資料列的值變更。 如需詳細資訊，請參閱 <<c0> [ 驗證資料集中](../data-tools/validate-data-in-datasets.md)。  
  
- 在 將驗證新增至表單的展示層。 如需詳細資訊，請參閱 <<c0> [ 在 Windows Form 中驗證使用者輸入](http://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1)。  
  
- 在資料後端，將資料傳送至資料來源 — 比方說，資料庫，並讓它接受或拒絕資料。 如果您正在使用的資料庫，具有複雜的驗證資料，以及提供錯誤資訊的設備，這可能是實用的方法，因為您可以驗證的資料，不論其來自何處。 不過，這種方法可能不會配合特定應用程式的驗證需求。 此外，驗證資料的資料來源可能會導致許多往返到資料來源，取決於您的應用程式可由後端所引發的驗證錯誤的解析的協助。  
  
  > [!IMPORTANT]
  >  使用資料命令時<xref:System.Data.SqlClient.SqlCommand.CommandType%2A>屬性設為<xref:System.Data.CommandType>，仔細檢查，然後將它傳遞到您的資料庫用戶端傳來的資訊。 惡意使用者可能會嘗試傳送 （插入） 修改過或其他的 SQL 陳述式，以取得未經授權的存取，或資料庫損毀。 傳送至資料庫的使用者輸入之前，請務必確認資訊有效。 最好一律使用參數化的查詢或預存程序，可能的話。 如需詳細資訊，請參閱 [Script Exploits Overview](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07) (指令碼攻擊概觀)。  
  
  集中進行完變更之後，您可以將變更傳送至資料來源。 大多數情況下，您可以呼叫`Update`TableAdapter （或資料配接器） 的方法。 方法會迴圈每一筆記錄資料表中的資料，判斷需要該類型的更新 （更新、 插入或刪除），如果有的話，然後再執行適當的命令。  
  
## <a name="transmitting-updates-to-the-data-source"></a>傳輸至資料來源的更新  
 如何進行更新的說明，假設您的應用程式會使用包含單一資料表的資料集。 應用程式會從資料庫擷取兩個資料列。 在擷取之後，記憶體中資料的資料表看起來像這樣：  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 您的應用程式將 Nancy 查爾斯狀態變更為 [慣用]。 因為這項變更，值<xref:System.Data.DataRow.RowState%2A>屬性，該資料列從變更<xref:System.Data.DataRowState>至<xref:System.Data.DataRowState>。 值<xref:System.Data.DataRow.RowState%2A>第一個資料列的屬性會保持<xref:System.Data.DataRowState>。 資料表現在看起來像這樣：  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 現在您的應用程式會呼叫 `Update` 方法將資料集傳送至資料庫。 方法會輪流檢查每個資料列。 第一個資料列中，方法會傳輸任何資料庫的 SQL 陳述式，因為該資料列尚未變更，因為它原本從資料庫擷取。  
  
 第二個資料列中，不過，`Update`方法自動叫用正確的資料命令，並將其傳送至資料庫。 SQL 陳述式的特定語法取決於基礎資料存放區所支援的 SQL 方言。 但下列傳輸的 SQL 陳述式的一般特性值得注意：  
  
-   傳送的 SQL 陳述式是 UPDATE 陳述式。 配接器知道要使用 UPDATE 陳述式，因為值<xref:System.Data.DataRow.RowState%2A>屬性是<xref:System.Data.DataRowState>。  
  
-   傳送的 SQL 陳述式包含 WHERE 子句的 UPDATE 陳述式的目標資料列，指出其中`CustomerID = 'c400'`。 SELECT 陳述式的這個部分會區分來自其他所有用途的目標資料列因為`CustomerID`是目標資料表的主索引鍵。 WHERE 子句衍生自資料錄的原始版本的資訊 (`DataRowVersion.Original`)，以免才能識別資料列的值已變更。  
  
-   傳送的 SQL 陳述式包含的 SET 子句，來設定新的已修改的資料行的值。  
  
    > [!NOTE]
    >  如果使用的 TableAdapter`UpdateCommand`屬性設定為預存程序的名稱、 配接器將不會建構 SQL 陳述式。 相反地，它會叫用預存程序以適當的參數傳入。  
  
## <a name="passing-parameters"></a>傳遞參數  
 通常，您會使用參數來傳遞要更新資料庫中的資料錄的值。  當 TableAdapter 的`Update`方法會執行 UPDATE 陳述式，它必須填寫的參數值。 它會取得這些值從`Parameters`適當的資料命令的集合，在此情況下，`UpdateCommand`在 TableAdapter 中的物件。  
  
 如果您已使用 Visual Studio 工具來產生資料配接器`UpdateCommand`物件包含對應至每個陳述式中的參數預留位置的參數集合。  
  
 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName>每個參數的屬性會指向資料表中的資料行。 例如，`SourceColumn`屬性`au_id`和`Original_au_id`參數設定為資料表中的任何資料行包含的作者 id。當配接器的`Update`方法執行時，它會讀取作者識別碼資料行從正在進行更新，將值填入陳述式的記錄。  
  
 在 UPDATE 陳述式，您需要指定這兩個新的值 （其會將寫入的記錄），以及舊值 （以便可以在資料庫中找到記錄）。 因此有每個值的兩個參數： 一個用於 SET 子句，WHERE 子句，另一種。 這兩個參數會讀取更新時，記錄中的資料，但他們會收到不同版本的資料行值的參數為基礎[SqlParameter.SourceVersion 屬性](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx)。 SET 子句的參數取得最新版本，和 WHERE 子句的參數取得原始的版本。  
  
> [!NOTE]
>  您也可以在 設定值`Parameters`收集程式碼，您通常會執行中的資料配接器的事件處理常式中自行<xref:System.Data.DataTable.RowChanging>事件。  
  
## <a name="see-also"></a>另請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)   
 [在 Visual Studio 中的資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)

