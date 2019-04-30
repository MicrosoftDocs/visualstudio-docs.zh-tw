---
title: HOW TO：將驗證新增至實體類別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5381c33790cbe9a7b5083f29d2602af39387bf61
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386750"
---
# <a name="how-to-add-validation-to-entity-classes"></a>HOW TO：將驗證新增至實體類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「驗證」實體類別過程會確認資料物件中，輸入的值是否符合物件結構描述中的條件約束，以及是否也符合為應用程式建立的規則。 先驗證資料再將更新傳送至基礎資料庫是減少錯誤的良好做法。 它同時也會降低應用程式與資料庫之間的可能往返次數。  
  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供可讓使用者將擴充的設計工具所產生的程式碼，執行插入、 更新和刪除完整實體，以及個別的資料行後面的部分方法變更。  
  
> [!NOTE]
> 本主題提供使用 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]將驗證加入至實體類別時的基本步驟。 因為它可能難以遵循這些泛型步驟，而不會參考特定實體類別，提供逐步解說中使用實際的資料。  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>加入在特定資料行中的值變更時的驗證  
 這個程序顯示如何在資料行中的值發生變更時驗證資料。 因為驗證是在實際類別定義 (而不是使用者介面) 內執行，所以如果值無法通過驗證，就會擲回例外狀況 (Exception)。 請在會嘗試變更資料行值的應用程式的程式碼中實作錯誤處理。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>若要在資料行值變更期間驗證資料  
  
1. 開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。 (按兩下 [方案總管] 中的 **.dbml** 檔案。)  
  
2. 在 O/R 設計工具中，以滑鼠右鍵按一下您要新增驗證，然後按一下的類別**檢視程式碼**。  
  
    [程式碼編輯器] 會以所選取實體類別的部分類別開啟。  
  
3. 將游標放在部分類別中。  
  
4. 如果是 Visual Basic 專案：  
  
   1. 展開 [方法名稱] 清單。  
  
   2. 找出**上**_COLUMNNAME_**變更**您想要加入驗證的資料行的方法。  
  
   3. `On` *COLUMNNAME* `Changing`方法會加入至部分類別。  
  
   4. 加入下列程式碼以先確認已輸入值，然後確定應用程式可接受輸入的資料行值。 `value` 引數包含建議值，因此請加入邏輯以確認它是有效值：  
  
      ```vb  
      If value.HasValue Then  
          ' Add code to ensure that the value is acceptable.  
          ' If value < 1 Then  
          '    Throw New Exception("Invalid data!")  
          ' End If  
      End If  
      ```  
  
      C# 專案：  
  
   5. 因為 C# 專案不會自動產生事件處理常式，所以您可以使用 IntelliSense 建立在資料行變更時執行的部分方法。  
  
       輸入 `partial` 和一個空格，以存取可用部分方法的清單。 針對要加入驗證的資料行按一下在資料行變更時執行的方法。 下列程式碼與選取在資料行變更時執行的部分方法時所產生的程式碼類似：  
  
      ```csharp  
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
          {  
             throw new System.NotImplementedException();  
          }  
  
      ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>加入更新實體類別時執行的驗證  
 除了可以檢查變更期間的值以外，您還可以在發生整個實體類別的更新時驗證資料。 更新期間執行的驗證可以應商務規則 (Business Rule) 的需要，比較多個資料行的值。 下列程序顯示如何在發生整個實體類別的更新時進行驗證。  
  
> [!NOTE]
> 整個實體類別的更新驗證程式碼是在部分 <xref:System.Data.Linq.DataContext> 類別 (而不是在特定實體類別的部分類別) 中執行。  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>若要在實體類別更新期間驗證資料  
  
1. 開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。 (按兩下 [方案總管] 中的 **.dbml** 檔案。)  
  
2. 以滑鼠右鍵按一下 O/R 設計工具上的空白區域，然後按一下 **檢視程式碼**。  
  
    會以 `DataContext` 的部分類別開啟 [程式碼編輯器]。  
  
3. 將游標放在 `DataContext` 的部分類別中。  
  
4. 如果是 Visual Basic 專案：  
  
   1. 展開 [方法名稱] 清單。  
  
   2. 按一下 **更新**_ENTITYCLASSNAME_。  
  
   3. `Update` *ENTITYCLASSNAME*方法會加入至部分類別。  
  
   4. 使用 `instance` 引數存取個別資料行值，如下列程式碼所示：  
  
      ```vb  
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
          Dim ErrorMessage As String = "Invalid data!"  
          Throw New Exception(ErrorMessage)  
      End If  
      ```  
  
      C# 專案：  
  
   5. 因為 C# 專案不會自動產生的事件處理常式，您可以使用 IntelliSense 建立部分`Update` *CLASSNAME*方法。  
  
   6. 輸入 `partial` 和一個空格，以存取可用部分方法的清單。 按一下要加入驗證的類別所適用的更新方法。 當您選取 產生程式碼的下列程式碼類似`Update` *CLASSNAME*部分方法：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) \(機器翻譯\)
