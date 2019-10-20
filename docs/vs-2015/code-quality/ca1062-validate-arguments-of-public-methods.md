---
title: CA1062：驗證公用方法的引數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663648"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062：驗證公用方法的引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Category|Microsoft. Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見的方法會對其中一個參考引數取值，而不會驗證該引數是否 `null` （Visual Basic 中的 `Nothing`）。

## <a name="rule-description"></a>規則描述
 所有傳遞至外部可見方法的參考引數都應該針對 `null` 進行檢查。 如果適當的話，當引數 `null` 時，就會擲回 <xref:System.ArgumentNullException>。

 如果方法可以從未知的元件呼叫，因為它是宣告為公用或受保護的，您應該驗證該方法的所有參數。 如果方法設計成隻由已知元件呼叫，您應該將方法設為內部，並將 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性套用至包含方法的元件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請對 `null` 驗證每個參考引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確定已解除參考的參數已由函式中的另一個方法呼叫驗證，則可以隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的方法，以及符合規則的方法。

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>範例
 在 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] 中，此規則不會偵測到參數會傳遞至另一個執行驗證的方法。

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>範例
 填入屬於參考物件之欄位或屬性的複製函式，也可能違反 CA1062 規則。 發生違規的原因是，傳遞至複製的函式的複製物件可能 `null` （Visual Basic 中 `Nothing`）。 若要解決違規，請使用靜態（在 Visual Basic 中為 Shared）方法來檢查複製的物件是否不是 null。

 在下列 `Person` 類別範例中，可能會 `null` 傳遞至 `Person` 複製的 `other` 物件。

```

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
 在下列已修改的 `Person` 範例中，會先在 `PassThroughNonNull` 方法中檢查傳遞至複製檢查程式的 `other` 物件是否為 null。

```
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
