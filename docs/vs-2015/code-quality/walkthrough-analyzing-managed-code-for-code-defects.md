---
title: 逐步解說：分析 Managed 程式碼的程式碼缺失 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d8412318efd2292fd0f5a0f0ef52fe36c7d06c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116286"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>逐步解說：分析受控碼的程式碼缺失
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說中，您可以分析程式碼缺失的 managed 的的專案使用程式碼分析工具。  
  
 本逐步解說將引導您逐步使用程式碼分析來分析您的.NET managed 程式碼組件符合 Microsoft.NET Framework 設計方針的程序。  
  
 在本逐步解說中，您：  
  
- 分析和修正程式碼缺失警告。  
  
## <a name="prerequisites"></a>必要條件  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>建立類別庫  
  
#### <a name="to-create-a-class-library"></a>若要建立類別庫  
  
1. 在上**檔案**功能表[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]，按一下 **新增**，然後按一下**專案**。  
  
2. 在 **新的專案**對話方塊的 **專案類型**，按一下  **Visual C#** 。  
  
3. 底下**範本**，選取**類別庫**。  
  
4. 在 **名稱**文字方塊中，輸入**CodeAnalysisManagedDemo** ，然後按一下 **確定**。  
  
5. 建立專案之後，開啟 Class1.cs 檔。  
  
6. 在 Class1.cs 中現有的文字取代為下列程式碼：  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7. 將 Class1.cs 檔案。  
  
## <a name="analyze-the-project"></a>分析專案  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>若要分析的程式碼缺失的受管理的專案  
  
1. 中，選取 CodeAnalysisManagedDemo 專案**方案總管 中**。  
  
2. 在 [專案]  功能表上，按一下 [屬性]  。  
  
     CodeAnalysisManagedDemo 的 [內容] 頁面會顯示。  
  
3. 按一下  **CodeAnalysis**。  
  
4. 請確定**建置時啟用程式碼分析 (定義 CODE_ANALYSIS 常數**) 核取。  
  
5. 從**執行此規則集**下拉式清單中，選取**Microsoft 所有規則**。  
  
6. 在上**檔案**功能表上，按一下**儲存選取項目**，然後關閉 ManagedDemo 屬性頁面。  
  
7. 在 **建置**功能表上，按一下**建置 ManagedDemo**。  
  
     CodeAnalysisManagedDemo 專案建置警告不會報告**程式碼分析**並**輸出**windows。  
  
     如果**程式碼分析**] 視窗沒有出現，在**分析**功能表上，選擇 [ **Windows** ，然後**選擇程式碼分析**。  
  
## <a name="correct-the-code-analysis-issues"></a>修正程式碼分析問題  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>若要修正程式碼分析規則違規  
  
1. 在 **檢視**功能表上，按一下**錯誤清單**。  
  
     根據您選擇的開發人員設定檔，您可能必須以指向**其他的 Windows**上**檢視**功能表，然後再按一下**錯誤清單**。  
  
2. 在 **方案總管**，按一下**顯示所有檔案**。  
  
3. 接下來，依序展開 屬性 節點，然後開啟 AssemblyInfo.cs 檔案。  
  
4. 您可以使用下列命令修正警告：  
  
- [CA1014:組件必須標記 clscompliantattribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md):Microsoft.Design： 應該 clscompliantattribute 標記 「 示範 」，其值應為 true。  
  
  - 加入程式碼`using``System;`AssemblyInfo.cs 檔案。  
  
       接下來，加入程式碼`[assembly: CLSCompliant(true)]`AssemblyInfo.cs 檔案的結尾。  
  
       重建專案。  
  
- [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 公用 demo(String)  
  
  - 加入建構函式`public demo (String s) : base(s) { }`類別`demo`。  
  
- [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 公用示範 （String，例外狀況）  
  
  - 加入建構函式`public demo (String s, Exception e) : base(s, e) { }`類別`demo`。  
  
- [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 受保護的示範 （SerializationInfo，StreamingContext）  
  
  - 加入程式碼`using System.Runtime.Serialization;`Class1.cs 檔案的開頭。  
  
       接下來，新增 建構函式 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       重建專案。  
  
- [CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md):Microsoft.Design:將下列建構函式加入至這個類別： 公用 demo  
  
  - 加入建構函式`public demo () : base() { }`類別`demo` **。**  
  
       重建專案。  
  
- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md):Microsoft.Naming:將它變更為 'TestCode'，以修正命名空間名稱 'testCode' 的大小寫。  
  
  - 變更命名空間的大小寫`testCode`至`TestCode`。  
  
- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md):Microsoft.Naming:將它變更為 「 示範 」，以更正大小寫的型別名稱 「 示範 」。  
  
  - 變更之成員的名稱`Demo`。  
  
- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md):Microsoft.Naming:將它變更為 'Item'，以修正成員名稱 'item' 的大小寫。  
  
  - 變更之成員的名稱`Item`。  
  
- [CA1710:識別項應該使用正確的後置詞](../code-quality/ca1710-identifiers-should-have-correct-suffix.md):Microsoft.Naming:將 'testCode.demo' 的重新命名為 'Exception' 結尾。  
  
  - 變更類別和其建構函式的名稱`DemoException`。  
  
- [CA2210:組件應該具備有效的強式名稱](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md):使用強式名稱金鑰簽署 'ManagedDemo'。  
  
  - 在 **專案**功能表上，按一下**ManagedDemo 屬性**。  
  
       專案屬性會出現。  
  
       按一下 **簽署**。  
  
       選取 **簽署組件**核取方塊。  
  
       在 **選擇字串名稱金鑰檔**清單中，選取 **\<新增...>** 。  
  
       **建立強式名稱金鑰** 對話方塊隨即出現。  
  
       在 **金鑰檔名稱**，類型為 TestKey。  
  
       輸入密碼，然後按一下**確定**。  
  
       在 **檔案** 功能表中，按一下**儲存選取項目**，然後關閉 屬性頁。  
  
       重建專案。  
  
- [CA2237：Serializableattribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md):Microsoft.Usage:加入輸入 'demo' 因為此類型會實作 ISerializable [Serializable] 屬性。  
  
  - 新增`[Serializable ()]`屬性加入該類別`demo`。  
  
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
  
#### <a name="to-exclude-code-defect-warnings"></a>若要排除程式碼缺失警告  
  
1. 針對每個剩餘的警告中，執行下列作業：  
  
   1. 在 [程式碼分析] 視窗中，選取警告。  
  
   2. 選擇**動作**，然後選擇**隱藏訊息**，然後選擇**專案隱藏項目檔中的流程範本**。  
  
      如需詳細資訊，請參閱[如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. 重建專案。  
  
    專案組建，而不出現任何警告或錯誤。
