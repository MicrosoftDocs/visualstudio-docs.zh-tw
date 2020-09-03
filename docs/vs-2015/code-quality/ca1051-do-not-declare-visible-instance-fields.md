---
title: CA1051：不要宣告可見的實例欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 076ce3858774d44e2d6c4c25205ced74b7a41bf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539759"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051:不要宣告可見的執行個體欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型具有外部可見的實例欄位。

## <a name="rule-description"></a>規則描述
 欄位的主要用法應該是當做實作詳細資料。 欄位應該是 `private` 或 `internal` ，而且應該使用屬性來公開。 存取欄位就像存取欄位一樣簡單，而且屬性存取子中的程式碼可以在不導入重大變更的情況下擴充的功能。 只傳回私用或內部欄位值的屬性已優化，可在等同于存取欄位時執行：使用外部可見的欄位來取代屬性，幾乎沒有足夠的效能提升。

 外部可見參考 `public` 、和 `protected` `protected internal` (`Public` 、 `Protected` 和 `Protected Friend` 在 Visual Basic) 存取層級中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請 `private` 使用外部可見屬性來讓欄位或加以 `internal` 公開。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 外部可見的欄位不會提供屬性無法使用的任何優點。 此外，公用欄位無法受到 [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)保護。 請參閱 [CA2112：安全類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。

## <a name="example"></a>範例
 下列範例顯示 `BadPublicInstanceFields` 違反此規則 () 類型。 `GoodPublicInstanceFields` 顯示已更正的程式碼。

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2112:受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>另請參閱
 [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
