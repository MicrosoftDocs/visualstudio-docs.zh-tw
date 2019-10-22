---
title: 驗證資料集中的資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d42553fbee6de6a89e16716a191db8a3d9fb883
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621060"
---
# <a name="validate-data-in-datasets"></a>驗證資料集中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

驗證資料是確認在資料物件中輸入的值符合資料集架構內之條件約束的程式。 驗證程式也會確認這些值都遵循為您的應用程式所建立的規則。 在將更新傳送至基礎資料庫之前，先驗證資料是很好的作法。 這可減少錯誤，以及應用程式與資料庫之間的可能往返次數。

 您可以藉由在資料集內建立驗證檢查，確認寫入資料集的資料是有效的。 不論執行更新的方式為何，資料集都可以檢查資料，無論是直接由表單中的控制項、元件內，或是以其他方式進行。 因為資料集是您應用程式的一部分（不同于資料庫後端），所以它是建立應用程式特定驗證的邏輯位置。

 將驗證新增至應用程式的最佳位置是在資料集的部分類別檔案中。 在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 中，開啟**DataSet 設計工具**，然後按兩下您要建立驗證的資料行或資料表。 此動作會自動建立 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件處理常式。 如需詳細資訊，請參閱[如何：在資料行變更期間驗證資料](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)或[如何：在資料列變更期間驗證資料](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)。 如需完整範例，請參閱[逐步解說：將驗證加入至資料集](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7)。

## <a name="validate-data"></a>驗證資料
 您可以透過下列方式來完成資料集內的驗證：

- 藉由建立您自己的應用程式特定驗證，可以在變更期間檢查個別資料行中的值。  如需詳細資訊，請參閱[如何：在資料行變更期間驗證資料](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)。

- 藉由建立您自己的應用程式特定驗證，在整個資料列變更時，可以將資料檢查為值。 如需詳細資訊，請參閱[如何：在資料列變更期間驗證資料](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)。

- 藉由建立索引鍵、唯一的條件約束等，做為資料集實際架構定義的一部分。 如需將驗證併入架構定義中的詳細資訊，請參閱[限制 DataColumn 以包含唯一值](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)。

- 藉由設定 <xref:System.Data.DataColumn> 物件的屬性，例如 <xref:System.Data.DataColumn.MaxLength%2A>、<xref:System.Data.DataColumn.AllowDBNull%2A> 和 <xref:System.Data.DataColumn.Unique%2A>。

  當記錄中發生變更時，<xref:System.Data.DataTable> 物件會引發數個事件：

- @No__t_0 和 <xref:System.Data.DataTable.ColumnChanged> 事件會在每次變更個別資料行期間和之後引發。 當您想要驗證特定資料行中的變更時，<xref:System.Data.DataTable.ColumnChanging> 事件會很有用。 建議變更的相關資訊會以引數的形式傳遞至事件。 如需詳細資訊，請參閱[如何：在資料行變更期間驗證資料](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)。

- @No__t_0 和 <xref:System.Data.DataTable.RowChanged> 事件會在資料列中的任何變更期間和之後引發。 @No__t_0 事件較一般。 這表示資料列中的某處發生了變更，但您不知道哪個資料行已變更。 如需詳細資訊，請參閱[如何：在資料列變更期間驗證資料](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)。

  根據預設，資料行的每個變更都因此引發四個事件。 第一個是要變更之特定資料行的 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.ColumnChanged> 事件。 接下來是 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。 如果對資料列進行多項變更，則會針對每個變更引發事件。

