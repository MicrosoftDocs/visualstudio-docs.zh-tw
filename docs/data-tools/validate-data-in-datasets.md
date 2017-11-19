---
title: "驗證資料在資料集中 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0f328cbaac03680885bdbda97dff7bc9ac3cf2cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="validate-data-in-datasets"></a>驗證資料集的資料
驗證資料是確認的程序的輸入資料物件的值符合資料集的結構描述中的條件約束。 驗證程序也會確認這些值會遵循您的應用程式已建立的規則。 它是最好的作法是驗證之前將更新傳送至基礎資料庫的資料。 這會減少錯誤，以及可能的應用程式與資料庫之間的往返次數。  
  
您可以確認正在寫入至資料集的資料無效建置到本身的資料集的驗證檢查。 資料集可以檢查資料，不論如何執行更新時，直接由控制項在表單中，元件，或以其他方法。 因為資料集是您的應用程式 （不同於後端資料庫） 的一部分，所以在邏輯上建置應用程式特定的驗證。  
  
若要將驗證加入至您的應用程式的最佳位置是資料集的部分類別檔案中。 在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]，開啟**Dataset 設計工具**連按兩下您要建立驗證的資料行或資料表。 這個動作會自動建立<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>事件處理常式。 
  
## <a name="validate-data"></a>驗證資料  
 資料集內的驗證可以下列方式完成：  
  
-   藉由建立您自己的應用程式的特定驗證中個別資料行的值變更期間檢查。  如需詳細資訊，請參閱[How to： 驗證期間資料行變更的資料](validate-data-in-datasets.md)。  
  
-   建立您自己的應用程式特定驗證，檢查值在整個資料的資料會變更資料列。 如需詳細資訊，請參閱[How to： 驗證期間資料列變更的資料](validate-data-in-datasets.md)。  
  
-   做為實際的結構描述定義的資料集的一部分，依此類推建立機碼，唯一的條件約束。 
  
-   藉由設定屬性<xref:System.Data.DataColumn>物件，例如<xref:System.Data.DataColumn.MaxLength%2A>， <xref:System.Data.DataColumn.AllowDBNull%2A>，和<xref:System.Data.DataColumn.Unique%2A>。  
  
多個事件所引發<xref:System.Data.DataTable>物件正在記錄發生變更時：  
  
-   <xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.ColumnChanged>期間和個別的資料行的每個變更之後，會引發事件。 <xref:System.Data.DataTable.ColumnChanging>事件很實用，當您想要驗證特定資料行中的變更。 提議的變更的相關資訊會傳遞做為引數與事件。 
-   <xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>期間和之後任何引發事件的資料列變更。 <xref:System.Data.DataTable.RowChanging>事件是更廣泛。 這表示資料列，在某處發生變更，但是您不知道哪個資料行已變更。  
  
根據預設，每個資料行的變更，因此引發四個事件。 第一個是<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.ColumnChanged>正在變更的特定資料行的事件。 接下來的<xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>事件。 如果多個要變更資料列，每項變更將會引發事件。  
  
