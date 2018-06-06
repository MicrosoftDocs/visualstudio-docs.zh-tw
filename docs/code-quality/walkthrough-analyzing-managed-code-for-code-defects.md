---
title: 逐步解說分析 Managed 程式碼的程式碼缺失 |Microsoft 文件
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a353d7a61f9bc1dbb83d37ad419c3d2fbdf656ba
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746555"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>逐步解說： 分析 managed 程式碼程式碼缺失

在本逐步解說中，您會使用程式碼分析工具來分析 managed 的專案的程式碼缺失。

本逐步解說會引導您完成使用程式碼分析來分析您的.NET managed 程式碼組件符合 Microsoft.NET Framework 設計方針的程序。

## <a name="create-a-class-library"></a>建立類別庫

### <a name="to-create-a-class-library"></a>若要建立類別庫

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。

1. 在**新專案**對話方塊方塊中，展開 **已安裝** > **Visual C#**，然後選擇  **Windows 桌面**。

1. 選擇**類別庫 (.NET Framework)** 範本。

1. 在**名稱**文字方塊中，輸入**CodeAnalysisManagedDemo** ，然後按一下 **確定**。

1. 在建立專案之後，請開啟*Class1.cs*檔案。

1. 下列程式碼取代 Class1.cs 中的現有文字：

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

## <a name="analyze-the-project"></a>分析的專案

### <a name="to-analyze-a-managed-project-for-code-defects"></a>若要分析的 managed 的專案的程式碼缺失

1. CodeAnalysisManagedDemo 中選取專案**方案總管 中**。

1. 在 [專案] 功能表上，按一下 [屬性]。

     CodeAnalysisManagedDemo 屬性頁面會顯示。

1. 選擇**程式碼分析** 索引標籤。

1. 請確定**建置時啟用程式碼分析**已核取。

1. 從**執行此規則集**下拉式清單中，選取**Microsoft 所有規則**。

1. 在**檔案**功能表上，按一下 **儲存選取項目**，然後關閉屬性頁。

1. 在**建置**功能表上，按一下 **建置 CodeAnalysisManagedDemo**。

    CodeAnalysisManagedDemo 專案建置警告如下所示**錯誤清單**和**輸出**windows。

## <a name="correct-the-code-analysis-issues"></a>修正程式碼分析問題

### <a name="to-correct-code-analysis-rule-violations"></a>若要修正程式碼分析規則違規

1. 在**檢視**功能表上，選擇**錯誤清單**。

    根據您選擇的開發人員設定檔，您可能必須指向**其他視窗**上**檢視**功能表，然後選擇 **錯誤清單**。

1. 在**方案總管 中**，選擇**顯示所有檔案**。

1. 展開 [屬性] 節點，然後開啟*AssemblyInfo.cs*檔案。

1. 若要更正這些警告中使用下列秘訣：

   [CA1014： 以 CLSCompliantAttribute 的組件的標記](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 「 示範 」 應該以 CLSCompliantAttribute 標記和其值必須為 true。

   1. 加入程式碼`using System;`AssemblyInfo.cs 檔案。

   1. 接下來，加入程式碼`[assembly: CLSCompliant(true)]`AssemblyInfo.cs 檔案結尾。

   [Ca1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design： 將下列建構函式加入至這個類別： 公用 demo(String)

   1. 加入建構函式`public demo (String s) : base(s) { }`類別`demo`。

   [Ca1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design： 將下列建構函式加入至這個類別： 公用示範 （String，例外狀況）

   1. 加入建構函式`public demo (String s, Exception e) : base(s, e) { }`類別`demo`。

   [Ca1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design： 將下列建構函式加入至這個類別： 受保護 （SerializationInfo，StreamingContext） 的示範

   1. 加入程式碼`using System.Runtime.Serialization;`Class1.cs 檔的開頭。

   1. 接下來，加入建構函式 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [Ca1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design： 將下列建構函式加入至這個類別： 公用 demo()

   1. 加入建構函式`public demo () : base() { }`類別`demo` **。**

   [CA1709： 識別項應該使用的大小寫正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming： 更正，請將它變更為 'TestCode' 命名空間名稱 'testCode' 的大小寫。

   1. 變更命名空間的大小寫`testCode`至`TestCode`。

   [CA1709： 識別項應該使用的大小寫正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming： 更正大小寫的型別名稱 「 示範 」，請將它變更為 「 示範 」。

   1. 變更之成員的名稱`Demo`。

   [CA1709： 識別項應該使用的大小寫正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming： 更正大小寫的成員名稱 'item'，請將它變更為 'Item'。

   1. 變更之成員的名稱`Item`。

   [： Ca1710 識別項應該正確的後置詞](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming： 重新命名 'testCode.demo' 'Exception' 結尾。

   1. 變更的類別和其建構函式名稱`DemoException`。

   [CA2210： 組件應該具有有效的強式名稱](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)： 使用強式名稱金鑰簽署 'CodeAnalysisManagedDemo'。

   1. 在**專案**功能表上，選擇**CodeAnalysisManagedDemo 屬性**。

      專案屬性會出現。

   1. 選擇 [ **簽署** ] 索引標籤。

   1. 選取**簽署組件**核取方塊。

   1. 在**選擇字串名稱金鑰檔**清單中，選取**\<新增...>**。

      **建立強式名稱金鑰** 對話方塊隨即出現。

   1. 在**金鑰檔名稱**，輸入為 TestKey。

   1. 輸入密碼，然後選擇**確定**。

   1. 在**檔案**功能表上，選擇**儲存選取項目**，然後關閉屬性頁。

   [Ca2237： 必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage： 加入輸入為此類型可以實作 ISerializable '示範' [Serializable] 屬性。

   1. 新增`[Serializable ()]`屬性加入該類別`demo`。

   完成變更之後，將 Class1.cs 檔案看起來應該如下所示：

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

1. 針對每個剩餘的警告，執行下列作業：

    1. 選取中的警告**錯誤清單**。

    1. 以滑鼠右鍵按一下或內容功能表上，選擇**抑制** > **中隱藏項目檔**。

1. 重建專案。

     專案建置時沒有任何警告或錯誤訊息。

## <a name="see-also"></a>另請參閱

[Managed 程式碼的程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)