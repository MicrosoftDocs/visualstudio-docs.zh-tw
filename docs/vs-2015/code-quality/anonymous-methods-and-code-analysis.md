---
title: 匿名方法和程式碼分析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8b3f64a0b5f70067367e98d7e1d1471fc670099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157068"
---
# <a name="anonymous-methods-and-code-analysis"></a>匿名方法和程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*匿名方法*是沒有名稱的方法。 匿名方法最常用來做為委派參數傳遞的程式碼區塊。  
  
 本主題說明程式碼分析如何處理警告和匿名方法相關聯的度量資訊。  
  
## <a name="anonymous-methods-declared-in-a-member"></a>在成員中宣告的匿名方法  
 警告和計量以便使匿名方法宣告的成員，例如方法或存取子，會宣告方法的成員與相關聯。 它們不會呼叫方法的成員與相關聯。  
  
 例如，在下列類別中，找到的宣告中的任何警告**anonymousMethod**應該針對引發**Method1**而非**Method2**。  
  
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
 警告和匿名方法宣告為內嵌指派給欄位的計量是建構函式相關聯。 如果欄位宣告為`static`(`Shared`在[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])、 警告和計量是相關聯的類別建構函式，否則為，它們的執行個體建構函式相關聯。  
  
 例如，在下列類別中，找到的宣告中的任何警告**anonymousMethod1**就會引發對隱含產生的預設建構函式**類別**。 然而，這些位於**anonymousMethod2**會實施以隱含方式產生的類別建構函式。  
  
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
  
 類別可以包含內嵌匿名方法，將值指派給具有多個建構函式的欄位。 在此情況下，警告和計量是相關聯的所有建構函式除非該建構函式鏈結到相同的類別中的另一個建構函式。  
  
 例如，在下列類別中，找到的宣告中的任何警告**anonymousMethod**應該針對引發**Class(int)** 並**Class(string)** 但不是針對**Class()** 。  
  
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
  
 雖然這看起來可能會非預期，這是因為編譯器會將輸出未鏈結至另一個建構函式的每個建構函式的唯一方法。 由於這個行為，任何違規，常見於**anonymousMethod**必須個別隱藏。 這也表示，如果新的建構函式會導入，先前已針對隱藏的警告**Class(int)** 並**Class(string)** 也可以隱藏對新的建構函式。  
  
 您可以暫時解決此問題，在兩種方式之一。 您可以宣告**anonymousMethod**常見的建構函式中，所有的建構函式鏈結。 或者，您可以在初始設定方法所呼叫的所有建構函式中宣告它。  
  
## <a name="see-also"></a>另請參閱  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
