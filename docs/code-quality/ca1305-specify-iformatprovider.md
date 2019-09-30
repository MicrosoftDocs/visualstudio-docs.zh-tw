---
title: CA1305:必須指定 IFormatProvider
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a9f6c8fd44749de43d86bf8037df0130ad682321
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235039"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305:必須指定 IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|分類|Microsoft.Globalization|
|重大變更|不中斷|

## <a name="cause"></a>原因

方法或函式會呼叫具有接受<xref:System.IFormatProvider?displayProperty=fullName>參數之多載的一個或多個成員，而方法或函式不會呼叫<xref:System.IFormatProvider>採用參數的多載。

此規則會忽略已記載為忽略<xref:System.IFormatProvider>參數之 .net 方法的呼叫。 此規則也會忽略下列方法：

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>規則描述

未提供<xref:System.IFormatProvider>或物件時，多載成員所提供的預設值可能不會在所有地區設定中有您想要的效果。 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> 此外，.NET 成員也會根據可能對程式碼不正確的假設，選擇預設的文化特性和格式。 為確保程式碼在您的案例中如預期般運作，您應該根據下列指導方針提供特定文化特性的資訊：

- 如果值將顯示給使用者，請使用目前的文化特性。 請參閱 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>。

- 如果值將由軟體儲存和存取（保存到檔案或資料庫），請使用不因文化特性而異。 請參閱 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。

- 如果您不知道值的目的地，請讓資料取用者或提供者指定文化特性。

即使多載成員的預設行為適合您的需求，最好還是明確地呼叫文化特性特定的多載，讓您的程式碼可以自我記錄並更容易維護。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請使用接受<xref:System.IFormatProvider>引數的多載。 或者，使用[ C#插入字串](/dotnet/csharp/tutorials/string-interpolation)並將<xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType>它傳遞給方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

當您確定預設格式是正確的選擇，而且程式碼維護性不是重要的開發優先順序時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例

在下列程式碼中， `example1`字串違反規則 CA1305。 字串會藉由將實作為<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.IFormatProvider>，傳遞給來<xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>滿足規則 CA1305。 `example2` 字串會藉由將字串插值傳遞至，來<xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>滿足規則 CA1305。 `example3`

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>相關規則

- [CA1304:指定 CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>另請參閱

- [使用 CultureInfo 類別](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)