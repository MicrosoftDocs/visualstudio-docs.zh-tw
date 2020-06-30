---
title: CA1303：不要將常值當做當地語系化參數傳遞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ad1f56215d002c03d346b38ce6155e8df7412b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539109"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303:不要將常值當作已當地語系化的參數傳遞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|類別|Microsoft。全球化|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法會將字串常值當做參數傳遞至類別庫中的函式或方法 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ，而且該字串應該是可當地語系化的。

 將常值字串當做值傳遞給參數或屬性，而且有一或多個下列情況成立時，就會引發這個警告：

- <xref:System.ComponentModel.LocalizableAttribute>參數或屬性的屬性設定為 true。

- 參數或屬性名稱包含 "Text"、"Message" 或 "Caption"。

- 傳遞至主控台的字串參數名稱。 Write 或 Console。 WriteLine 方法可以是 "value" 或 "format"。

## <a name="rule-description"></a>規則描述
 內嵌在原始程式碼中的字串常值很容易當地語系化。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將字串常值取代為透過類別的實例所抓取的字串 <xref:System.Resources.ResourceManager> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果程式碼程式庫不會當地語系化，或字串未向使用者或使用程式碼程式庫的開發人員公開，則可以放心地隱藏此規則的警告。

 使用者可以透過重新命名名為的參數或屬性，或將這些專案標記為條件式，來消除不應傳遞當地語系化字串的方法。

## <a name="example"></a>範例
 下列範例顯示當兩個引數的其中一個超出範圍時，會擲回例外狀況的方法。 對於第一個引數，例外狀況的函式會傳遞常值字串，這會違反此規則。 若為第二個引數，則會正確傳遞透過取得的字串 <xref:System.Resources.ResourceManager> 。

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>另請參閱
 [桌面應用程式中的資源](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
