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
ms.openlocfilehash: 377906675d70a712f8ca72b0b6e4d8a6864c1fbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533233"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062:必須驗證公用方法的引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見的方法會在其中一個參考引數中進行取值，而不會驗證是否 `null` `Nothing` 在 Visual Basic) 中 (該引數。

## <a name="rule-description"></a>規則描述
 所有傳遞給外部可見方法的參考引數都應該針對進行檢查 `null` 。 如果有的話，則在 <xref:System.ArgumentNullException> 引數為時擲回 `null` 。

 如果可以從未知的元件呼叫方法，因為它是宣告為公用或受保護的，您應該驗證方法的所有參數。 如果方法設計為只能由已知的元件呼叫，您應該將方法設為內部，並將 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性套用至包含方法的元件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請針對每個參考引數進行驗證 `null` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確定函式中的另一個方法呼叫已驗證可取值的參數，您可以隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的方法，以及滿足規則的方法。

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>範例
 在中 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] ，這項規則並不會偵測到參數會傳遞至另一個執行驗證的方法。

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>範例
 填入參考物件之欄位或屬性的複製函式，也可能違反 CA1062 規則。 發生違規的原因是，傳遞至複製函式的複製物件可能會 `null` `Nothing` 在 Visual Basic) 中 (。 若要解決違規，請使用 Visual Basic) 方法中共用的靜態 (，以檢查複製的物件是否不是 null。

 在下列 `Person` 類別範例中， `other` 傳遞至 `Person` 複製函數的物件可能是 `null` 。

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
 在下列修訂的 `Person` 範例中，會 `other` 先在方法中檢查傳遞至複製函式的物件是否為 null `PassThroughNonNull` 。

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
