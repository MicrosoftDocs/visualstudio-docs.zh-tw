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
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548006"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>逐步解說：使用靜態程式碼分析來尋找程式碼缺失

在此逐步解說中, 您將使用舊版程式碼分析, 分析 managed 專案中的程式碼缺失。

本文會逐步引導您使用舊版分析來分析您的 .NET managed 程式碼元件, 以符合 .NET 設計方針。

## <a name="create-a-class-library"></a>建立類別庫

### <a name="to-create-a-class-library"></a>若要建立類別庫

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。

1. 在 [**新增專案**] 對話方塊中, 展開 [**已安裝** > 的**視覺效果C#** ], 然後選擇 [ **Windows 桌面**]。

1. 選擇 [**類別庫 (.NET Framework)** ] 範本。

1. 在 [**名稱**] 文字方塊中, 輸入**CodeAnalysisManagedDemo** , 然後按一下 **[確定]** 。

1. 建立專案之後, 請開啟*Class1.cs*檔案。

1. 將 Class1.cs 中的現有文字取代為下列程式碼:

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

## <a name="analyze-the-project"></a>分析專案

### <a name="to-analyze-a-managed-project-for-code-defects"></a>若要分析 managed 專案的程式碼缺失

1. 在**方案總管**中選取 [CodeAnalysisManagedDemo] 專案。

1. 在 [專案] 功能表上，按一下 [屬性]。

     [CodeAnalysisManagedDemo 屬性] 頁面隨即顯示。

1. 選擇 [程式**代碼分析**] 索引標籤。

1. 請確定已核取 [**在組建上啟用程式碼分析**]。

1. 從 [**執行此規則集**] 下拉式清單中, 選取 [ **Microsoft 所有規則**]。

1. 在 [檔案] 功能表上, 按一下 [**儲存選取的專案**], 然後關閉 [屬性] 頁面。

1. 在 [**建立**] 功能表上, 按一下 [**建立 CodeAnalysisManagedDemo**]。

    [**錯誤清單**] 和 [**輸出**] 視窗中會顯示 CodeAnalysisManagedDemo 專案組建警告。

## <a name="correct-the-code-analysis-issues"></a>更正程式碼分析問題

### <a name="to-correct-code-analysis-rule-violations"></a>更正程式碼分析規則違規

1. 在 [ **View** ] 功能表上, 選擇 [**錯誤清單**]。

    視您選擇的開發人員設定檔而定, 您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**], 然後選擇 [**錯誤清單**]。

1. 在 [方案總管] 中選擇 [顯示所有檔案]。

1. 展開 [屬性] 節點, 然後開啟*AssemblyInfo.cs*檔案。

1. 使用下列秘訣來更正警告:

   [CA1014以 CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)標記元件:Microsoft. Design: ' demo ' 應該以 CLSCompliantAttribute 標記, 其值應為 true。

   1. 將程式碼`using System;`新增至 AssemblyInfo.cs 檔案。

   1. 接下來, 將程式`[assembly: CLSCompliant(true)]`代碼新增至 AssemblyInfo.cs 檔案的結尾。

   [CA1032 必須執行標準的例外](../code-quality/ca1032-implement-standard-exception-constructors.md)狀況構造函式:Microsoft. Design:將下列函式新增至這個類別: 公用示範 (字串)

   1. 將此函數`public demo (String s) : base(s) { }`新增至類別`demo`。

   [CA1032 必須執行標準的例外](../code-quality/ca1032-implement-standard-exception-constructors.md)狀況構造函式:Microsoft. Design:將下列函式新增至這個類別: 公用示範 (String、Exception)

   1. 將此函數`public demo (String s, Exception e) : base(s, e) { }`新增至類別`demo`。

   [CA1032 必須執行標準的例外](../code-quality/ca1032-implement-standard-exception-constructors.md)狀況構造函式:Microsoft. Design:將下列函式新增至這個類別: 受保護的示範 (SerializationInfo、StreamingCoNtext)

   1. 將程式碼`using System.Runtime.Serialization;`新增至 Class1.cs 檔案的開頭。

   1. 接下來, 新增此函式`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032 必須執行標準的例外](../code-quality/ca1032-implement-standard-exception-constructors.md)狀況構造函式:Microsoft. Design:將下列函式新增至這個類別: 公用示範 ()

   1. 將此函數`public demo () : base() { }`新增至類別`demo` **。**

   [CA1709識別碼的大小寫應](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)正確:Microsoft。命名:將命名空間名稱 ' testCode ' 變更為 ' TestCode ', 藉此修正其大小寫。

   1. 將命名空間`testCode`的大小寫變更`TestCode`為。

   [CA1709識別碼的大小寫應](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)正確:Microsoft。命名:將類型名稱「示範」變更為「示範」, 以更正其大小寫。

   1. 將成員的名稱變更為`Demo`。

   [CA1709識別碼的大小寫應](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)正確:Microsoft。命名:將成員名稱 ' item ' 的大小寫變更為 ' Item ', 以更正其大小寫。

   1. 將成員的名稱變更為`Item`。

   [CA1710識別碼應該有正確的](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)尾碼:Microsoft。命名:將 ' testCode ' 重新命名為 ' Exception ' 結尾。

   1. 將類別的名稱和其構造函式變更`DemoException`為。

   [CA2210元件應該具有有效的強](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)名稱:以強式名稱金鑰簽署 ' CodeAnalysisManagedDemo '。

   1. 在 [**專案**] 功能表上, 選擇 [ **CodeAnalysisManagedDemo 屬性**]。

      專案屬性隨即出現。

   1. 選擇 [ **簽署** ] 索引標籤。

   1. 選取 [**簽署元件**] 核取方塊。

   1. 在 **選擇字串名稱金鑰檔**清單中，選取 **\<新增...>** 。

      [**建立強式名稱金鑰**] 對話方塊隨即出現。

   1. 在機**碼檔案名**中, 輸入 y。

   1. 輸入密碼, 然後選擇 **[確定]** 。

   1. 在 [檔案] 功能表上, 選擇 [**儲存選取的專案**], 然後關閉屬性頁。

   [CA2237：使用 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)標記 ISerializable 類型:Microsoft。使用方式:將 [Serializable] 屬性加入至類型 ' demo ', 因為此類型會執行 ISerializable。

   1. 將屬性加入至類別`demo`。 `[Serializable ()]`

   完成變更之後, Class1.cs 檔案看起來應該如下所示:

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

1. 針對每個剩餘的警告, 執行下列動作:

    1. 在 **錯誤清單**中選取警告。

    1. 從右鍵功能表 (操作功能表), 選擇 [**在隱藏**專案檔中**隱藏** > ]。

1. 重建專案。

     專案建立時不會出現任何警告或錯誤。

## <a name="see-also"></a>另請參閱

[受控碼的程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)