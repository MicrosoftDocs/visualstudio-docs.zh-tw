---
title: 將驗證加入至 n-tier 資料集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: addcbd4640acd86cc40097742dcdfd515308f256
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="add-validation-to-an-n-tier-dataset"></a>將驗證加入至 n-tier 資料集
將驗證加入至資料集分成多層式架構方案，基本上是相同的單一檔案的資料集 （單一專案中的資料集） 中加入驗證。 在資料上執行驗證的建議的位置是在<xref:System.Data.DataTable.ColumnChanging>及/或<xref:System.Data.DataTable.RowChanging>事件資料表的資料。  
  
 資料集提供的功能，以建立部分類別，您可以新增使用者程式碼變更資料行和資料列的資料集內資料表的事件。 如需程式碼加入至多層式架構方案中的資料集的詳細資訊，請參閱[將程式碼加入 n-tier 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)，和[多層式架構應用程式中，加入至 Tableadapter 的程式碼](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)。 如需部分類別的詳細資訊，請參閱[How to： 將類別分割成部分類別 （類別設計工具）](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)或[部分類別和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)。  
  
> [!NOTE]
>  當您分隔資料集從 Tableadapter 時 (藉由設定**資料集專案**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有資料集部分類別必須手動移至資料集專案。  
  
> [!NOTE]
>  資料集設計工具不會自動建立事件處理常式的 C# 中<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件。 您必須手動建立事件處理常式，並連結到基礎事件的事件處理常式。 下列程序描述如何在 Visual Basic 和 C# 中建立所需的事件處理常式。  
  
## <a name="validate-changes-to-individual-columns"></a>驗證變更個別資料行  
 驗證個別資料行中的值，藉由處理<xref:System.Data.DataTable.ColumnChanging>事件。 <xref:System.Data.DataTable.ColumnChanging>時修改資料行中的值，便會引發事件。 建立事件處理常式<xref:System.Data.DataTable.ColumnChanging>按兩下所要的資料行上的事件**Dataset 設計工具**。  
  
 您按兩下資料行，第一次在設計工具產生的事件處理常式<xref:System.Data.DataTable.ColumnChanging>事件。 `If...Then`陳述式也會建立測試的特定資料行。 例如，當您按兩下 Northwind Orders 資料表的 RequiredDate 資料行時，就會產生下列程式碼：  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  在 C# 專案中，在 Dataset 設計工具只會建立資料集和資料集內的個別資料表的部分類別。 Dataset 設計工具不會自動建立的事件處理常式<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>C# 中一樣在 Visual Basic 中的事件。 在 C# 專案中，您必須手動建構來處理事件，並連接到基礎事件方法的方法。 下列程序提供在 Visual Basic 和 C# 中建立所需的事件處理常式的步驟。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>若要加入個別資料行值變更期間驗證  
  
1.  按兩下，即可開啟資料集**.xsd**檔案**方案總管 中**。 如需詳細資訊，請參閱[逐步解說： 在 Dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  按兩下您想要驗證的資料行。 這個動作會建立<xref:System.Data.DataTable.ColumnChanging>事件處理常式。  
  
    > [!NOTE]
    >  Dataset 設計工具不會自動建立 C# 事件的事件處理常式。 需要 C# 中處理事件的程式碼隨附於下一節。 `SampleColumnChangingEvent` 建立並繫結多達<xref:System.Data.DataTable.ColumnChanging>中的事件<xref:System.Data.DataTable.EndInit%2A>方法。  
  
3.  加入程式碼可讓您確認`e.ProposedValue`包含符合您的應用程式需求的資料。 如果無法接受建議的值，表示它包含錯誤資料行的設定。  
  
     下列程式碼範例會驗證**數量**資料行包含大於 0 的值。 如果**數量**小於或等於 0，該資料行設錯誤。 `Else`子句會清除錯誤，如果**數量**大於 0。 中的資料行有變更的事件處理常式的程式碼應該如下所示：  
  
    ```vb  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```    
    ```csharp  
    // Add this code to the DataTable partial class.  
  
    public override void EndInit()  
    {  
        base.EndInit();  
        // Hook up the ColumnChanging event  
        // to call the SampleColumnChangingEvent method.  
        ColumnChanging += SampleColumnChangingEvent;  
    }  
  
    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)  
    {  
        if (e.Column.ColumnName == QuantityColumn.ColumnName)  
        {  
            if ((short)e.ProposedValue <= 0)  
            {  
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
            }  
            else  
            {  
                e.Row.SetColumnError("Quantity", "");  
            }  
        }  
    }  
    ```  
  
## <a name="validate-changes-to-whole-rows"></a>驗證整個資料列的變更  
 驗證整個資料列中的值，藉由處理<xref:System.Data.DataTable.RowChanging>事件。 <xref:System.Data.DataTable.RowChanging>認可所有資料行中的值時，就會引發事件。 它是為了在驗證<xref:System.Data.DataTable.RowChanging>事件，當一個資料行中的值依賴另一個資料行中的值。 例如，考慮 OrderDate 和 RequiredDate Northwind 在 Orders 資料表中。  
  
 當輸入訂單時，驗證可確保不會與 在或之前 OrderDate RequiredDate 輸入訂單。 在此範例中，RequiredDate 和 OrderDate 資料行的值需要進行比較，因此驗證變更個別資料行不具意義。  
  
 建立事件處理常式<xref:System.Data.DataTable.RowChanging>按兩下標題列的資料表中的資料表名稱的事件**Dataset 設計工具**。  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>若要加入整個資料列變更期間驗證  
  
1.  按兩下，即可開啟資料集**.xsd**檔案**方案總管 中**。 如需詳細資訊，請參閱[逐步解說： 在 Dataset 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  按兩下標題列的資料表設計工具上。  
  
     部分類別會透過`RowChanging`事件處理常式，並在程式碼編輯器隨即開啟。  
  
    > [!NOTE]
    >  Dataset 設計工具不會自動建立的事件處理常式<xref:System.Data.DataTable.RowChanging>C# 專案中的事件。 您必須建立方法以處理<xref:System.Data.DataTable.RowChanging>事件並執行程式碼，然後將連結資料表的初始設定方法中的事件。  
  
3.  加入部分類別宣告內的使用者程式碼。  
  
4.  下列程式碼將示範如何加入使用者程式碼執行期間驗證<xref:System.Data.DataTable.RowChanging>事件。 C# 範例也會包含最多連結事件處理常式方法的程式碼`OrdersRowChanging`事件。  
  
    ```vb  
    Partial Class OrdersDataTable  
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging  
            ' Add logic to validate columns here.  
            If e.Row.RequiredDate <= e.Row.OrderDate Then  
                ' Set the RowError if validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"  
            Else  
                ' Clear the RowError when validation passes.  
                e.Row.RowError = ""  
            End If  
        End Sub  
    End Class  
    ```  
    ```csharp  
    partial class OrdersDataTable  
    {  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the event to the  
            // RowChangingEvent method.  
            OrdersRowChanging += RowChangingEvent;  
        }  
  
        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)  
        {  
            // Perform the validation logic.  
            if (e.Row.RequiredDate <= e.Row.OrderDate)  
            {  
                // Set the row to an error when validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";  
            }  
            else  
            {  
                // Clear the RowError if validation passes.  
                e.Row.RowError = "";  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)   
 [逐步解說： 建立 N-tier 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)