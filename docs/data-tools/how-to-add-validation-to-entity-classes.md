---
title: "如何： 為實體類別加入驗證 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 7110fed065816c6d6843e9ed6f95d2da2d6f4851
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-add-validation-to-entity-classes"></a>如何： 為實體類別加入驗證
*驗證*實體類別會確認程序的輸入資料物件的值符合的條件約束物件的結構描述，以及建立應用程式的規則。 先驗證資料再將更新傳送至基礎資料庫是減少錯誤的良好做法。 它同時也會降低應用程式與資料庫之間的可能往返次數。  
  
 [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供部分的方法，讓使用者以擴充的設計工具產生的程式碼執行期間插入、 更新和刪除的完整實體，以及期間和之後個別資料行變更。  
  
> [!NOTE]
>  本主題提供使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]將驗證加入至實體類別時的基本步驟。 因為可能難以在不參考特定實體類別的情況下遵循這些泛型步驟，使用實際資料的逐步解說提供了的。  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>加入在特定資料行中的值變更時的驗證  
 這個程序顯示如何在資料行中的值發生變更時驗證資料。 因為驗證是在實際類別定義 (而不是使用者介面) 內執行，所以如果值無法通過驗證，就會擲回例外狀況 (Exception)。 請在會嘗試變更資料行值的應用程式的程式碼中實作錯誤處理。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>若要在資料行值變更期間驗證資料  
  
1.  開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (按兩下**.dbml**檔案**方案總管 中**。)  
  
2.  在 O/R 設計工具中，以滑鼠右鍵按一下您要加入驗證，然後按一下 的類別**檢視程式碼**。  
  
     [程式碼編輯器] 會以所選取實體類別的部分類別開啟。  
  
3.  將游標放在部分類別中。  
  
4.  如果是 Visual Basic 專案：  
  
    1.  展開**方法名稱**清單。  
  
    2.  找出**OnCOLUMNNAMEChanging**您想要加入驗證的資料行的方法。  
  
    3.  `OnCOLUMNNAMEChanging`方法會加入至部分類別。  
  
    4.  加入下列程式碼以先確認已輸入值，然後確定應用程式可接受輸入的資料行值。 `value` 引數包含建議值，因此請加入邏輯以確認它是有效值：  
  
        ```vb  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
    C# 專案：  
  
    因為 C# 專案不會自動產生事件處理常式，您可以使用 IntelliSense 建立的資料行有變更的部分方法。 輸入 `partial` 和一個空格，以存取可用部分方法的清單。 針對要加入驗證的資料行按一下在資料行變更時執行的方法。 下列程式碼類似於您選取資料行有變更的部分方法時，會產生的程式碼：  
  
    ```csharp  
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
        {  
           throw new System.NotImplementedException();  
        }  
    ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>加入更新實體類別時執行的驗證  
 除了可以檢查變更期間的值以外，您還可以在發生整個實體類別的更新時驗證資料。 更新期間執行的驗證可以應商務規則 (Business Rule) 的需要，比較多個資料行的值。 下列程序顯示如何在發生整個實體類別的更新時進行驗證。  
  
> [!NOTE]
>  整個實體類別的更新驗證程式碼是在部分 <xref:System.Data.Linq.DataContext> 類別 (而不是在特定實體類別的部分類別) 中執行。  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>若要在實體類別更新期間驗證資料  
  
1.  開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (按兩下**.dbml**檔案**方案總管 中**。)  
  
2.  以滑鼠右鍵按一下 O/R 設計工具上的空白區域，然後按一下**檢視程式碼**。  
  
     會以 `DataContext` 的部分類別開啟 [程式碼編輯器]。  
  
3.  將游標放在 `DataContext` 的部分類別中。  
  
4.  如果是 Visual Basic 專案：  
  
    1.  展開**方法名稱**清單。  
  
    2.  按一下**UpdateENTITYCLASSNAME**。  
  
    3.  `UpdateENTITYCLASSNAME`方法會加入至部分類別。  
  
    4.  使用 `instance` 引數存取個別資料行值，如下列程式碼所示：  
  
        ```vb  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
    C# 專案：  
  
    因為 C# 專案不會自動產生事件處理常式，您可以使用 IntelliSense 建立部分`UpdateCLASSNAME`方法。 輸入 `partial` 和一個空格，以存取可用部分方法的清單。 按一下要加入驗證的類別所適用的更新方法。 下列程式碼類似的程式碼，當您選取時，會產生`UpdateCLASSNAME`部分方法：  
  
    ```csharp  
    partial void UpdateCLASSNAME(CLASSNAME instance)  
    {  
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
        {  
            string ErrorMessage = "Invalid data!";  
            throw new System.Exception(ErrorMessage);  
        }  
    }  
    ```  
  
## <a name="see-also"></a>請參閱
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[驗證資料](../data-tools/validate-data-in-datasets.md)  
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)  