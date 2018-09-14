---
title: CA1304：指定 CultureInfo
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: fe02dd66b523e6ee82c5e1a2051f3a68839957d4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546184"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304：指定 CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|類別|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因

方法或建構函式呼叫可接受的多載成員<xref:System.Globalization.CultureInfo?displayProperty=nameWithType>參數的方法或建構函式不會呼叫多載，<xref:System.Globalization.CultureInfo>參數。 此規則會忽略呼叫下列方法：

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>規則描述

當<xref:System.Globalization.CultureInfo>或<xref:System.IFormatProvider?displayProperty=nameWithType>未提供物件，多載成員所提供的預設值可能沒有您想要以所有地區設定的效果。 此外，.NET Framework 成員選擇預設文化特性，而且格式為基礎的假設，可能不正確的程式碼。 為了確保程式碼的運作如預期般運作，您的案例，您應該提供特定文化特性資訊，根據下列指導方針：

- 如果此值會顯示給使用者，使用目前文化特性。 請參閱 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>。

- 如果將儲存的值，且供軟體存取，也就是保存至檔案或資料庫，使用文化特性而異。 請參閱 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。

- 如果您不知道值的目的地，具有資料取用者，或提供者指定的文化特性。

即使多載成員的預設行為是適用於您的需求，最好明確呼叫的特定文化特性的多載，讓您的程式碼是自我記錄並更容易維護。

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 只能用來擷取當地語系化的資源所使用的執行個體<xref:System.Resources.ResourceManager?displayProperty=nameWithType>類別。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，使用採用的多載<xref:System.Globalization.CultureInfo>引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，當您確定預設文化特性是正確的選擇，以及程式碼維護性不是重要的開發優先順序。

## <a name="example-showing-how-to-fix-violations"></a>範例，示範如何修正違規

在下列範例中，`BadMethod`會導致兩個違反此規則。 `GoodMethod` 藉由傳遞而異的文化特性，若要修正的第一個違規<xref:System.String.Compare%2A?displayProperty=nameWithType>，並傳遞目前的文化特性，若要修正第二個違規<xref:System.String.ToLower%2A?displayProperty=nameWithType>因為`string3`顯示給使用者。

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>範例顯示如何格式化輸出

下列範例會顯示目前的文化特性的效果，使用預設<xref:System.IFormatProvider>選取的<xref:System.DateTime>型別。

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

這個範例會產生下列輸出：

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>相關的規則

- [CA1305：指定 IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>另請參閱

- [使用 CultureInfo 類別](/dotnet/standard/globalization-localization/globalization#Cultures)