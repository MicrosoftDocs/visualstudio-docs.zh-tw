---
title: "匿名方法和程式碼分析 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ebf550ca92cbefbed684e2b11e0b20b62661133
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="anonymous-methods-and-code-analysis"></a>匿名方法和程式碼分析
*匿名方法*是沒有名稱的方法。 匿名方法最常用來做為委派的參數傳遞的程式碼區塊。  
  
 本主題會說明程式碼分析會處理警告和匿名方法相關聯的度量資訊。  
  
## <a name="anonymous-methods-declared-in-a-member"></a>宣告為成員內的匿名方法  
 警告和匿名方法中的成員，例如方法或存取子，宣告的度量資訊與相關聯的宣告方法的成員。 它們不會在呼叫方法的成員與相關聯。  
  
 例如，在下列類別宣告中所找到的任何警告**anonymousMethod**應該針對引發**Method1**而非**Method2**。  
  
```vb  
  
      Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5  
        Method2(anonymousMethod)  
    End SubSub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## <a name="inline-anonymous-methods"></a>內嵌匿名方法  
 警告和匿名方法宣告為內嵌指派給欄位的度量資訊與相關聯的建構函式。 如果欄位宣告為`static`(`Shared`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、 警告和度量資訊與相關聯的類別建構函式，否則它們的執行個體建構函式與相關聯。  
  
 例如，在下列類別宣告中所找到的任何警告**anonymousMethod1** ，系統將產生的隱含產生的預設建構函式針對**類別**。 而這些位於**anonymousMethod2**隱含產生的類別建構函式，將會套用。  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 類別可以包含內嵌匿名方法，將值指派給具有多個建構函式的欄位。 在此情況下，警告和度量資訊與相關聯的所有建構函式除非該建構函式鏈結到相同類別中的其他建構函式。  
  
 例如，在下列類別宣告中所找到的任何警告**anonymousMethod**應該針對引發**Class(int)**和**Class(string)**但不是針對**Class()**。  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
SubNew()  
    New(CStr(Nothing))  
End SubSub New(ByVal a As Integer)  
End SubSub New(ByVal a As String)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 雖然這看起來可能會非預期，這是因為編譯器會輸出未鏈結至另一個建構函式每個建構函式的唯一方法。 基於此行為，任何違規，就會發生在**anonymousMethod**必須分別隱藏。 這也表示，如果新的建構函式會導入了對已先前隱藏的警告**Class(int)**和**Class(string)**也會歸併針對新的建構函式。  
  
 您可以暫時解決此問題，在兩種方式之一。 您無法宣告**anonymousMethod**一般建構函式中的所有建構函式鏈結。 或者，您無法在初始設定方法所呼叫的所有建構函式宣告它。  
  
## <a name="see-also"></a>另請參閱  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)