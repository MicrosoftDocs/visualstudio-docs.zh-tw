---
title: 將驗證新增至多層式架構資料集 |Microsoft Docs
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
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 773af4469f8d72acb6768e62cd2091c396d36b45
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439546"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>將驗證新增至多層式架構 (N-Tier) 資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將驗證新增至資料集分割為多層式架構方案基本上是將驗證新增至單一檔案的資料集 （必須在單一專案中的資料集） 相同。 在資料上執行驗證的建議的位置是期間<xref:System.Data.DataTable.ColumnChanging>及/或<xref:System.Data.DataTable.RowChanging>事件資料表的資料。  
  
DataSet 設計工具提供的功能，以建立部分類別，您可以新增資料行和資料列-使用者程式碼變更的資料集內的資料表事件。 如需有關如何將程式碼新增至多層式架構方案中的資料集的詳細資訊，請參閱[程式碼加入 n-tier 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)，並[程式碼加入多層式架構應用程式中的 Tableadapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)。 如需部分類別的詳細資訊，請參閱[How to:將類別分割成部分類別 （類別設計工具）](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)或是[部分類別和方法](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)。  
  
> [!NOTE]
> 當您分隔資料集與 Tableadapter 時 (藉由設定**資料集 Project**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有的資料集部分的類別必須手動將移至資料集專案。  
  
> [!NOTE]
> Dataset 設計工具不會自動建立事件處理常式中的 C#<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件。 您必須手動建立事件處理常式，並連結事件處理常式，基礎事件。 下列程序說明如何在 Visual Basic 和 C# 中建立所需的事件處理常式。  
  
## <a name="validatechanges-to-individual-columns"></a>Validatechanges 至個別資料行  
 驗證個別資料行中的值，藉由處理<xref:System.Data.DataTable.ColumnChanging>事件。 <xref:System.Data.DataTable.ColumnChanging>修改資料行的值時，會引發事件。 建立事件處理常式<xref:System.Data.DataTable.ColumnChanging>按兩下所要的資料行的資料集上的事件。  
  
 按兩下 資料行，第一次，設計師會產生的事件處理常式<xref:System.Data.DataTable.ColumnChanging>事件。 `If…Then`陳述式也會建立測試特定資料行。 例如，當您按兩下 Northwind 訂單資料表上的 RequiredDate 資料行時，就會產生下列程式碼：  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
> 在 C# 專案中，Dataset 設計工具只會建立資料集和資料集內的個別資料表的部分類別。 Dataset 設計工具不會自動建立的事件處理常式<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件在 C# 在 Visual Basic 中所顯示的一樣。 在 C# 專案中，您必須以手動方式建構來處理事件，並將方法連結至基礎事件的方法。 下列程序提供在 Visual Basic 和 C# 中建立所需的事件處理常式的步驟。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>若要在變更期間驗證加入個別的資料行值  
  
1. 開啟資料集設計工具中，按兩下 **.xsd**中的檔案**方案總管 中**。 如需詳細資訊，請參閱[如何：在 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2. 按兩下您想要驗證的資料行。 這個動作會建立<xref:System.Data.DataTable.ColumnChanging>事件處理常式。  
  
    > [!NOTE]
    > Dataset 設計工具不會自動建立 C# 事件的事件處理常式。 C# 中處理事件所需的程式碼會包含在下一節。 `SampleColumnChangingEvent` 建立並繫結最多<xref:System.Data.DataTable.ColumnChanging>中的事件<xref:System.Data.DataTable.EndInit%2A>方法。  
  
3. 加入程式碼來確認`e.ProposedValue`包含符合您的應用程式的資料。 如果無法接受建議的值，表示它包含錯誤資料行的設定。  
  
     下列程式碼範例會驗證**Quantity**資料行包含大於 0。 如果**Quantity**小於或等於 0，資料行會設定為錯誤。 `Else`子句會清除錯誤，如果**Quantity**大於 0。 中的資料行變更的事件處理常式的程式碼應該如下所示：  
  
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
    // C#  
    // Add this code to the DataTable   
    // partial class.  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Validatechanges 整個資料列  
 驗證在整個資料列中的值，藉由處理<xref:System.Data.DataTable.RowChanging>事件。 <xref:System.Data.DataTable.RowChanging>認可中的所有資料行的值時，會引發事件。 就必須在驗證<xref:System.Data.DataTable.RowChanging>事件時的一個資料行中的值相依於另一個資料行中的值。 例如，請考慮 OrderDate 和 RequiredDate Northwind 在 Orders 資料表中。  
  
 當輸入訂單時，驗證確定訂單與訂單日期早於或 RequiredDate 不輸入。 在此範例中，RequiredDate 和 OrderDate 資料行的值需要進行比較，以便驗證個別的資料行的變更不會毫無意義。  
  
 建立事件處理常式<xref:System.Data.DataTable.RowChanging>按兩下標題列的資料表中的資料表名稱的事件。  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>將變更期間驗證新增至整個資料列  
  
1. 開啟資料集設計工具中，按兩下 **.xsd**中的檔案**方案總管 中**。 如需詳細資訊，請參閱[如何：在 Dataset 設計工具中開啟資料集](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)。  
  
2. 按兩下標題列的資料表設計工具上。  
  
     部分類別會透過`RowChanging`事件處理常式，並在程式碼編輯器中開啟。  
  
    > [!NOTE]
    > Dataset 設計工具不會自動建立的事件處理常式<xref:System.Data.DataTable.RowChanging>C# 專案中的事件。 您必須建立方法以處理<xref:System.Data.DataTable.RowChanging>事件和執行程式碼，來連結資料表的初始設定方法中的事件。  
  
3. 加入部分類別宣告內的使用者程式碼。  
  
4. 下列程式碼示範如何加入使用者程式碼，以驗證期間<xref:System.Data.DataTable.RowChanging>Visual basic 中的事件：  
  
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
  
5. 下列程式碼示範如何建立`RowChanging`事件處理常式及如何加入使用者程式碼，以驗證期間<xref:System.Data.DataTable.RowChanging>適用於 C# 的事件：  
  
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
 [逐步解說：建立多層式架構資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)
