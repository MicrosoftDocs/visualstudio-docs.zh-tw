---
title: "匿名方法和程式碼分析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "匿名方法, 程式碼分析"
  - "程式碼分析, 匿名方法"
  - "方法, 匿名"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# 匿名方法和程式碼分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「*匿名方法*」\(Anonymous Method\) 就是沒有名稱的方法。  匿名方法是將程式碼區塊當做委派 \(Delegate\) 參數傳遞時最常使用的方法。  
  
 本主題說明程式碼分析如何處理與匿名方法相關聯的警告和度量資訊。  
  
## 成員內宣告的匿名方法  
 宣告在成員中的匿名方法的警告和度量資訊，例如方法或存取子，是與宣告方法的成員相關聯。  但是與呼叫該方法的成員無關。  
  
 例如，在下列類別中，**anonymousMethod** 宣告中出現的任何警告，都應該針對 **Method1** 引發，而不是 **Method2**。  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
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
  
## 內嵌匿名方法  
 匿名方法的警告和度量資訊如果宣告為欄位的內嵌指派，則是與建構函式相關聯的。  如果欄位宣告為 `static` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Shared`\)，那麼警告和度量資訊則與類別建構函式相關聯。否則他們會與執行個體建構函式相關聯。  
  
 例如，在下列類別中，**anonymousMethod1** 宣告中出現的任何警告，都會針對 **Class** 隱含產生的預設建構函式來引發。  而 **anonymousMethod2** 內出現的警告將會針對隱含產生的預設建構函式來套用。  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
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
  
 類別可以包含內嵌匿名方法，用於指派值給具有多重建構函式的欄位。  在這種情況下，警告和度量資訊是與所有建構函式相關聯，除非該建構函式鏈結到相同類別中的另一個建構函式。  
  
 例如，在下列類別中，**anonymousMethod** 宣告中出現的任何警告，都應該針對 **Class\(int\)** 和 **Class\(string\)** 引發，而不是 **Class\(\)**。  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
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
  
 雖然這似乎不如預期，但發生這樣的原因在於編譯器會為每個沒有鏈結到另一個建構函式的建構函式，輸出唯一的方法。  因為這項行為，所以 **anonymousMethod** 內發生的任何違規都必須個別隱藏。  這也代表如果引入新的建構函式，先前針對 **Class\(int\)** 和 **Class\(string\)** 隱藏的警告，也都必須針對新建構函式隱藏。  
  
 您可以採用兩種方法中的一個解決這個問題。  您可以在所有建構函式所鏈結的通用建構函式中宣告 **anonymousMethod**。  或是可以在所有建構函式呼叫的初始設定方法中宣告。  
  
## 請參閱  
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)