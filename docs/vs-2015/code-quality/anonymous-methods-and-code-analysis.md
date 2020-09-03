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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652216"
---
# <a name="anonymous-methods-and-code-analysis"></a>匿名方法和程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*匿名方法*是沒有名稱的方法。 匿名方法最常用來將程式碼區塊當做委派參數傳遞。

 本主題說明程式碼分析如何處理與匿名方法相關聯的警告和計量。

## <a name="anonymous-methods-declared-in-a-member"></a>成員中宣告的匿名方法
 在成員中宣告的匿名方法（例如方法或存取子）的警告和度量，會與宣告方法的成員相關聯。 它們不會與呼叫方法的成員相關聯。

 例如，在下列類別中， **anonymousMethod** 宣告中找到的任何警告都應針對 **Method1** 引發，而不是 **Method2**。

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
 宣告為欄位之內嵌指派的匿名方法的警告和度量會與該函式相關聯。 如果欄位在 `static`) 中宣告為 `Shared` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ，則警告和度量會與類別的函式相關聯，否則會與實例的函式相關聯。

 例如，在下列類別中，會針對以隱含方式產生之**類別**的預設函式，引發在**anonymousMethod1**宣告中找到的任何警告。 然而，在 **anonymousMethod2** 中找到的會套用至隱含產生的類別的函式。

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

 類別可以包含內嵌匿名方法，該方法會將值指派給具有多個函式的欄位。 在此情況下，除非該函式會連結至相同類別中的另一個函式，否則警告和計量會與所有的函式相關聯。

 例如，在下列類別中，在 **anonymousMethod** 宣告中找到的任何警告都應該針對 **class (Int) ** 和 **class (string) ** ，而不是針對 **類別 ( # B5 **來引發。

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

 雖然這看起來似乎不是預期的，但這是因為編譯器會針對每個未與另一個函式的函式，輸出唯一的方法。 由於這種行為，在 **anonymousMethod** 中發生的任何違規都必須分開隱藏。 這也表示，如果引進新的函式，則先前針對 **類別 (int) ** 和 **類別 (字串) ** 隱藏的警告也必須針對新的函式隱藏。

 您可以透過下列兩種方式之一來解決這個問題。 您可以在所有的函式所鏈的通用函式中宣告 **anonymousMethod** 。 或者，您可以在所有的函式所呼叫的初始化方法中宣告它。

## <a name="see-also"></a>另請參閱
 [分析 Managed 程式碼品質](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
