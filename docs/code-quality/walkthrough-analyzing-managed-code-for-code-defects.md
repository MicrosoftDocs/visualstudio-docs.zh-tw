---
title: 逐步解說分析 Managed 程式碼的程式碼缺失 |Microsoft Docs
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: fd24485d02d20bf4ab1b5def30e34b8d14a71cb3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955249"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>逐步解說：分析 managed 程式碼的程式碼缺失

在本逐步解說中，您會使用程式碼分析工具來分析 managed 的專案的程式碼缺失。

本逐步解說會引導您使用程式碼分析來分析您的.NET managed 程式碼組件符合 Microsoft.NET Framework 設計方針的程序。

## <a name="create-a-class-library"></a>建立類別庫

### <a name="to-create-a-class-library"></a>若要建立類別庫

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。

1. 在**新的專案**對話方塊方塊中，展開**已安裝** > **Visual C#**，然後選擇  **Windows 桌面**。

1. 選擇**類別庫 (.NET Framework)** 範本。

1. 在 **名稱**文字方塊中，輸入**CodeAnalysisManagedDemo** ，然後按一下 **確定**。

1. 建立專案之後，請開啟*Class1.cs*檔案。

1. 在 Class1.cs 中現有的文字取代為下列程式碼：

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

1. 將 Class1.cs 檔案。

## <a name="analyze-the-project"></a>分析專案

### <a name="to-analyze-a-managed-project-for-code-defects"></a>若要分析的程式碼缺失的受管理的專案

1. 中，選取 CodeAnalysisManagedDemo 專案**方案總管 中**。

1. 在 [專案] 功能表上，按一下 [屬性]。

     CodeAnalysisManagedDemo 的 [內容] 頁面會顯示。

1. 選擇**程式碼分析** 索引標籤。

1. 請確定**建置時啟用程式碼分析**已核取。

1. 從**執行此規則集**下拉式清單中，選取**Microsoft 所有規則**。

1. 在上**檔案**功能表上，按一下**儲存選取項目**，然後關閉 [屬性] 頁面。

1. 在 **建置**功能表上，按一下**建置 CodeAnalysisManagedDemo**。

    CodeAnalysisManagedDemo 專案建置警告所示**錯誤清單**並**輸出**windows。

## <a name="correct-the-code-analysis-issues"></a>修正程式碼分析問題

### <a name="to-correct-code-analysis-rule-violations"></a>若要修正程式碼分析規則違規

1. 在 **檢視**功能表上，選擇**錯誤清單**。

    根據您選擇的開發人員設定檔，您可能必須以指向**其他的 Windows**上**檢視**功能表，然後選擇**錯誤清單**。

1. 在 [方案總管] 中選擇 [顯示所有檔案]。

1. 展開 [屬性] 節點，然後開啟*AssemblyInfo.cs*檔案。

1. 若要修正警告，使用下列秘訣：

   [CA1014:組件必須標記 clscompliantattribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md):Microsoft.Design： 應該 clscompliantattribute 標記 「 示範 」，其值應為 true。

   1. 加入程式碼`using System;`AssemblyInfo.cs 檔案。

   1. 接下來，加入程式碼`[assembly: CLSCompliant(true)]`AssemblyInfo.cs 檔案的結尾。

   [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 公用 demo(String)

   1. 加入建構函式`public demo (String s) : base(s) { }`類別`demo`。

   [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 公用示範 （String，例外狀況）

   1. 加入建構函式`public demo (String s, Exception e) : base(s, e) { }`類別`demo`。

   [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 受保護的示範 （SerializationInfo，StreamingContext）

   1. 加入程式碼`using System.Runtime.Serialization;`Class1.cs 檔案的開頭。

   1. 接下來，新增 建構函式 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 公用 demo

   1. 加入建構函式`public demo () : base() { }`類別`demo` **。**

   [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md):Microsoft.Naming:將它變更為 'TestCode'，以修正命名空間名稱 'testCode' 的大小寫。

   1. 變更命名空間的大小寫`testCode`至`TestCode`。

   [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md):Microsoft.Naming:將它變更為 「 示範 」，以更正大小寫的型別名稱 「 示範 」。

   1. 變更之成員的名稱`Demo`。

   [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md):Microsoft.Naming:將它變更為 'Item'，以修正成員名稱 'item' 的大小寫。

   1. 變更之成員的名稱`Item`。

   [CA1710:識別項應該使用正確的後置詞](../code-quality/ca1710-identifiers-should-have-correct-suffix.md):Microsoft.Naming:將 'testCode.demo' 的重新命名為 'Exception' 結尾。

   1. 變更類別和其建構函式的名稱`DemoException`。

   [CA2210:組件應該具備有效的強式名稱](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md):使用強式名稱金鑰簽署 'CodeAnalysisManagedDemo'。

   1. 在 **專案**功能表上，選擇**CodeAnalysisManagedDemo 屬性**。

      專案屬性會出現。

   1. 選擇 [ **簽署** ] 索引標籤。

   1. 選取 **簽署組件**核取方塊。

   1. 在 **選擇字串名稱金鑰檔**清單中，選取**\<新增...>**。

      **建立強式名稱金鑰** 對話方塊隨即出現。

   1. 在 **金鑰檔名稱**，類型為 TestKey。

   1. 輸入密碼，然後選擇**確定**。

   1. 在 **檔案**功能表上，選擇**儲存選取項目**，然後關閉 屬性頁。

   [CA2237： 必須Serializableattribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md):Microsoft.Usage:加入輸入 'demo' 因為此類型會實作 ISerializable [Serializable] 屬性。

   1. 新增`[Serializable ()]`屬性加入該類別`demo`。

   完成變更之後，Class1.cs 檔案看起來應該如下所示：

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

### <a name="to-exclude-code-defect-warnings"></a>若要排除程式碼缺失警告

1. 針對每個剩餘的警告中，執行下列作業：

    1. 選取中的警告**錯誤清單**。

    1. 以滑鼠右鍵按一下功能表或操作功能表，選擇**抑制** > **檔案中的隱藏項目**。

1. 重建專案。

     專案組建，而不出現任何警告或錯誤。

## <a name="see-also"></a>另請參閱

[Managed 程式碼的程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)