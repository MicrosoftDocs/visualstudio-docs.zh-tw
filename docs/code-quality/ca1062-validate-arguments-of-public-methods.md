---
title: CA1062：驗證公用方法的引數
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac6f150903c54c7bea6b5f092aa472a6b3a6e08e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062：驗證公用方法的引數

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因

外部可見的方法會對其中一個參考引數不需驗證該引數是否`null`(`Nothing`在 Visual Basic 中)。

## <a name="rule-description"></a>規則描述

所有傳遞至外部可見方法的參考引數應經過`null`。 如果可行，會擲回<xref:System.ArgumentNullException>引數是當`null`。

如果可以從未知的組件呼叫方法，因為它宣告為公用或受保護，您應該驗證方法的所有參數。 如果方法設計成只能由已知的組件呼叫中，您應該將方法設為內部，並套用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性設定為包含方法的組件。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，驗證每個參考引數的`null`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您確定取值的參數已由另一個函式中的方法呼叫驗證，您可以隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反規則的方法和滿足規則的方法。

 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>範例

填入欄位或屬性所參考物件的複製建構函式也可能會違反 CA1062 規則。 因為複製的物件傳遞至複製建構函式可能會發生違規`null`(`Nothing`在 Visual Basic 中)。 若要解決此違規情形，使用靜態 (在 Visual Basic 中的是 Shared) 方法來檢查複製的物件不是 null。

在下列`Person`類別範例`other`物件傳遞至`Person`複製建構函式可能`null`。

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>範例

以下修訂`Person`範例中，`other`物件傳遞至複製建構函式，會先檢查中的 null`PassThroughNonNull`方法。

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}

```