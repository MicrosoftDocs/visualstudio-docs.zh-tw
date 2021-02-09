---
title: 驗證資料集中的資料
description: 瞭解如何驗證資料集中的資料。 驗證資料涉及確認輸入至資料物件的值符合資料集架構內的條件約束。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1db0f53ffc049d8844d7447461c4c33a0492a2d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858237"
---
# <a name="validate-data-in-datasets"></a>驗證資料集中的資料
驗證資料是確認在資料物件中輸入的值符合資料集架構內之條件約束的程式。 驗證程式也會確認這些值是否遵循針對您的應用程式所建立的規則。 先驗證資料再將更新傳送至基礎資料庫是很好的作法。 這可減少錯誤，以及應用程式與資料庫之間的潛在往返次數。

您可以藉由建立資料集本身的驗證檢查，來確認要寫入資料集的資料是有效的。 無論如何執行更新，資料集都可以檢查資料，無論是直接由表單中的控制項、元件內的控制項，或以其他方式進行。 因為資料集是您應用程式的一部分 (與資料庫後端) 不同，所以這是建立應用程式特定驗證的邏輯位置。

將驗證新增至您的應用程式的最佳位置是在資料集的部分類別檔案中。 在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 或中 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ，開啟 **DataSet 設計工具** ，然後按兩下您想要建立驗證的資料行或資料表。 此動作會自動建立 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件處理常式。

## <a name="validate-data"></a>驗證資料
您可以透過下列方式來完成資料集內的驗證：

- 藉由建立您自己的應用程式特定驗證，在變更期間檢查個別資料行中的值。 如需詳細資訊，請參閱 [如何：在資料行變更期間驗證資料](validate-data-in-datasets.md)。

- 藉由建立您自己的應用程式特定驗證，在整個資料列變更時，將資料檢查至值。 如需詳細資訊，請參閱 [如何：在資料列變更期間驗證資料](validate-data-in-datasets.md)。

- 藉由建立索引鍵、唯一條件約束等，做為資料集實際架構定義的一部分。

- 藉由設定物件的屬性 <xref:System.Data.DataColumn> ，例如 <xref:System.Data.DataColumn.MaxLength%2A> 、 <xref:System.Data.DataColumn.AllowDBNull%2A> 和 <xref:System.Data.DataColumn.Unique%2A> 。

<xref:System.Data.DataTable>當記錄中發生變更時，物件會引發數個事件：

- <xref:System.Data.DataTable.ColumnChanging>和 <xref:System.Data.DataTable.ColumnChanged> 事件會在每次變更個別資料行的期間和之後引發。 <xref:System.Data.DataTable.ColumnChanging>當您想要驗證特定資料行中的變更時，這個事件就很有用。 建議的變更相關資訊會以引數的形式傳遞給事件。
- <xref:System.Data.DataTable.RowChanging>和事件會在資料列中的 <xref:System.Data.DataTable.RowChanged> 任何變更期間和之後引發。 <xref:System.Data.DataTable.RowChanging>事件更為普遍。 這表示資料列中某處發生變更，但您不知道哪個資料行已變更。

依預設，資料行的每個變更都會引發四個事件。 第一個是 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> 要變更之特定資料行的和事件。 接下來是 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。 如果對資料列進行多項變更，就會針對每個變更引發事件。

