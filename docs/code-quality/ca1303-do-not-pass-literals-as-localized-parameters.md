---
title: CA1303:不要將常值當作已當地語系化的參數傳遞
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2700dc2ade7ba901f15f67045e3170e2bbb40ff8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235120"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303:不要將常值當作已當地語系化的參數傳遞

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|分類|Microsoft.Globalization|
|重大變更|不中斷|

## <a name="cause"></a>原因

方法會將字串常值當做參數傳遞至 .NET 的函式或方法，而且該字串應該是可當地語系化的。

將常值字串當做值傳遞給參數或屬性，而且有一或多個下列情況成立時，就會引發這個警告：

- 參數或屬性的屬性設定為true。<xref:System.ComponentModel.LocalizableAttribute>

- 參數或屬性名稱包含 "Text"、"Message" 或 "Caption"。

- 傳遞至主控台的字串參數名稱。 Write 或 Console。 WriteLine 方法可以是 "value" 或 "format"。

## <a name="rule-description"></a>規則描述

內嵌在原始程式碼中的字串常值很容易當地語系化。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將字串常值取代為透過類別的實例所<xref:System.Resources.ResourceManager>抓取的字串。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果程式碼程式庫不會當地語系化，或字串未向使用者或使用程式碼程式庫的開發人員公開，則可以放心地隱藏此規則的警告。

使用者可以藉由重新具名引數或屬性，或將這些專案標記為條件，來消除不應傳遞當地語系化字串之方法的干擾。

## <a name="example"></a>範例

下列範例顯示當兩個引數的其中一個超出範圍時，會擲回例外狀況的方法。 對於第一個引數，例外狀況的函式會傳遞常值字串，這會違反此規則。 若為第二個引數，則會正確傳遞透過<xref:System.Resources.ResourceManager>取得的字串。

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>另請參閱

- [桌面應用程式中的資源](/dotnet/framework/resources/index)