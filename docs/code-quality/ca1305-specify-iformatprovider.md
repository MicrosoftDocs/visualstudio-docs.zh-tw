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
ms.openlocfilehash: b96ca08b51bb5145357ef921bde753e133062203
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868004"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305:必須指定 IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|分類|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因

方法或建構函式會呼叫具有多載，接受的一或多個成員<xref:System.IFormatProvider?displayProperty=fullName>參數的方法或建構函式不會呼叫多載，<xref:System.IFormatProvider>參數。

此規則會忽略會記載為略過的.NET Framework 方法的呼叫<xref:System.IFormatProvider>參數。 此規則也會忽略下列方法：

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>規則描述

當<xref:System.Globalization.CultureInfo?displayProperty=nameWithType>或<xref:System.IFormatProvider>未提供物件，多載成員所提供的預設值可能沒有您想要以所有地區設定的效果。 此外，.NET Framework 成員選擇預設文化特性，而且格式為基礎的假設，可能不正確的程式碼。 若要確定程式碼運作如預期般運作，您的案例，您應該提供特定文化特性資訊，根據下列方針：

- 如果此值會顯示給使用者，使用目前文化特性。 請參閱 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>。

- 如果將儲存的值，且供軟體 （保存至檔案或資料庫），使用文化特性而異。 請參閱 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。

- 如果您不知道值的目的地，具有資料取用者，或提供者指定的文化特性。

即使多載成員的預設行為是適用於您的需求，最好明確呼叫的特定文化特性的多載，讓您的程式碼是自我記錄並更容易維護。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，使用採用的多載<xref:System.IFormatProvider>引數。 或者，您也可以使用[C# 字串插值](/dotnet/csharp/tutorials/string-interpolation)並將它傳遞給<xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，當您確定預設的格式是正確的選擇，以及程式碼維護性不是重要的開發優先順序。

## <a name="example"></a>範例

下列程式碼，`example1`字串違反規則 CA1305。 `example2`字串傳遞符合規則 CA1305 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>，它會實作<xref:System.IFormatProvider>至<xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>。 `example3`字串符合規則 CA1305 藉由傳遞字串插值的<xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>。

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>相關的規則

- [CA1304:指定 CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>另請參閱

- [使用 CultureInfo 類別](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)