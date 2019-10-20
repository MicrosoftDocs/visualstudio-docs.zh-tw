---
title: 逐步解說：分析 Managed 程式碼是否有缺陷 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609325"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>逐步解說：分析 Managed 程式碼中的程式碼缺失
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在此逐步解說中，您會使用程式碼分析工具來分析 managed 專案中的程式碼缺失。

 本逐步解說將引導您完成使用程式碼分析來分析您的 .NET managed 程式碼元件，以符合 Microsoft .NET Framework 設計方針的流程。

 在本逐步解說中，您會：

- 分析和更正程式碼缺失警告。

## <a name="prerequisites"></a>Prerequisites

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]

## <a name="create-a-class-library"></a>建立類別庫

#### <a name="to-create-a-class-library"></a>若要建立類別庫

1. **在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 的 [檔案**] 功能表上，按一下 [**新增**]，然後按一下 [**專案**]。

2. 在 [**新增專案**] 對話方塊的 [**專案類型**] 底下，按一下 [**視覺效果C#** ]。

3. 在 [**範本**] 底下，選取 [**類別庫**]。

4. 在 [**名稱**] 文字方塊中，輸入**CodeAnalysisManagedDemo** ，然後按一下 **[確定]** 。

5. 建立專案之後，請開啟 Class1.cs 檔案。

6. 將 Class1.cs 中的現有文字取代為下列程式碼：

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. 儲存 Class1.cs 檔案。

## <a name="analyze-the-project"></a>分析專案

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>若要分析 managed 專案的程式碼缺失

1. 在**方案總管**中選取 [CodeAnalysisManagedDemo] 專案。

2. 在 [專案] 功能表上，按一下 [屬性]。

     [CodeAnalysisManagedDemo 屬性] 頁面隨即顯示。

3. 按一下 [ **CodeAnalysis**]。

4. 請確定已核取 **[在組建上啟用程式碼分析（定義 CODE_ANALYSIS 常數**）]。

5. 從 [**執行此規則集**] 下拉式清單中，選取 [ **Microsoft 所有規則**]。

6. **在 [檔案**] 功能表上，按一下 [**儲存選取的專案**]，然後關閉 [ManagedDemo 屬性] 頁面。

7. 在 [**建立**] 功能表上，按一下 [**建立 ManagedDemo**]。

     [程式**代碼分析**] 和 [**輸出**] 視窗中會報告 CodeAnalysisManagedDemo 專案組建警告。

     如果 [程式**代碼分析**] 視窗未出現，請在 [**分析**] 功能表上選擇 [**視窗**]，然後**選擇 [程式碼分析**]。

## <a name="correct-the-code-analysis-issues"></a>更正程式碼分析問題

#### <a name="to-correct-code-analysis-rule-violations"></a>更正程式碼分析規則違規

1. 在 [ **View** ] 功能表上，按一下 [**錯誤清單**]。

     視您選擇的開發人員設定檔而定，您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**]，然後按一下 [**錯誤清單**]。

2. 在**方案總管**中，按一下 [**顯示所有**檔案]。

3. 接下來，展開 [屬性] 節點，然後開啟 AssemblyInfo.cs 檔案。

4. 使用下列內容來更正警告：

- [CA1014： Mark 具有 CLSCompliantAttribute 的元件](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)： Microsoft. Design： ' demo ' 應該以 CLSCompliantAttribute 標記，而其值應為 true。

  - 將程式碼 `using``System;` 新增至 AssemblyInfo.cs 檔案。

       接下來，將程式碼 `[assembly: CLSCompliant(true)]` 新增至 AssemblyInfo.cs 檔案的結尾。

       重建專案。

- [Ca1032 必須：實作為標準例外狀況構造](../code-quality/ca1032-implement-standard-exception-constructors.md)函式： Microsoft. Design：將下列函式新增至這個類別：公用示範（字串）

  - 將 `public demo (String s) : base(s) { }` 的函式新增至類別 `demo`。

- [Ca1032 必須：實作為標準例外狀況構造](../code-quality/ca1032-implement-standard-exception-constructors.md)函式： Microsoft. Design：將下列函式新增至這個類別：公用示範（字串、例外狀況）

  - 將 `public demo (String s, Exception e) : base(s, e) { }` 的函式新增至類別 `demo`。

- [Ca1032 必須：實作為標準例外狀況構造](../code-quality/ca1032-implement-standard-exception-constructors.md)函式： Microsoft. Design：將下列函式新增至這個類別： protected Demo （SerializationInfo，StreamingCoNtext）

  - 將程式碼 `using System.Runtime.Serialization;` 新增至 Class1.cs 檔案的開頭。

       接下來，新增此函式 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       重建專案。

- [Ca1032 必須：實作為標準例外狀況構造](../code-quality/ca1032-implement-standard-exception-constructors.md)函式： Microsoft. Design：將下列函式新增至這個類別：公用示範（）

  - 將 `public demo () : base() { }` 的函式新增至類別 `demo` **。**

       重建專案。

- [CA1709：識別碼的大小寫應正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)： Microsoft. 命名空間名稱 ' testCode ' 的大小寫，方法是將其變更為 ' testCode '。

  - 將命名空間 `testCode` 的大小寫變更為 `TestCode`。

- [CA1709：識別碼的大小寫應正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)： Microsoft. 命名：將類型名稱「示範」變更為「示範」，以更正其大小寫。

  - 將成員的名稱變更為 `Demo`。

- [CA1709：識別碼的大小寫應正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)： Microsoft. 命名：將成員名稱 ' item ' 的大小寫變更為 ' item '，以更正其大小寫。

  - 將成員的名稱變更為 `Item`。

- [CA1710：識別碼應具有正確的後](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)置詞： Microsoft. 命名：將 ' TestCode ' 重新命名為 ' Exception ' 結尾。

  - 將類別的名稱和其構造函式變更為 `DemoException`。

- [CA2210：元件應具有有效的強式名稱](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)：使用強式名稱金鑰簽署 ' ManagedDemo '。

  - 在 [**專案**] 功能表上，按一下 [ **ManagedDemo 屬性**]。

       專案屬性隨即出現。

       按一下 [**簽署**]。

       選取 [**簽署元件**] 核取方塊。

       在 **選擇字串名稱金鑰**檔 清單中，選取  **\<New 。>** 。

       [**建立強式名稱金鑰**] 對話方塊隨即出現。

       在機**碼檔案名**中，輸入 y。

       輸入密碼，然後按一下 **[確定]** 。

       **在 [檔案**] 功能表上，按一下 [**儲存選取的專案**]，然後關閉屬性頁。

       重建專案。

- [Ca2237 必須：將 iserializable 類型標記為 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)： Microsoft。使用方式：將 [Serializable] 屬性加入至類型 ' demo '，因為此類型會執行 ISerializable。

  - 將 `[Serializable ()]` 屬性加入 `demo` 的類別。

       重建專案。

  完成變更之後，Class1.cs 檔案看起來應該如下所示：

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>排除程式碼分析警告

#### <a name="to-exclude-code-defect-warnings"></a>若要排除程式碼瑕疵警告

1. 針對每個剩餘的警告，執行下列動作：

   1. 在 [程式碼分析] 視窗中，選取警告。

   2. 選擇 [**動作**]，然後選擇 [**隱藏訊息**]，再選擇 [**在專案隱藏檔中**]。

      如需詳細資訊，請參閱[如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. 重建專案。

    專案建立時不會出現任何警告或錯誤。
