---
title: CA1303:不要將常值當作已當地語系化的參數傳遞
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 7ca26a7c0a11915f1f68fab2ec4a6e4b3268f349
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043345"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303:不要將常值當作已當地語系化的參數傳遞

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|分類|Microsoft.Globalization|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法將字串常值做為參數的建構函式或.NET Framework 類別庫中的方法，該字串應該是可當地語系化。

 字串常值當做值傳遞至參數或屬性，且在一或多個下列情況下，則為 true 時，會引發此警告：

- <xref:System.ComponentModel.LocalizableAttribute>參數或屬性的屬性設定為 true。

- 參數或屬性名稱中包含 「 文字 」、 「 訊息 」，或 「 標題 」。

- 「 值 」 或"format"字串參數傳遞至 Console.Write 或 Console.WriteLine 方法的名稱。

## <a name="rule-description"></a>規則描述
 內嵌在原始程式碼中的字串常值很難進行當地語系化。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，取代字串常值字串的執行個體透過擷取<xref:System.Resources.ResourceManager>類別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全的程式碼程式庫不會當地語系化，則字串不會公開給使用者或使用程式碼程式庫的開發人員隱藏此規則的警告。

 使用者可以排除，應該不會被傳送當地語系化的字串重新命名的參數或屬性名稱，或標示為條件的這些項目方法的干擾。

## <a name="example"></a>範例
 下列範例會示範當任一其兩個引數超出範圍時，會擲回例外狀況的方法。 第一個引數，例外狀況的建構函式會違反此規則的常值字串。 第二個引數，建構函式會正確傳遞字串，透過擷取<xref:System.Resources.ResourceManager>。

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>另請參閱
 [桌面應用程式中的資源](/dotnet/framework/resources/index)