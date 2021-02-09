---
title: 針對程式碼瑕疵分析 Managed 程式碼的逐步解說 |Microsoft Docs
ms.date: 01/29/2018
description: 瞭解如何使用舊版程式碼分析來分析 .NET managed 程式碼元件。 瞭解如何使用 .NET 設計指導方針檢查瑕疵和是否符合規範。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b9895dc8926f1bb5c7d33e792168ca46297c8196
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859602"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>逐步解說：使用靜態程式碼分析來尋找程式碼瑕疵

在這個逐步解說中，您將使用舊版程式碼分析來分析 managed 專案的程式碼缺失。

本文將逐步引導您完成使用舊版分析來分析 .NET managed 程式碼元件，以符合 .NET 設計指導方針的流程。

## <a name="create-a-class-library"></a>建立類別庫

1. 開啟 Visual Studio，並從 [ **類別庫] ( .NET Framework)** 範本建立新專案。

1. 將專案命名為 **CodeAnalysisManagedDemo**。

1. 建立專案之後，請開啟 *Class1.cs* 檔案。

1. 以下列程式碼取代 Class1.cs 中的現有文字：

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

## <a name="analyze-the-project-for-code-defects"></a>分析專案中的程式碼瑕疵

1. 在 **方案總管** 中選取 [CodeAnalysisManagedDemo] 專案。

2. 按一下 [專案]  功能表上的 [屬性]  。

   [CodeAnalysisManagedDemo 屬性] 頁面隨即顯示。

3. 選擇 [程式 **代碼分析** ] 索引標籤。

::: moniker range="vs-2017"

4. 確定已選取 [ **啟用組建的程式碼分析** ]。

5. 從 [ **執行此規則集** ] 下拉式清單中，選取 [ **Microsoft 所有規則**]。

::: moniker-end

::: moniker range=">=vs-2019"

4. 請確定已在 [**二進位分析器**] 區段中選取 [**在組建上執行**]。

5. 從 [作用中 **規則** ] 下拉式清單中，選取 [ **Microsoft 所有規則**]。

::: moniker-end

6. **在 [檔案**] 功能表上，按一下 [**儲存選取專案**]，然後關閉 [屬性] 頁面。

7. 在 [ **組建** ] 功能表上，按一下 [ **組建 CodeAnalysisManagedDemo**]。

    CodeAnalysisManagedDemo 專案組建警告會顯示在 [ **錯誤清單** ] 和 [ **輸出** ] 視窗中。

## <a name="correct-the-code-analysis-issues"></a>更正程式碼分析問題

1. 在 [ **View** ] 功能表上，選擇 [ **錯誤清單**]。

    根據您選擇的開發人員設定檔，您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**]，然後選擇 [**錯誤清單**]。

1. 在 [方案總管] 中選擇 [顯示所有檔案]。

1. 展開 [屬性] 節點，然後開啟 *AssemblyInfo.cs* 檔案。

1. 使用下列秘訣來修正警告：

   [CA1014：使用 >clscompliantattribute 標記元件](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)：將程式碼新增 `[assembly: CLSCompliant(true)]` 至 AssemblyInfo.cs 檔案的結尾。

   [Ca1032 必須：實行標準例外](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)狀況的函式：將此函式加入 `public demo (String s) : base(s) { }` 至類別 `demo` 。

   [Ca1032 必須：實行標準例外](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)狀況的函式：將此函式加入 `public demo (String s, Exception e) : base(s, e) { }` 至類別 `demo` 。

   [Ca1032 必須：實行標準例外](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)狀況的函式：將此函式新增 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` 至類別示範。 您也需要新增的 `using` 語句 <xref:System.Runtime.Serialization?displayProperty=fullName> 。

   [Ca1032 必須：實行標準例外](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)狀況的函式：將此函式加入 `public demo () : base() { }` 至類別 `demo` 。

   [CA1709：識別碼的大小寫應該正確](../code-quality/ca1709.md)：將命名空間的大小寫變更 `testCode` 為 `TestCode` 。

   [CA1709：識別碼的大小寫應該正確：請](../code-quality/ca1709.md)將成員的名稱變更為 `Demo` 。

   [CA1709：識別碼的大小寫應該正確：請](../code-quality/ca1709.md)將成員的名稱變更為 `Item` 。

   [CA1710：識別碼應該有正確的後](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)置詞：將類別的名稱及其函式變更為 `DemoException` 。

   [Ca2237 必須：使用 SerializableAttribute 標記 ISerializable 類型](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)：將 `[Serializable ()]` 屬性加入至類別 `demo` 。

   [CA2210：元件應該具有有效的強式名稱](../code-quality/ca2210.md)：使用強式名稱金鑰簽署 ' CodeAnalysisManagedDemo '：

   1. 在 [ **專案** ] 功能表上，選擇 [ **CodeAnalysisManagedDemo 屬性**]。

      專案屬性隨即出現。

   1. 選擇 [ **簽署** ] 索引標籤。

   1. 選取 [ **簽署元件** ] 核取方塊。

   1. 在 [ **選擇字串名稱金鑰** 檔] 清單中，選取 **\<New>** 。

      [建立強式名稱金鑰] 對話方塊隨即出現。

   1. 針對 [ **金鑰檔名稱**]，輸入 **y**。

   1. 輸入密碼，然後選擇 **[確定]**。

   1. 在 [檔案 **] 功能表上，選擇 [** **儲存選取專案**]，然後關閉屬性頁。

   當您完成所有變更之後，Class1.cs 檔案看起來應該如下所示：

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

1. 請重建專案。

## <a name="exclude-code-analysis-warnings"></a>排除程式碼分析警告

1. 針對每個剩餘的警告，請執行下列動作：

    1. 選取 [ **錯誤清單**] 中的警告。

    1. 從滑鼠右鍵功能表 (操作功能表) 中，選擇 [**隱藏**  >  **在隱藏** 專案檔中]。

1. 請重建專案。

     專案建立時不會出現任何警告或錯誤。

## <a name="see-also"></a>另請參閱

[受控碼的程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)
