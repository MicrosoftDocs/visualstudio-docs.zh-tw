---
title: 針對程式碼缺失分析受控碼的逐步解說 |Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab1e0b890d6241742770ed38ff61fc1c2c0ed2f4
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535699"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>逐步解說：使用靜態程式碼分析來尋找程式碼缺失

在此逐步解說中，您將使用舊版程式碼分析，分析 managed 專案中的程式碼缺失。

本文會逐步引導您使用舊版分析來分析您的 .NET managed 程式碼元件，以符合 .NET 設計方針。

## <a name="create-a-class-library"></a>建立類別庫

1. 開啟 Visual Studio，然後從 [**類別庫] （.NET Framework）** 範本建立新的專案。

1. 將專案命名為**CodeAnalysisManagedDemo**。

1. 建立專案之後，請開啟*Class1.cs*檔案。

1. 將 Class1.cs 中的現有文字取代為下列程式碼：

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. 儲存 Class1.cs 檔案。

## <a name="analyze-the-project-for-code-defects"></a>分析專案中的程式碼缺失

1. 在**方案總管**中選取 [CodeAnalysisManagedDemo] 專案。

2. 在 [專案] 功能表上，按一下 [屬性]。

   [CodeAnalysisManagedDemo 屬性] 頁面隨即顯示。

3. 選擇 [程式**代碼分析**] 索引標籤。

::: moniker range="vs-2017"

4. 請確定已選取 [**在組建上啟用程式碼分析**]。

5. 從 [**執行此規則集**] 下拉式清單中，選取 [ **Microsoft 所有規則**]。

::: moniker-end

::: moniker range=">=vs-2019"

4. 請確定已在 [**二進位分析器**] 區段中選取 [**在組建上執行**]。

5. 從 [作用中**規則**] 下拉式清單中，選取 [ **Microsoft 所有規則**]。

::: moniker-end

6. **在 [檔案**] 功能表上，按一下 [**儲存選取的專案**]，然後關閉 [屬性] 頁面。

7. 在 [**建立**] 功能表上，按一下 [**建立 CodeAnalysisManagedDemo**]。

    [**錯誤清單**] 和 [**輸出**] 視窗中會顯示 CodeAnalysisManagedDemo 專案組建警告。

## <a name="correct-the-code-analysis-issues"></a>更正程式碼分析問題

1. 在 [ **View** ] 功能表上，選擇 [**錯誤清單**]。

    視您選擇的開發人員設定檔而定，您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**]，然後選擇 [**錯誤清單**]。

1. 在 [方案總管] 中選擇 [顯示所有檔案]。

1. 展開 [屬性] 節點，然後開啟*AssemblyInfo.cs*檔案。

1. 使用下列秘訣來更正警告：

   [CA1014：使用 CLSCompliantAttribute 標記元件](../code-quality/ca1014.md)：將程式碼 `[assembly: CLSCompliant(true)]` 新增至 AssemblyInfo.cs 檔案的結尾。

   [Ca1032 必須：實作為標準例外](../code-quality/ca1032.md)狀況的函式：將 `public demo (String s) : base(s) { }` 的函數新增至類別 `demo`。

   [Ca1032 必須：實作為標準例外](../code-quality/ca1032.md)狀況的函式：將 `public demo (String s, Exception e) : base(s, e) { }` 的函數新增至類別 `demo`。

   [Ca1032 必須：執行標準例外](../code-quality/ca1032.md)狀況的函式：將 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` 的函數新增至類別示範。 您也需要為 <xref:System.Runtime.Serialization?displayProperty=fullName> 新增 `using` 語句。

   [Ca1032 必須：實作為標準例外](../code-quality/ca1032.md)狀況的函式：將 `public demo () : base() { }` 的函數新增至類別 `demo`。

   [CA1709：識別碼的大小寫應正確](../code-quality/ca1709.md)：將命名空間的大小寫 `testCode` 變更為 `TestCode`。

   [CA1709：識別碼的大小寫應正確](../code-quality/ca1709.md)：將成員的名稱變更為 `Demo`。

   [CA1709：識別碼的大小寫應正確](../code-quality/ca1709.md)：將成員的名稱變更為 `Item`。

   [CA1710：識別碼應具有正確的後](../code-quality/ca1710.md)置詞：將類別的名稱和其函式變更為 `DemoException`。

   [Ca2237 必須：將 ISerializable 類型標記為 SerializableAttribute](../code-quality/ca2237.md)：將 `[Serializable ()]` 屬性新增至類別 `demo`。

   [CA2210：元件應具有有效的強式名稱](../code-quality/ca2210.md)：使用強式名稱金鑰簽署 ' CodeAnalysisManagedDemo '：

   1. 在 [**專案**] 功能表上，選擇 [ **CodeAnalysisManagedDemo 屬性**]。

      專案屬性隨即出現。

   1. 選擇 [ **簽署** ] 索引標籤。

   1. 選取 [**簽署元件**] 核取方塊。

   1. 在 [**選擇字串名稱金鑰**檔] 清單中，選取 [ **\<New >** ]。

      [**建立強式名稱金鑰**] 對話方塊隨即出現。

   1. 針對 [**金鑰檔名稱**]，輸入**y**。

   1. 輸入密碼，然後選擇 **[確定]** 。

   1. 在 [檔案 **] 功能表上，選擇 [** **儲存選取的專案**]，然後關閉屬性頁。

   完成所有變更之後，Class1.cs 檔案看起來應該如下所示：

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. 重建專案。

## <a name="exclude-code-analysis-warnings"></a>排除程式碼分析警告

1. 針對每個剩餘的警告，執行下列動作：

    1. 在 **錯誤清單**中選取警告。

    1. 從右鍵功能表（操作功能表），選擇 [**隱藏** **隱藏專案中**的  > ]。

1. 重建專案。

     專案建立時不會出現任何警告或錯誤。

## <a name="see-also"></a>請參閱

[受控碼的程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)