> [!NOTE]
>  資料列<xref:System.Data.DataRow.BeginEdit%2A>方法會關閉<xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>之後每個個別資料行變更的事件。 在此情況下，不會引發事件之前<xref:System.Data.DataRow.EndEdit%2A>已呼叫方法，當<xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>就可以一次引發事件。 如需詳細資訊，請參閱[填入 dataset 時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
您想要驗證方式的細微取決於您選擇的事件。 如果必須立即在資料行的變更時，攔截錯誤，驗證使用建置<xref:System.Data.DataTable.ColumnChanging>事件。 否則，請使用<xref:System.Data.DataTable.RowChanging>事件，可能會導致一次擷取數個錯誤。 此外，如果您的資料結構化，一個資料行的值會根據另一個資料行的內容驗證，然後執行驗證期間<xref:System.Data.DataTable.RowChanging>事件。
  
在更新記錄時<xref:System.Data.DataTable>物件會引發事件，您可以回應時所發生的變更，並進行變更之後。  
  
如果您的應用程式會使用具類型資料集，您可以建立強類型的事件處理常式。 這會新增四個額外的具類型的事件，您可以建立處理常式： `dataTableNameRowChanging`， `dataTableNameRowChanged`， `dataTableNameRowDeleting`，和`dataTableNameRowDeleted`。 這些具類型的事件處理常式傳遞引數，其中包含讓程式碼更容易寫入和讀取您的資料表資料行名稱。  
  
## <a name="data-update-events"></a>資料更新事件  
  
|事件|說明|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|正在變更的資料行中的值。 事件傳遞資料列和資料行，以及建議的新值。|  
|<xref:System.Data.DataTable.ColumnChanged>|已變更資料行中的值。 事件傳遞資料列和資料行，以及建議的值。|  
|<xref:System.Data.DataTable.RowChanging>|對所做的變更<xref:System.Data.DataRow>物件即將回資料集進行認可。 如果尚未呼叫<xref:System.Data.DataRow.BeginEdit%2A>方法，<xref:System.Data.DataTable.RowChanging>的每個資料行的變更都會引發事件之後立即<xref:System.Data.DataTable.ColumnChanging>在引發事件。 如果您呼叫<xref:System.Data.DataRow.BeginEdit%2A>再進行變更，<xref:System.Data.DataTable.RowChanging>只有當您呼叫時，就會引發事件<xref:System.Data.DataRow.EndEdit%2A>方法。<br /><br /> 這個事件會給您，傳遞資料列，以及值，指出正在執行的動作 （例如變更、 插入、 等等） 類型。|  
|<xref:System.Data.DataTable.RowChanged>|已變更的資料列。 這個事件會給您，傳遞資料列，以及值，指出正在執行的動作 （例如變更、 插入、 等等） 類型。|  
|<xref:System.Data.DataTable.RowDeleting>|正在刪除一個資料列。 這個事件會給您，傳遞資料列，以及值，指出正在執行的動作 (delete) 類型。|  
|<xref:System.Data.DataTable.RowDeleted>|已刪除資料列。 這個事件會給您，傳遞資料列，以及值，指出正在執行的動作 (delete) 類型。|  
  
<xref:System.Data.DataTable.ColumnChanging>， <xref:System.Data.DataTable.RowChanging>，和<xref:System.Data.DataTable.RowDeleting>更新程序期間引發事件。 您可以使用這些事件來驗證資料，或是執行其他類型的處理。 因為更新程序在這些事件時，可以取消藉由擲回例外狀況，如此可防止從更新完成。  
  
<xref:System.Data.DataTable.ColumnChanged>，<xref:System.Data.DataTable.RowChanged>和<xref:System.Data.DataTable.RowDeleted>事件是更新已成功完成時，會引發通知事件。 當您想要採取進一步的動作成功更新為基礎，這些事件很實用。  
  
## <a name="validate-data-during-column-changes"></a>資料行變更期間驗證資料  
  
> [!NOTE]
>  **Dataset 設計工具**建立部分類別中的驗證邏輯加入至資料集。 設計工具產生的資料集不會刪除，或變更的部分類別中的任何程式碼。  
  
您可以在回應中的資料行的值變更時驗證資料<xref:System.Data.DataTable.ColumnChanging>事件。 此事件引發時，事件引數傳遞 (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>)，其中包含會被提議為目前的資料行的值。 根據內容`e.ProposedValue`，您可以：  
  
-   不進行任何動作，以接受建議的值。  
  
-   藉由設定資料行錯誤拒絕建議的值 (<xref:System.Data.DataRow.SetColumnError%2A>) 從在資料行變更事件處理常式。  
  
-   選擇性地使用<xref:System.Windows.Forms.ErrorProvider>控制項來顯示錯誤訊息給使用者。 如需詳細資訊，請參閱[ErrorProvider 元件](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)。  
  
您也可以驗證執行期間<xref:System.Data.DataTable.RowChanging>事件。 
  
## <a name="validate-data-during-row-changes"></a>資料列變更期間驗證資料  
您可以撰寫程式碼來確認您想要驗證每個資料的行包含符合您的應用程式需求的資料。 藉由設定資料行，以表示它包含錯誤，是否無法接受建議的值執行這項操作。 下列範例會設定資料行發生錯誤時`Quantity`資料行是 0 或更少。 資料列變更的事件處理常式應該類似下列的範例。  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>若要驗證的資料列時的資料變更 (Visual Basic)  
  
1.  開啟您的資料集在**Dataset 設計工具**。 如需詳細資訊，請參閱[逐步解說： 在 Dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  按兩下您想要驗證之資料表的標題列。 這個動作會自動建立<xref:System.Data.DataTable.RowChanging>事件處理常式<xref:System.Data.DataTable>資料集的部分類別檔案中。  
  
    > [!TIP]
    >  按兩下左邊的資料表名稱來建立資料列變更的事件處理常式。 如果您按兩下資料表名稱時，您可以編輯它。  
  
     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>若要驗證的資料列時的資料變更 (C#)  
  
1.  開啟您的資料集在**Dataset 設計工具**。 如需詳細資訊，請參閱[逐步解說： 在 dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  按兩下您想要驗證之資料表的標題列。 這個動作會建立部分類別檔案<xref:System.Data.DataTable>。  
  
    > [!NOTE]
    >  **Dataset 設計工具**並不會自動建立的事件處理常式<xref:System.Data.DataTable.RowChanging>事件。 您必須建立方法以處理<xref:System.Data.DataTable.RowChanging>事件，並執行程式碼將連結資料表的初始設定方法中的事件。  
  
3.  將下列程式碼複製到部分的類別：  
  
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
  
## <a name="to-retrieve-changed-rows"></a>若要擷取變更的資料列  
資料表中的每個資料列都有<xref:System.Data.DataRow.RowState%2A>屬性，可追蹤該資料列的目前狀態的使用中的值<xref:System.Data.DataRowState>列舉型別。 您可以從資料集或資料的資料表傳回變更的資料列，藉由呼叫`GetChanges`方法<xref:System.Data.DataSet>或<xref:System.Data.DataTable>。 您可以確認變更存在然後才呼叫`GetChanges`藉由呼叫<xref:System.Data.DataSet.HasChanges%2A>資料集的方法。 
  
> [!NOTE]
>  您在認可至資料集或資料表的變更後 (透過呼叫<xref:System.Data.DataSet.AcceptChanges%2A>方法)，則`GetChanges`方法會傳回任何資料。 如果您的應用程式必須處理變更的資料列，您必須處理的變更，然後再呼叫`AcceptChanges`方法。  
  
呼叫<xref:System.Data.DataSet.GetChanges%2A>的資料集或資料表的方法會傳回新的資料集或資料表包含只記錄已變更。 如果您想要取得特定的資料錄 — 例如，新的記錄或已修改的記錄，您可以從值傳遞<xref:System.Data.DataRowState>列舉型別為參數，以`GetChanges`方法。  
  
使用<xref:System.Data.DataRowVersion>存取 （例如，原始值已處理它之前的資料列中） 的資料列的不同版本的列舉。  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>若要取得所有已變更的記錄從資料集  
  
-   呼叫<xref:System.Data.DataSet.GetChanges%2A>資料集的方法。  
  
     下列範例會建立新的資料集，稱為`changedRecords`並填入所有已變更的記錄，從其他資料集稱為`dataSet1`。  
  
     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>若要取得所有已變更的記錄資料表的資料  
  
-   呼叫<xref:System.Data.DataTable.GetChanges%2A>DataTable 的方法。  
  
     下列範例會建立新的資料表呼叫`changedRecordsTable`，並從呼叫的另一個資料表所有已變更的記錄填入`dataTable1`。  
  
     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>若要取得特定資料列狀態的所有記錄  
  
-   呼叫`GetChanges`方法的資料集或資料表和傳遞<xref:System.Data.DataRowState>做為引數的列舉值。  
  
     下列範例示範如何建立新的資料集，稱為`addedRecords`並填入只記錄已加入至的`dataSet1`資料集。  
  
     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]  
  
     下列範例示範如何傳回最近加入的所有記錄`Customers`資料表：  
  
     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>存取資料列的原始版本  
資料集將資料列變更時，會保留這兩個原始 (<xref:System.Data.DataRowVersion.Original>) 和新 (<xref:System.Data.DataRowVersion.Current>) 的資料列版本。 之前呼叫，例如`AcceptChanges`方法，您的應用程式可以存取記錄的不同版本 (如中所定義<xref:System.Data.DataRowVersion>列舉型別) 並據以處理所做的變更。  
  
> [!NOTE]
>  不同版本的資料列存在，只有它已經編輯之後之前它,`AcceptChanges`呼叫方法。 之後`AcceptChanges`呼叫方法，目前和原始版本相同。  
  
傳遞<xref:System.Data.DataRowVersion>值資料行索引 （或做為字串資料行名稱） 以及傳回該資料行的特定資料列版本的值。 已變更的資料行識別期間<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.ColumnChanged>事件。 這是檢查進行驗證的不同的資料列版本的好時機。 不過，如果您已暫時停用條件約束，將不會引發這些事件，而且您必須以程式設計方式識別已變更哪些資料行。 您可以透過逐一<xref:System.Data.DataTable.Columns%2A>集合，並比較不同<xref:System.Data.DataRowVersion>值。  
  
#### <a name="to-get-the-original-version-of-a-record"></a>若要取得之記錄的原始版本  
  
-   藉由傳遞存取的資料行值<xref:System.Data.DataRowVersion>您想要傳回的資料列。  
  
     下列範例示範如何使用<xref:System.Data.DataRowVersion>要取得的原始值值`CompanyName`欄位<xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>存取目前版本的資料列  
  
#### <a name="to-get-the-current-version-of-a-record"></a>若要取得目前版本的記錄  
  
-   存取資料行的值，然後將參數加入至索引，指出您想要傳回的資料列版本。  
  
     下列範例示範如何使用<xref:System.Data.DataRowVersion>要取得的目前值值`CompanyName`欄位<xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]  
  
## <a name="see-also"></a>請參閱
[Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)  
[如何： 驗證 Windows Form DataGridView 控制項中的資料](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)   
[操作說明：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)