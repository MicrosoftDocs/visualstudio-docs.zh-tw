---
title: 如何：將驗證新增至實體類別
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 83c6addb7aa6cf0b54398db351bee5825bc2d6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648402"
---
# <a name="how-to-add-validation-to-entity-classes"></a>如何：將驗證新增至實體類別
「驗證」實體類別過程會確認資料物件中，輸入的值是否符合物件結構描述中的條件約束，以及是否也符合為應用程式建立的規則。 先驗證資料再將更新傳送至基礎資料庫是減少錯誤的良好做法。 它同時也會降低應用程式與資料庫之間的可能往返次數。

[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供部分方法，可讓使用者擴充設計工具產生的程式碼，在完成實體的插入、更新和刪除期間，以及個別資料行變更期間和之後執行。

> [!NOTE]
> 本主題提供使用**O/R 設計**工具將驗證加入至實體類別的基本步驟。 因為在不參考特定實體類別的情況下，可能會難以遵循這些一般步驟，所以會提供使用實際資料的逐步解說。

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>為特定資料行中的值新增變更的驗證
這個程序顯示如何在資料行中的值發生變更時驗證資料。 因為驗證是在類別定義 (而不是使用者介面) 內執行，所以如果值無法通過驗證，就會擲回例外狀況。 請在會嘗試變更資料行值的應用程式的程式碼中實作錯誤處理。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>若要在資料行值變更期間驗證資料

1. 在**O/R 設計**工具中開啟或建立新的 LINQ to SQL 類別檔案（ **.dbml**檔案）。 (按兩下 [方案總管] 中的 **.dbml** 檔案。)

2. 在 **O/R 設計工具**中，以滑鼠右鍵按一下要新增驗證的類別，然後按一下 [檢視程式碼]。

     [程式碼編輯器] 會以所選取實體類別的部分類別開啟。

3. 將游標放在部分類別中。

4. 如果是 Visual Basic 專案：

    1. 展開 [方法名稱] 清單。

    2. 尋找要新增驗證到其中之資料行所適用的 **OnCOLUMNNAMEChanging** 方法。

    3. 將 `OnCOLUMNNAMEChanging` 方法新增至部分類別中。

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

    因為C#專案不會自動產生事件處理常式，所以您可以使用 IntelliSense 來建立資料行變更的部分方法。 輸入 `partial` 和一個空格，以存取可用部分方法的清單。 針對要加入驗證的資料行按一下在資料行變更時執行的方法。 下列程式碼類似于您選取資料行變更的部分方法時所產生的程式碼：

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>將更新的驗證加入至實體類別
除了可以檢查變更期間的值以外，您還可以在發生整個實體類別的更新時驗證資料。 更新期間執行的驗證可以應商務規則 (Business Rule) 的需要，比較多個資料行的值。 下列程序顯示如何在發生整個實體類別的更新時進行驗證。

> [!NOTE]
> 整個實體類別的更新驗證程式碼是在部分 <xref:System.Data.Linq.DataContext> 類別 (而不是在特定實體類別的部分類別) 中執行。

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>若要在實體類別更新期間驗證資料

1. 在**O/R 設計**工具中開啟或建立新的 LINQ to SQL 類別檔案（ **.dbml**檔案）。 (按兩下 [方案總管] 中的 **.dbml** 檔案。)

2. 以滑鼠右鍵按一下 [O/R 設計工具] 中的空白區域，然後按一下 [檢視程式碼]。

     會以 `DataContext` 的部分類別開啟 [程式碼編輯器]。

3. 將游標放在 `DataContext` 的部分類別中。

4. 如果是 Visual Basic 專案：

    1. 展開 [方法名稱] 清單。

    2. 按一下 [UpdateENTITYCLASSNAME]。

    3. 將 `UpdateENTITYCLASSNAME` 方法新增至部分類別中。

    4. 使用 `instance` 引數存取個別資料行值，如下列程式碼所示：

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    C# 專案：

    因為C#專案不會自動產生事件處理常式，所以您可以使用 IntelliSense 來建立部分 `UpdateCLASSNAME` 方法。 輸入 `partial` 和一個空格，以存取可用部分方法的清單。 針對您要在其上加入驗證的類別，按一下更新方法。 下列程式碼類似于您選取 `UpdateCLASSNAME` 部分方法時所產生的程式碼：

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

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [驗證資料](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL （.NET Framework）](/dotnet/framework/data/adonet/sql/linq/index)