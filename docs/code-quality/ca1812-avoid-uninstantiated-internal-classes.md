---
title: "CA1812： 避免使用未執行個體化的內部類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f6344b5dca6df21cba4d9a747925a24fffe1025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812：避免使用未執行個體化的內部類別
|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|CheckId|CA1812|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 組件層級類型的執行個體不是由組件中的程式碼所建立。  
  
## <a name="rule-description"></a>規則描述  
 此規則會找出呼叫其中一種類型的建構函式，並報告違規情形，如果不找到任何呼叫。  
  
 此規則不會檢查下列類型：  
  
-   值類型  
  
-   抽象類型  
  
-   列舉  
  
-   委派  
  
-   編譯器會發出陣列類型  
  
-   類型，無法具現化，並且定義`static`(`Shared`在 Visual Basic 中) 只方法。  
  
 如果您套用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>正在分析之組件，此規則不會在任何建構函式標示為`internal`因為您無法分辨欄位是否正由另一個`friend`組件。  
  
 即使無法解決這項限制中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]程式碼分析，外部的獨立 FxCop 如果會發生在內部的建構函式每個`friend`組件存在於分析。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，移除型別或加入程式碼與使用它。 如果型別僅包含靜態方法，請將下列其中一種加入至要防止編譯器發出的預設公用執行個體建構函式的類型：  
  
-   私用建構函式的類型為目標[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]1.0 和 1.1 版。  
  
-   `static` (`Shared`在 Visual Basic 中) 修飾詞的類型為目標[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告。 我們建議您隱藏這個警告，在下列情況：  
  
-   這類的類別建立透過晚期繫結的反映方法<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>。  
  
-   執行階段所自動建立類別或[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。 例如，類別可實作<xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName>或<xref:System.Web.IHttpHandler?displayProperty=fullName>。  
  
-   類別會當做具有新的條件約束的泛型型別參數傳遞。 例如，下列範例將會引發此規則。  
  
    ```csharp  
    internal class MyClass  
    {     
        public DoSomething()     
        {  
        }  
    }   
    public class MyGeneric<T> where T : new()  
    {  
        public T Create()  
        {  
            return new T();     
        }  
    }  
    // [...]   
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();  
    mc.Create();  
    ```  
  
 在這些情況下，我們建議您隱藏這個警告。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801：必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)