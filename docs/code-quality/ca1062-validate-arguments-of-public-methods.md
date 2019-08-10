---
title: CA1062:必須驗證公用方法的引數
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3868061a01572d0b1adadec6619f88269d353dff
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922443"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062:必須驗證公用方法的引數

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因

外部可見的方法會對其中一個參考引數取值, 而不會`null`驗證`Nothing`該引數是否為 (在 Visual Basic 中)。

## <a name="rule-description"></a>規則描述

所有傳遞至外部可見方法的參考引數都應該針對`null`進行檢查。 如果適當的話, <xref:System.ArgumentNullException>當引數為時, 會`null`擲回。

如果方法可以從未知的元件呼叫, 因為它是宣告為公用或受保護的, 您應該驗證該方法的所有參數。 如果方法設計成隻由已知元件呼叫, 您應該將方法設為內部, 並將<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性套用至包含方法的元件。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形, 請針對`null`每個參考引數進行驗證。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您確定已解除參考的參數已由函式中的另一個方法呼叫驗證, 則可以隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反規則的方法, 以及符合規則的方法。

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

填入屬於參考物件之欄位或屬性的複製函式, 也可能違反 CA1062 規則。 發生違規的原因是, 傳遞至複製的函式的複製物件可能`null`是`Nothing` (在 Visual Basic 中)。 若要解決違規, 請使用靜態 (在 Visual Basic 中為 Shared) 方法來檢查複製的物件是否不是 null。

在下列`Person`類別範例中`other` , 傳遞至`Person`複製函數的物件可能是`null`。

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

在下列已修改`Person`的範例中`other` , 會先在`PassThroughNonNull`方法中檢查傳遞至複製檢查程式的物件是否為 null。

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