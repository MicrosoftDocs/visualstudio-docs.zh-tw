---
title: CA1305：指定 IFormatProvider |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 025d76f8e946dd3021141d6736c6b4bd40d57170
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539082"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305:必須指定 IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|類別|Microsoft。全球化|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法或函式會呼叫一或多個具有接受參數之多載的成員 <xref:System.IFormatProvider?displayProperty=fullName> ，而且方法或函式不會呼叫接受參數的多載 <xref:System.IFormatProvider> 。 這項規則會忽略 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 記錄為忽略參數之方法的呼叫 <xref:System.IFormatProvider> ，以及下列方法：

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 <xref:System.Globalization.CultureInfo?displayProperty=fullName> <xref:System.IFormatProvider> 未提供或物件時，多載成員所提供的預設值可能不會在所有地區設定中有您想要的效果。 此外， [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 成員會根據可能對程式碼不正確的假設，選擇預設文化特性和格式。 為了確定程式碼在您的案例中如預期般運作，您應該根據下列指導方針提供文化特性特定的資訊：

- 如果將顯示值給使用者，請使用目前的文化特性。 請參閱 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>。

- 如果值將由軟體 (儲存和存取保存到檔案或資料庫) ，請使用不因文化特性而異。 請參閱 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。

- 如果您不知道值的目的地，請讓資料取用者或提供者指定文化特性。

  請注意， <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 只能使用類別的實例來取出當地語系化的資源 <xref:System.Resources.ResourceManager?displayProperty=fullName> 。

  即使多載成員的預設行為符合您的需求，最好還是明確地呼叫文化特性特定的多載，讓您的程式碼可以自我記錄且更容易維護。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用接受或的多載， <xref:System.Globalization.CultureInfo> <xref:System.IFormatProvider> 並根據稍早所列的指導方針來指定引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您確定預設的文化特性/格式提供者是正確的選擇，而且程式碼可維護性不是重要的開發優先順序時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中， `BadMethod` 會造成這項規則有兩個違規。 `GoodMethod` 藉由將不因文化特性的文化特性傳遞給，以修正第一個違規 <xref:System.String.Compare%2A> ，並藉由將目前的文化特性傳遞給，以修正第二個違規， <xref:System.String.ToLower%2A> 因為 `string3` 會向使用者

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>範例
 下列範例會顯示目前文化特性對類型所選取之預設值的影響 <xref:System.IFormatProvider> <xref:System.DateTime> 。

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 此範例會產生下列輸出。

 **6/4/1900 12:15:12 PM** 
**06/04/1900 12:15:12**
## <a name="related-rules"></a>相關規則
 [CA1304:必須指定 CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>另請參閱
 [筆尖：使用 CultureInfo 類別](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
