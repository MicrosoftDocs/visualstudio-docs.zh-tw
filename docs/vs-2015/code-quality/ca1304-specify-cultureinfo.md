---
title: CA1304：指定 CultureInfo |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 202f3759026bbedd5e99e94bba76e956b83357b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661462"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304：指定 CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|分類|Microsoft。全球化|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 方法或函式會呼叫具有多載的成員，而此多載會接受 <xref:System.Globalization.CultureInfo?displayProperty=fullName> 參數，而且方法或函式不會呼叫接受 <xref:System.Globalization.CultureInfo> 參數的多載。 此規則會忽略下列方法的呼叫：

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 未提供 <xref:System.Globalization.CultureInfo> 或 <xref:System.IFormatProvider?displayProperty=fullName> 物件時，多載成員所提供的預設值可能不會有您在所有地區設定中想要的效果。 此外，[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 成員根據可能對程式碼不正確的假設，選擇預設的文化特性和格式。 若要確保程式碼在您的案例中如預期般運作，您應該根據下列指導方針提供特定文化特性的資訊：

- 如果值將顯示給使用者，請使用目前的文化特性。 請參閱<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- 如果值將由軟體儲存及存取，亦即保存到檔案或資料庫中，請使用不因文化特性而異。 請參閱<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- 如果您不知道值的目的地，請讓資料取用者或提供者指定文化特性。

  請注意，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 僅用於使用 <xref:System.Resources.ResourceManager?displayProperty=fullName> 類別的實例來取得當地語系化的資源。

  即使多載成員的預設行為適合您的需求，最好還是明確地呼叫文化特性特定的多載，讓您的程式碼可以自我記錄並更容易維護。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請使用接受 <xref:System.Globalization.CultureInfo> 或 <xref:System.IFormatProvider> 的多載，並根據先前所列的指導方針指定引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您確定預設的文化特性/格式提供者是正確的選擇，而且程式碼維護性不是重要的開發優先順序時，就可以放心地隱藏這項規則的警告。

## <a name="example"></a>範例
 在下列範例中，`BadMethod` 會造成這項規則的兩個違規。 `GoodMethod` 藉由將不因文化特性而傳遞至 System.string 來更正第一個違規，請將目前的文化特性傳遞給 <xref:System.String.ToLower%2A>，以更正第二個違規，因為 `string3` 會向使用者顯示。

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>範例
 下列範例顯示 <xref:System.DateTime> 類型選取之預設 <xref:System.IFormatProvider> 上目前文化特性的效果。

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 此範例會產生下列輸出。

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>相關規則
 [CA1305：指定 IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>另請參閱
 [筆尖：使用 CultureInfo 類別](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
