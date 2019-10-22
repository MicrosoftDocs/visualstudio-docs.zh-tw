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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652216"
---
# <a name="anonymous-methods-and-code-analysis"></a>匿名方法和程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*匿名方法*是沒有名稱的方法。 匿名方法最常用來傳遞程式碼區塊做為委派參數。

 本主題說明程式碼分析如何處理與匿名方法相關聯的警告和計量。

## <a name="anonymous-methods-declared-in-a-member"></a>成員中宣告的匿名方法
 在成員中宣告的匿名方法（例如方法或存取子）的警告和計量，會與宣告該方法的成員相關聯。 它們不會與呼叫方法的成員相關聯。

 例如，在下列類別中，在**anonymousMethod**的宣告中找到的任何警告都應該針對**Method1**而非**Method2**引發。

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
 宣告為欄位之內嵌指派的匿名方法，其警告和計量會與此函式相關聯。 如果欄位宣告為 `static` （在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中為 `Shared`），則警告和計量會與類別的「函式」相關聯;否則，它們會與實例的「處理函式」相關聯。

 例如，在下列類別中，在**anonymousMethod1**的宣告中找到的任何警告都會針對**類別**的隱含產生預設函式來引發。 不過，在**anonymousMethod2**中找到的會針對隱含產生的類別的函式套用。

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

 類別可以包含內嵌匿名方法，將值指派給具有多個函數的欄位。 在此情況下，警告和計量會與所有的函式相關聯，除非該函式會連結至相同類別中的另一個函式。

 例如，在下列類別中，在**anonymousMethod**的宣告中找到的任何警告都應該針對**類別（Int）** 和**類別（字串）** 引發，而不是針對**class （）** 。

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

 雖然這看起來似乎不是預期的，但這是因為編譯器會針對每個未連結至另一個函式的函式，輸出唯一的方法。 基於此行為， **anonymousMethod**中發生的任何違規都必須分開隱藏。 這也表示，如果引進了新的函式，先前針對**類別（int）** 和**類別（字串）** 隱藏的警告也必須針對新的檢查程式隱藏。

 您可以使用兩種方法之一來解決此問題。 您可以在所有的函式所鏈通用的函式中宣告**anonymousMethod** 。 或者，您可以在所有的程式調用的初始化方法中宣告它。

## <a name="see-also"></a>請參閱
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
