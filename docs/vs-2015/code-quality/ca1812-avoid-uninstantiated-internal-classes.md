---
title: CA1812:避免未具現化的內部類別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f5a36ee8cffc221d15243ff72e2e71558e867319
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645400"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812:避免使用未執行個體化的內部類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|分類|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 組件層級類型的執行個體不是由組件中的程式碼所建立。

## <a name="rule-description"></a>規則描述
 此規則會嘗試找出呼叫類型的其中一個函式，並在找不到任何呼叫時報告違規。

 此規則不會檢查下列類型：

- 值類型

- 抽象類別型

- 列舉

- 委派

- 編譯器發出的陣列類型

- 無法具現化且只定義 `static` （在 Visual Basic 中 `Shared`）方法的類型。

  如果您將 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> 套用至要分析的元件，此規則就不會發生在標示為 `internal` 的任何函式上，因為您無法判斷某個欄位是否由另一個 `friend` 元件所使用。

  雖然您無法在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼分析中解決這項限制，但如果分析中有每個 `friend` 元件，則會在內部的函式上發生外部獨立 FxCop。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除類型或新增使用它的程式碼。 如果類型只包含靜態方法，請將下列其中一項加入至類型，以防止編譯器發出預設公用實例的函式：

- 以 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本1.0 和1.1 為目標之類型的私用函數。

- 以 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 為目標之類型的 `static` （Visual Basic 中的 `Shared`）修飾詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告。 我們建議您在下列情況下隱藏此警告：

- 類別是透過晚期繫結反映方法（例如 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>）所建立。

- 類別會由執行時間自動建立，或 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]。 例如，執行 <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> 或 <xref:System.Web.IHttpHandler?displayProperty=fullName> 的類別。

- 類別會當做具有新條件約束的泛型型別參數傳遞。 例如，下列範例將會引發此規則。

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

  在這些情況下，建議您隱藏這個警告。

## <a name="related-rules"></a>相關規則
 [CA1811：避免使用未呼叫私用程式碼 ](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801：檢查未使用的參數 ](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804：移除未使用的區域變數 ](../code-quality/ca1804-remove-unused-locals.md)
