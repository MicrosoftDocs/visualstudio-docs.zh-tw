---
title: CA1304：指定 CultureInfo
ms.date: 06/30/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f4726b21b51b963074ee9ae1c161872f6a5e5a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444432"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304：指定 CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|分類|Microsoft。全球化|
|重大變更|不中斷|

## <a name="cause"></a>原因

方法或函式會呼叫具有多載的成員，而此多載會接受 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> 參數，而方法或函式不會呼叫接受 <xref:System.Globalization.CultureInfo> 參數的多載。 此規則會忽略下列方法的呼叫：

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>規則描述

未提供 <xref:System.Globalization.CultureInfo> 或 @no__t 1 物件時，多載成員所提供的預設值可能不會在所有地區設定中有您想要的效果。 此外，.NET 成員也會根據可能對程式碼不正確的假設，選擇預設的文化特性和格式。 若要確保程式碼在您的案例中如預期般運作，您應該根據下列指導方針提供特定文化特性的資訊：

- 如果值將顯示給使用者，請使用目前的文化特性。 請參閱<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- 如果值將由軟體儲存及存取，亦即保存到檔案或資料庫中，請使用不因文化特性而異。 請參閱<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- 如果您不知道值的目的地，請讓資料取用者或提供者指定文化特性。

即使多載成員的預設行為適合您的需求，最好還是明確地呼叫文化特性特定的多載，讓您的程式碼可以自我記錄並更容易維護。

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 僅用於使用 <xref:System.Resources.ResourceManager?displayProperty=nameWithType> 類別的實例來取出當地語系化的資源。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請使用接受 <xref:System.Globalization.CultureInfo> 引數的多載。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

當您確定預設文化特性是正確的選擇，而且程式碼維護性不是重要的開發優先順序時，可以安全地隱藏此規則的警告。

## <a name="example-showing-how-to-fix-violations"></a>顯示如何修正違規的範例

在下列範例中，`BadMethod` 會造成這項規則的兩個違規。 `GoodMethod` 會藉由將不因文化特性（culture）傳遞給 <xref:System.String.Compare%2A?displayProperty=nameWithType> 來更正第一個違規，並藉由將目前文化特性傳遞至 <xref:System.String.ToLower%2A?displayProperty=nameWithType> 來更正第二個違規，因為會向使用者顯示 `string3`。

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>顯示格式化輸出的範例

下列範例顯示 <xref:System.DateTime> 類型所選取之預設 <xref:System.IFormatProvider> 的目前文化特性的效果。

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

這個範例會產生下列輸出：

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>相關規則

- [CA1305：指定 IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>請參閱

- [使用 CultureInfo 類別](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)