> [!NOTE]
> 資料列的 <xref:System.Data.DataRow.BeginEdit%2A> 方法會關閉每個個別資料行變更後的 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。 在這種情況下，在呼叫 <xref:System.Data.DataRow.EndEdit%2A> 方法之前，只引發 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件一次，就不會引發事件。 如需詳細資訊，請參閱[填入資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。

 您所選擇的事件取決於您想要驗證的細微程度。 如果資料行變更時，請務必立即攔截錯誤，請使用 <xref:System.Data.DataTable.ColumnChanging> 事件來建立驗證。 否則，請使用 <xref:System.Data.DataTable.RowChanging> 事件，這可能會一次捕捉數個錯誤。 此外，如果您的資料是結構化的，因此會根據另一個資料行的內容來驗證一個資料行的值，然後在 <xref:System.Data.DataTable.RowChanging> 事件期間執行驗證。

 當記錄更新時，<xref:System.Data.DataTable> 物件會引發事件，您可以在發生變更和變更之後，回應這些事件。

 如果您的應用程式使用具類型的資料集，您可以建立強型別的事件處理常式。 這會加入四個額外的具型別事件，您可以在其中建立處理常式： `dataTableNameRowChanging`、`dataTableNameRowChanged`、`dataTableNameRowDeleting` 和 `dataTableNameRowDeleted`。 這些具類型的事件處理常式會傳遞引數，其中包含您資料表的資料行名稱，讓程式碼更容易寫入和讀取。

## <a name="data-update-events"></a>資料更新事件

|Event - 事件|描述|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|正在變更資料行中的值。 事件會將資料列和資料行傳遞給您，以及建議的新值。|
|<xref:System.Data.DataTable.ColumnChanged>|資料行中的值已變更。 事件會將資料列和資料行傳遞給您，以及建議的值。|
|<xref:System.Data.DataTable.RowChanging>|對 <xref:System.Data.DataRow> 物件所做的變更即將認可回資料集。 如果您尚未呼叫 <xref:System.Data.DataRow.BeginEdit%2A> 方法，就會在引發 <xref:System.Data.DataTable.ColumnChanging> 事件之後，立即針對資料行的每個變更引發 <xref:System.Data.DataTable.RowChanging> 事件。 如果您在進行變更之前呼叫 <xref:System.Data.DataRow.BeginEdit%2A>，只有在呼叫 <xref:System.Data.DataRow.EndEdit%2A> 方法時，才會引發 <xref:System.Data.DataTable.RowChanging> 事件。<br /><br /> 事件會將資料列傳遞給您，以及指出正在執行哪種類型的動作（變更、插入等等）的值。|
|<xref:System.Data.DataTable.RowChanged>|資料列已經變更。 事件會將資料列傳遞給您，以及指出正在執行哪種類型的動作（變更、插入等等）的值。|
|<xref:System.Data.DataTable.RowDeleting>|正在刪除資料列。 事件會將資料列傳遞給您，以及指出正在執行哪種類型的動作（delete）的值。|
|<xref:System.Data.DataTable.RowDeleted>|已刪除資料列。 事件會將資料列傳遞給您，以及指出正在執行哪種類型的動作（delete）的值。|

 @No__t_0、<xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowDeleting> 事件會在更新程式期間引發。 您可以使用這些事件來驗證資料，或執行其他類型的處理。 因為在這些事件期間正在進行更新，所以您可以藉由擲回例外狀況來取消它，這會使更新無法完成。

 @No__t_0、<xref:System.Data.DataTable.RowChanged> 和 <xref:System.Data.DataTable.RowDeleted> 事件是更新順利完成時所引發的通知事件。 當您想要根據成功的更新採取進一步的動作時，這些事件會很有用。

## <a name="validate-data-during-column-changes"></a>在資料行變更期間驗證資料

> [!NOTE]
> **DataSet 設計工具**會建立可將驗證邏輯加入至資料集的部分類別。 設計工具產生的資料集不會刪除或變更部分類別中的任何程式碼。

 當資料行中的值因回應 <xref:System.Data.DataTable.ColumnChanging> 事件而變更時，您可以驗證資料。 當引發時，這個事件會傳遞事件引數（<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>），其中包含目前資料行所建議的值。 根據 `e.ProposedValue` 的內容，您可以：

- 不執行任何動作以接受建議的值。

- 從資料行變更事件處理常式中設定資料行錯誤（<xref:System.Data.DataRow.SetColumnError%2A>），以拒絕建議的值。

- 選擇性地使用 <xref:System.Windows.Forms.ErrorProvider> 控制項向使用者顯示錯誤訊息。 如需詳細資訊，請參閱[ErrorProvider 元件](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6)。

  驗證也可以在 <xref:System.Data.DataTable.RowChanging> 事件期間執行。 如需詳細資訊，請參閱[如何：在資料列變更期間驗證資料](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)。

## <a name="validate-data-during-row-changes"></a>在資料列變更期間驗證資料
 您可以撰寫程式碼，確認您想要驗證的每個資料行都包含符合應用程式需求的資料。 若要這麼做，請將資料行設定為，以指出當建議的值無法接受時，它會包含錯誤。 下列範例會在 `Quantity` 資料行小於或等於0時，設定資料行錯誤。 資料列變更事件處理常式應該類似下列範例。

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>若要在資料列變更時驗證資料（Visual Basic）

1. 在 [DataSet 設計工具] 中開啟資料集。 如需詳細資訊，請參閱[如何：在 DataSet 設計工具中開啟資料集](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。

2. 按兩下您想要驗證之資料表的標題列。 此動作會自動在資料集的部分類別檔案中建立 <xref:System.Data.DataTable> 的 <xref:System.Data.DataTable.RowChanging> 事件處理常式。

    > [!TIP]
    > 按兩下資料表名稱的左邊，以建立資料列變更事件處理常式。 如果您按兩下資料表名稱，就可以進行編輯。

     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>若要在資料列變更時驗證C#資料（）

1. 在 [DataSet 設計工具] 中開啟資料集。 如需詳細資訊，請參閱[如何：在 DataSet 設計工具中開啟資料集](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。

2. 按兩下您想要驗證之資料表的標題列。 此動作會建立 <xref:System.Data.DataTable> 的部分類別檔案。

    > [!NOTE]
    > **DataSet 設計工具**不會自動建立 <xref:System.Data.DataTable.RowChanging> 事件的事件處理常式。 您必須建立方法來處理 <xref:System.Data.DataTable.RowChanging> 事件，並執行程式碼來連結資料表的初始化方法中的事件。

3. 將下列程式碼複製到部分類別中：

    ```
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>若要取出已變更的資料列
 資料表中的每個資料列都有一個 <xref:System.Data.DataRow.RowState%2A> 屬性，可使用 <xref:System.Data.DataRowState> 列舉中的值來追蹤該資料列的目前狀態。 您可以藉由呼叫 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 的 `GetChanges` 方法，從資料集或資料表傳回已變更的資料列。 您可以藉由呼叫 dataset 的 <xref:System.Data.DataSet.HasChanges%2A> 方法，在呼叫 `GetChanges` 之前，確認有變更存在。 如需 <xref:System.Data.DataSet.HasChanges%2A> 的詳細資訊，請參閱[如何：檢查已變更的資料列](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653)。

> [!NOTE]
> 在您將變更認可至資料集或資料表（藉由呼叫 <xref:System.Data.DataSet.AcceptChanges%2A> 方法）之後，`GetChanges` 方法不會傳回任何資料。 如果您的應用程式需要處理已變更的資料列，您必須先處理這些變更，然後再呼叫 `AcceptChanges` 方法。

 呼叫資料集或資料表的 <xref:System.Data.DataSet.GetChanges%2A> 方法，會傳回新的資料集或資料表，其中只包含已變更的記錄。 如果您想要取得特定記錄（例如，只有新的記錄或僅修改的記錄），您可以將值從 <xref:System.Data.DataRowState> 列舉當做參數傳遞至 `GetChanges` 方法。

 使用 <xref:System.Data.DataRowVersion> 列舉來存取資料列的不同版本（例如，在處理資料列前的原始值）。

#### <a name="to-get-all-changed-records-from-a-dataset"></a>從資料集取得所有已變更的記錄

- 呼叫資料集的 <xref:System.Data.DataSet.GetChanges%2A> 方法。

     下列範例會建立名為 `changedRecords` 的新資料集，並在其中填入另一個稱為 `dataSet1` 的資料集的已變更記錄。

     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>從資料表取得所有已變更的記錄

- 呼叫 DataTable 的 <xref:System.Data.DataTable.GetChanges%2A> 方法。

     下列範例會建立稱為 `changedRecordsTable` 的新資料表，並在其中填入另一個稱為 `dataTable1` 的資料表中已變更的記錄。

     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>取得具有特定資料列狀態的所有記錄

- 呼叫 dataset 或資料表的 `GetChanges` 方法，並傳遞 <xref:System.Data.DataRowState> 列舉值做為引數。

     下列範例示範如何建立名為 `addedRecords` 的新資料集，並只填入已加入至 `dataSet1` 資料集的記錄。

     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]

- 下列範例示範如何傳回最近新增至 `Customers` 資料表的所有記錄：

     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]

## <a name="access-the-original-version-of-a-datarow"></a>存取 DataRow 的原始版本
 當對資料列進行變更時，資料集會同時保留原始（<xref:System.Data.DataRowVersion>）和資料列的新（<xref:System.Data.DataRowVersion>）版本。 例如，在呼叫 `AcceptChanges` 方法之前，您的應用程式可以存取不同版本的記錄（如 <xref:System.Data.DataRowVersion> 列舉中所定義），並據此處理變更。

> [!NOTE]
> 資料列的不同版本只有在編輯之後，以及在呼叫 `AcceptChanges` 方法之前，才會存在。 呼叫 `AcceptChanges` 方法之後，目前和原始版本會相同。

 傳遞 <xref:System.Data.DataRowVersion> 值以及資料行索引（或資料行名稱為字串），會從該資料行的特定資料列版本傳回值。 在 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.ColumnChanged> 事件期間，會識別已變更的資料行。 這是檢查不同資料列版本以進行驗證的好時機。 不過，如果您已暫時暫止條件約束，就不會引發這些事件，而且您必須以程式設計方式識別哪些資料行已變更。 若要這麼做，您可以逐一查看 <xref:System.Data.DataTable.Columns%2A> 集合，並比較不同的 <xref:System.Data.DataRowVersion> 值。

#### <a name="to-get-the-original-version-of-a-record"></a>取得記錄的原始版本

- 藉由傳入您想要傳回之資料列的 <xref:System.Data.DataRowVersion>，來存取資料行的值。

     下列範例示範如何使用 <xref:System.Data.DataRowVersion> 值來取得 <xref:System.Data.DataRow> 中 `CompanyName` 欄位的原始值：

     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]

## <a name="access-the-current-version-of-a-datarow"></a>存取 DataRow 的目前版本

#### <a name="to-get-the-current-version-of-a-record"></a>取得記錄的目前版本

- 存取資料行的值，然後將參數加入至索引，以指出您要傳回的資料列版本。

     下列範例顯示如何使用 <xref:System.Data.DataRowVersion> 值，取得 <xref:System.Data.DataRow> 中 `CompanyName` 欄位的目前值：

     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]

## <a name="see-also"></a>請參閱

- [操作說明：驗證 Windows Forms DataGridView 控制項中的資料](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)
- [操作說明：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)