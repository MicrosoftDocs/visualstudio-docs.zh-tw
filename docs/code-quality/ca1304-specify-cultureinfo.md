---
title: CA1304：指定 CultureInfo
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dec38172f65b7b4d828dc96f0b2f51b28ce1ebd6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304：指定 CultureInfo
|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|分類|Microsoft.Globalization|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法或建構函式，呼叫具有可接受多載成員<xref:System.Globalization.CultureInfo?displayProperty=fullName>參數和方法或建構函式不會呼叫的多載，<xref:System.Globalization.CultureInfo>參數。 此規則會忽略呼叫下列方法：

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 當<xref:System.Globalization.CultureInfo>或<xref:System.IFormatProvider?displayProperty=fullName>未提供物件，多載成員所提供的預設值可能沒有您想要在所有地區設定的效果。 此外，[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]成員選擇預設文化特性及格式設定為基礎的假設，可能不正確的程式碼。 若要確保程式碼的運作不如預期您的案例，您應該提供根據下列指導方針的特定文化特性資訊：

-   如果此值將會顯示給使用者，使用目前文化特性。 請參閱 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>。

-   如果將儲存的值，且透過軟體，也就是保存至檔案或資料庫，使用文化特性而異。 請參閱 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。

-   如果您不知道值的目的，有資料取用者，或提供者指定的文化特性。

 請注意，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>只能用於擷取當地語系化的資源所使用的執行個體<xref:System.Resources.ResourceManager?displayProperty=fullName>類別。

 即使多載成員的預設行為是適用於您的需求，最好明確呼叫的特定文化特性的多載，讓您的程式碼是自我記錄並更容易維護。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，使用的多載，<xref:System.Globalization.CultureInfo>或<xref:System.IFormatProvider>和指定的引數，根據先前列出的指導方針。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，確定預設文化特性/格式提供者是正確的選擇，並在程式碼維護性不是重要的開發優先順序。

## <a name="example"></a>範例
 在下列範例中，`BadMethod`會導致兩個違反此規則。 `GoodMethod` 更正 System.String.Compare，來傳遞文化特性而異的第一個違規，而且藉由傳遞至目前的文化特性以修正第二個違規<xref:System.String.ToLower%2A>因為`string3`顯示給使用者。

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example"></a>範例
 下列範例會顯示目前的文化特性的效果，使用預設<xref:System.IFormatProvider>，會選取<xref:System.DateTime>型別。

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

 此範例會產生下列輸出。

 **1900 年 6 月 4 日 12:15:12 PM**
**06/04/1900年 12:15:12**
## <a name="related-rules"></a>相關的規則
 [CA1305：指定 IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>另請參閱
[使用 CultureInfo 類別](/dotnet/standard/globalization-localization/globalization#Cultures)