> [!NOTE]
> 資料 <xref:System.Data.DataRow.BeginEdit%2A> 列的方法會 <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> 在每個個別資料行變更之後，關閉和事件。 在這種情況下，在 <xref:System.Data.DataRow.EndEdit%2A> 呼叫方法之前，如果 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件只引發一次，則不會引發事件。 如需詳細資訊，請參閱 [在填滿資料集時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。

您所選擇的事件取決於您想要驗證的細微程度。 如果您一定要在資料行變更時立即攔截錯誤，請使用事件來建立驗證 <xref:System.Data.DataTable.ColumnChanging> 。 否則，請使用 <xref:System.Data.DataTable.RowChanging> 事件，這可能會一次捕捉到數個錯誤。 此外，如果您的資料是結構化的，以便根據另一個資料行的內容來驗證某個資料行的值，請在事件期間執行驗證 <xref:System.Data.DataTable.RowChanging> 。

當記錄更新時， <xref:System.Data.DataTable> 物件會引發事件，讓您可以在變更發生時以及進行變更之後回應。

如果您的應用程式使用具類型的資料集，您可以建立強型別的事件處理常式。 這會加入四個您可以建立處理常式的其他具類型事件： `dataTableNameRowChanging` 、 `dataTableNameRowChanged` 、 `dataTableNameRowDeleting` 和 `dataTableNameRowDeleted` 。 這些具類型的事件處理常式會傳遞引數，其中包含資料表的資料行名稱，使程式碼更容易寫入和讀取。

## <a name="data-update-events"></a>資料更新事件

|事件|描述|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|正在變更資料行中的值。 事件會將資料列和資料行傳遞給您，以及建議的新值。|
|<xref:System.Data.DataTable.ColumnChanged>|資料行中的值已變更。 事件會將資料列和資料行傳遞給您，以及建議的值。|
|<xref:System.Data.DataTable.RowChanging>|對物件所做的變更 <xref:System.Data.DataRow> 即將認可回資料集。 如果您未呼叫 <xref:System.Data.DataRow.BeginEdit%2A> 方法，則會在 <xref:System.Data.DataTable.RowChanging> 引發事件之後，立即針對資料行的每個變更引發事件 <xref:System.Data.DataTable.ColumnChanging> 。 如果您在 <xref:System.Data.DataRow.BeginEdit%2A> 進行變更之前呼叫， <xref:System.Data.DataTable.RowChanging> 只會在您呼叫方法時引發事件 <xref:System.Data.DataRow.EndEdit%2A> 。<br /><br /> 此事件會將資料列傳遞給您，並提供一個值，指出 (變更、插入等) 正在執行的動作類型。|
|<xref:System.Data.DataTable.RowChanged>|資料列已變更。 此事件會將資料列傳遞給您，並提供一個值，指出 (變更、插入等) 正在執行的動作類型。|
|<xref:System.Data.DataTable.RowDeleting>|正在刪除資料列。 事件會將資料列傳遞給您，以及表示正在執行 (刪除) 動作類型的值。|
|<xref:System.Data.DataTable.RowDeleted>|已刪除資料列。 事件會將資料列傳遞給您，以及表示正在執行 (刪除) 動作類型的值。|

在 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowDeleting> 更新過程中，會引發、和事件。 您可以使用這些事件來驗證資料或執行其他類型的處理。 因為更新是在這些事件期間進行，所以您可以藉由擲回例外狀況來取消更新，這會導致無法完成更新。

<xref:System.Data.DataTable.ColumnChanged>、 <xref:System.Data.DataTable.RowChanged> 和 <xref:System.Data.DataTable.RowDeleted> 事件是在更新成功完成時引發的通知事件。 當您想要根據成功的更新採取進一步的動作時，這些事件會很有用。

## <a name="validate-data-during-column-changes"></a>在資料行變更期間驗證資料

> [!NOTE]
> **DataSet 設計工具** 會建立可將驗證邏輯加入至資料集的部分類別。 設計工具產生的資料集不會刪除或變更部分類別中的任何程式碼。

您可以藉由回應事件來變更資料行中的值，以驗證資料 <xref:System.Data.DataTable.ColumnChanging> 。 引發時，此事件會傳遞事件引數 (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) ，其中包含目前資料行所建議的值。 根據的內容 `e.ProposedValue` ，您可以：

- 不執行任何動作來接受建議的值。

- <xref:System.Data.DataRow.SetColumnError%2A>從資料行變更事件處理常式內設定資料行錯誤 () ，以拒絕建議的值。

- 選擇性地使用 <xref:System.Windows.Forms.ErrorProvider> 控制項向使用者顯示錯誤訊息。 如需詳細資訊，請參閱 [ErrorProvider 元件](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)。

您也可以在事件期間執行驗證 <xref:System.Data.DataTable.RowChanging> 。

## <a name="validate-data-during-row-changes"></a>在資料列變更期間驗證資料
您可以撰寫程式碼來確認您想要驗證的每個資料行都包含符合您應用程式需求的資料。 若要這麼做，請設定資料行，以指出如果無法接受建議的值，則會包含錯誤。 下列範例會在資料行小於或等於0時設定資料行錯誤 `Quantity` 。 資料列變更事件處理常式應該類似于下列範例。

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>若要在資料列變更時驗證資料 (Visual Basic) 

1. 在 [DataSet 設計工具] 中開啟資料集。 如需詳細資訊，請參閱 [逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 按兩下要驗證之資料表的標題列。 此動作會自動 <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable> 在資料集的部分類別檔案中建立的事件處理常式。

    > [!TIP]
    > 按兩下資料表名稱的左邊，以建立資料列變更事件處理常式。 如果您按兩下資料表名稱，就可以編輯它。

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>若要在資料列變更時驗證資料 (c # ) 

1. 在 [DataSet 設計工具] 中開啟資料集。 如需詳細資訊，請參閱 [逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 按兩下要驗證之資料表的標題列。 此動作會建立的部分類別檔案 <xref:System.Data.DataTable> 。

    > [!NOTE]
    > **DataSet 設計工具** 不會自動建立事件的事件處理常式 <xref:System.Data.DataTable.RowChanging> 。 您必須建立方法來處理 <xref:System.Data.DataTable.RowChanging> 事件，並執行程式碼以將事件連結至資料表的初始化方法。

3. 將下列程式碼複製到部分類別中：

    ```csharp
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

## <a name="to-retrieve-changed-rows"></a>若要取出變更的資料列
資料表中的每個資料列都有一個 <xref:System.Data.DataRow.RowState%2A> 屬性，此屬性會使用列舉中的值來追蹤該資料列的目前狀態 <xref:System.Data.DataRowState> 。 您可以藉由呼叫或的方法，從資料集或資料表傳回已變更的資料列 `GetChanges` <xref:System.Data.DataSet> <xref:System.Data.DataTable> 。 您可以藉 `GetChanges` 由呼叫資料集的方法，在呼叫之前確認變更是否存在 <xref:System.Data.DataSet.HasChanges%2A> 。

> [!NOTE]
> 當您藉由呼叫) 方法 (，將變更認可至資料集或資料表之後 <xref:System.Data.DataSet.AcceptChanges%2A> ，此 `GetChanges` 方法不會傳回任何資料。 如果您的應用程式需要處理已變更的資料列，您必須在呼叫方法之前先處理變更 `AcceptChanges` 。

呼叫 <xref:System.Data.DataSet.GetChanges%2A> 資料集或資料表的方法會傳回新的資料集或資料表，其中只包含已變更的記錄。 如果您想要取得特定記錄（例如，只有新的記錄或僅限修改過的記錄），您可以將值從 <xref:System.Data.DataRowState> 列舉作為參數傳遞給 `GetChanges` 方法。

您 <xref:System.Data.DataRowVersion> 可以使用列舉來存取資料列的不同版本 (例如，在處理資料列之前的原始值) 。

### <a name="to-get-all-changed-records-from-a-dataset"></a>從資料集取得所有變更的記錄

- 呼叫 <xref:System.Data.DataSet.GetChanges%2A> 資料集的方法。

     下列範例會建立名為的新資料集 `changedRecords` ，並從另一個稱為的資料集填入所有變更的記錄 `dataSet1` 。

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>從資料表取得所有變更的記錄

- 呼叫 <xref:System.Data.DataTable.GetChanges%2A> DataTable 的方法。

     下列範例會建立名為的新資料表 `changedRecordsTable` ，並在其中填入來自另一個資料表的已變更記錄 `dataTable1` 。

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>取得具有特定資料列狀態的所有記錄

- 呼叫 `GetChanges` 資料集或資料表的方法，並傳遞 <xref:System.Data.DataRowState> 列舉值做為引數。

     下列範例將示範如何建立名為的新資料集 `addedRecords` ，並只在其中填入已加入至 `dataSet1` 資料集的記錄。

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     下列範例顯示如何傳回最近新增至資料表的所有記錄 `Customers` ：

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>存取 DataRow 的原始版本
對資料列進行變更時，資料集會同時保留原始 (<xref:System.Data.DataRowVersion.Original>) 和新的 (<xref:System.Data.DataRowVersion.Current>) 版本的資料列。 例如，在呼叫方法之前 `AcceptChanges` ，您的應用程式可以存取不同版本的記錄 (如列舉) 中所定義 <xref:System.Data.DataRowVersion> ，然後據以處理變更。

> [!NOTE]
> 資料列的不同版本只會在編輯之後，以及在 `AcceptChanges` 呼叫方法之前存在。 在 `AcceptChanges` 呼叫方法之後，目前的和原始版本都相同。

以 <xref:System.Data.DataRowVersion> 字串的形式傳遞值 (或資料行名稱，) 會從該資料行的特定資料列版本傳回值。 在和事件期間會識別已變更的資料行 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> 。 針對驗證目的，這是檢查不同資料列版本的好時機。 但是，如果您已暫時暫停條件約束，則不會引發這些事件，您必須以程式設計的方式識別哪些資料行已變更。 您可以逐一查看 <xref:System.Data.DataTable.Columns%2A> 集合並比較不同的值，來執行這項作業 <xref:System.Data.DataRowVersion> 。

### <a name="to-get-the-original-version-of-a-record"></a>取得記錄的原始版本

- 傳遞您要傳回之資料列的，以存取資料行的值 <xref:System.Data.DataRowVersion> 。

     下列範例示範如何使用 <xref:System.Data.DataRowVersion> 值來取得中欄位的原始值 `CompanyName` <xref:System.Data.DataRow> ：

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>存取 DataRow 的目前版本

### <a name="to-get-the-current-version-of-a-record"></a>取得記錄的目前版本

- 存取資料行的值，然後將參數加入至索引，指出您想要傳回的資料列版本。

     下列範例示範如何使用 <xref:System.Data.DataRowVersion> 值來取得中欄位的目前值 `CompanyName` <xref:System.Data.DataRow> ：

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [如何：驗證 Windows Forms DataGridView 控制項中的資料](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [如何：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
