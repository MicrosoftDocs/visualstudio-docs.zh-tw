---
title: 將驗證新增至多層式架構 (N-Tier) 資料集
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 91dbe04c85491a38a221edfb064702085136780f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283017"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>將驗證新增至多層式架構 (N-Tier) 資料集
將驗證加入至分成多層式方案的資料集基本上與將驗證加入至單一檔案資料集（單一專案中的資料集）的方式相同。 針對資料執行驗證的建議位置是在資料表的 <xref:System.Data.DataTable.ColumnChanging> 和/或 <xref:System.Data.DataTable.RowChanging> 事件期間。

資料集提供的功能可建立部分類別，您可以將使用者程式碼加入資料集內資料表的資料行和資料列變更事件中。 如需如何將程式碼加入至多層式方案中資料集的詳細資訊，請參閱[將程式碼新增至多層式架構應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)，並[將程式碼新增至多層式應用程式](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)中的 tableadapter。 如需部分類別的詳細資訊，請參閱[如何：將類別分割成部分類別（類別設計工具）](../ide/class-designer/how-to-split-a-class-into-partial-classes.md)或[部分類別和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)。

> [!NOTE]
> 當您從 Tableadapter 區隔資料集（藉由設定 [**資料集專案**] 屬性）時，不會自動移動專案中的現有部分資料集類別。 現有的部分資料集類別必須手動移至 dataset 專案。

> [!NOTE]
> Dataset 設計工具不會自動為和事件建立 c # 中的事件處理常式 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 。 您必須手動建立事件處理常式，並將事件處理常式連結至基礎事件。 下列程式描述如何在 Visual Basic 和 c # 中建立必要的事件處理常式。

## <a name="validate-changes-to-individual-columns"></a>驗證個別資料行的變更
藉由處理事件來驗證個別資料行中的值 <xref:System.Data.DataTable.ColumnChanging> 。 <xref:System.Data.DataTable.ColumnChanging>修改資料行中的值時，就會引發事件。 <xref:System.Data.DataTable.ColumnChanging>按兩下 [ **DataSet 設計工具**上所需的資料行，建立事件的事件處理常式。

當您第一次按兩下資料行時，設計工具會產生事件的事件處理常式 <xref:System.Data.DataTable.ColumnChanging> 。 `If...Then`也會建立一個語句，以測試特定的資料行。 例如，當您按兩下 Northwind Orders 資料表上**的 [規定**] 資料行時，就會產生下列程式碼：

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> 在 c # 專案中，DataSet 設計工具只會針對資料集內的資料集和個別資料表建立部分類別。 DataSet 設計工具不會 <xref:System.Data.DataTable.ColumnChanging> 在 c # 中自動建立和事件的事件處理常式， <xref:System.Data.DataTable.RowChanging> 就像在 Visual Basic 中一樣。 在 c # 專案中，您必須手動建立方法來處理事件，並將方法連結至基礎事件。 下列程式提供在 Visual Basic 和 c # 中建立必要事件處理常式的步驟。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>若要在變更個別資料行值期間加入驗證

1. 按兩下**方案總管**中的 *.xsd*檔案以開啟資料集。 如需詳細資訊，請參閱[逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 按兩下您想要驗證的資料行。 此動作會建立 <xref:System.Data.DataTable.ColumnChanging> 事件處理常式。

    > [!NOTE]
    > DataSet 設計工具不會自動建立 c # 事件的事件處理常式。 下一節包含處理 c # 中的事件所需的程式碼。 `SampleColumnChangingEvent`隨即建立，然後連結至 <xref:System.Data.DataTable.ColumnChanging> 方法中的事件 <xref:System.Data.DataTable.EndInit%2A> 。

3. 加入程式碼，以確認 `e.ProposedValue` 包含符合應用程式需求的資料。 如果建議的值無法接受，請將資料行設定為指出它包含錯誤。

     下列程式碼範例會驗證**Quantity**資料行是否包含大於0的值。 如果**Quantity**小於或等於0，則會將資料行設定為錯誤。 `Else`如果**Quantity**大於0，子句會清除錯誤。 資料行變更事件處理常式中的程式碼應如下所示：

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
藉由處理事件來驗證整個資料列中的值 <xref:System.Data.DataTable.RowChanging> 。 <xref:System.Data.DataTable.RowChanging>當所有資料行中的值都已認可時，就會引發事件。 <xref:System.Data.DataTable.RowChanging>當某個資料行中的值依賴另一個資料行中的值時，必須在事件中進行驗證。 例如，請考慮 Northwind 中 Orders 資料表的「訂購日期」和「日期」。

輸入訂單時，驗證可確保不會在訂購日期之前或之前輸入訂單。 在此範例中，必須比較「符合規定」和「訂購日期」資料行的值，因此驗證個別資料行變更並沒有意義。

在 <xref:System.Data.DataTable.RowChanging> **DataSet 設計工具**上，按兩下資料表標題列中的資料表名稱，建立事件的事件處理常式。

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>若要在整個資料列變更期間加入驗證

1. 按兩下**方案總管**中的 *.xsd*檔案以開啟資料集。 如需詳細資訊，請參閱[逐步解說：在 DataSet 設計工具中建立資料集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。

2. 在設計工具上，按兩下資料表的標題列。

     部分類別是使用 `RowChanging` 事件處理常式所建立，並在程式碼編輯器中開啟。

    > [!NOTE]
    > DataSet 設計工具不會自動為 <xref:System.Data.DataTable.RowChanging> c # 專案中的事件建立事件處理常式。 您必須建立方法來處理 <xref:System.Data.DataTable.RowChanging> 事件，然後執行程式碼，然後在資料表的初始化方法中連結事件。

3. 在部分類別宣告內加入使用者程式碼。

4. 下列程式碼示範在何處加入使用者程式碼，以在事件期間進行驗證 <xref:System.Data.DataTable.RowChanging> 。 C # 範例也包含用來將事件處理常式方法與事件掛鉤的程式碼 `OrdersRowChanging` 。

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

- [多層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說：建立多層式資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)
