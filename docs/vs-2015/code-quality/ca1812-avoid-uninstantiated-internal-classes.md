---
title: CA1812：避免未具現化的內部類別 |Microsoft Docs
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
ms.openlocfilehash: 401fbfbccfeeeeec5cbdc0e791b110d1b5f0201b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543971"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812:避免使用未執行個體化的內部類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|類別|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 組件層級類型的執行個體不是由組件中的程式碼所建立。

## <a name="rule-description"></a>規則描述
 此規則會嘗試找出呼叫類型的其中一個函式，並在找不到任何呼叫時報告違規。

 此規則不會檢查下列類型：

- 實值型別

- 抽象類別型

- 列舉

- 委派

- 編譯器發出的陣列類型

- 無法具現化且 `static` 只定義（ `Shared` 在 Visual Basic 中）方法的類型。

  如果您將套用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> 至要分析的元件，此規則就不會發生在標示為的任何函式上， `internal` 因為您無法判斷某個欄位是否由另一個 `friend` 元件所使用。

  雖然您無法在程式碼分析中解決這項限制 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，但如果分析中有每個元件，則會在內部的函式上發生外部獨立 FxCop `friend` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除類型或新增使用它的程式碼。 如果類型只包含靜態方法，請將下列其中一項加入至類型，以防止編譯器發出預設公用實例的函式：

- 以版本1.0 和1.1 為目標之類型的私用函數 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

- 以 `static` `Shared` 為目標之類型的（在 Visual Basic）修飾詞 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告。 我們建議您在下列情況下隱藏此警告：

- 類別是透過晚期繫結的反映方法（例如）所建立 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> 。

- 類別會由執行時間或自動建立 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 。 例如，會執行或的 <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> 類別 <xref:System.Web.IHttpHandler?displayProperty=fullName> 。

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
 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801:必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804:必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)
