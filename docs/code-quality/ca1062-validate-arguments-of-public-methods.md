---
title: "CA1062：驗證公用方法的引數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062：驗證公用方法的引數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|分類|Microsoft.Design|  
|中斷變更|不中斷|  
  
## 原因  
 外部可見的方法會取它其中一個參考引數的值，而不驗證該引數是否是 `null` \(在 Visual Basic 中是 `Nothing`\)。  
  
## 規則描述  
 應根據 `null` 檢查所有傳遞至外部可見方法的所有參考引數。  如果適當，會在引數為 `null` 時擲回 <xref:System.ArgumentNullException>。  
  
 如果可從未知的組件呼叫方法 \(因為該方法已宣告為公用或保護\)，您應該驗證該方法的所有參數。  如果方法的設計僅供已知組件呼叫，您應將方法設為內部，並將 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性套用至包含方法的組件。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請根據 `null` 驗證每個參考引數。  
  
## 隱藏警告的時機  
 如果您確定函式中的另一個方法呼叫已經驗證過解除參考的參數，就可以隱藏這個規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的方法和滿足規則的方法。  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## 範例  
 在 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] 中，這個規則不會偵測傳遞至另一個會執行驗證之方法的參數。  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## 範例  
 複製填入欄位的建構函式或參考物件的屬性，也可能會違反 CA1062 規則。  發生違規的原因是傳遞至複製建構函式的複製物件可能是 `null` \(在 Visual Basic 中為`Nothing`\)。  若要解決違規情形，請使用靜態 \(在 Visual Basic 中為共用\) 方法，檢查複製的物件是否為 Null。  
  
 在下列 `Person` 類別範例中，傳遞至`Person` 複製建構函式的 `other` 物件可能是 `null`。  
  
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
  
## 範例  
 在下列範例已修訂的 `Person` 範例中，會先在傳遞至複製建構函式的 `other` 物件中尋找 `PassThroughNonNull` 方法中的 Null。  
  
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