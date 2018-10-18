---
title: CA1062： 驗證公用方法的引數 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7fd1cc9786c82a7abb5c8cca589317bae56c4b00
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221685"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062：驗證公用方法的引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見方法其中一個參考引數而不需要確認該引數是否已取值`null`(`Nothing` Visual Basic 中)。

## <a name="rule-description"></a>規則描述
 所有的參考引數傳遞至外部可見方法應針對檢查`null`。 如果適當的話，會擲回<xref:System.ArgumentNullException>引數時`null`。

 如果可以從未知的組件呼叫的方法，因為它宣告為公用或受保護，您應該驗證方法的所有參數。 如果方法設計成只能呼叫已知的組件中，您應該將方法設為內部，並套用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性包含方法的組件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，驗證每個參考引數的`null`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確定函式中的另一個方法呼叫通過已取值的參數，您可以隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則方法，並符合規則的方法。

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>範例
 在  [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]，此規則不會偵測參數，會傳遞至另一個方法，會執行驗證。

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>範例
 填入欄位或屬性所參考物件的複製建構函式也可能會違反 CA1062 規則。 因為複製的物件傳遞給複製建構函式可能會發生的違規`null`(`Nothing` Visual Basic 中)。 若要解決此違規情形，使用靜態的 (在 Visual Basic 中的是 Shared) 方法來檢查複製的物件不是 null。

 在下列`Person`類別的範例`other`物件傳遞給`Person`複製建構函式可能`null`。

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
 下列已修訂`Person`範例中，`other`物件傳遞給複製建構函式會先檢查中的 null`PassThroughNonNull`方法。

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



