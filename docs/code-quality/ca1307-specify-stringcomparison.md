---
title: CA1307:必須指定 StringComparison
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e352eea1b7fcf82cb948315affeae6e30690a4aa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234978"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307:必須指定 StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|分類|Microsoft.Globalization|
|重大變更|不中斷|

## <a name="cause"></a>原因
字串比較作業會使用未設定<xref:System.StringComparison>參數的方法多載。

## <a name="rule-description"></a>規則描述
許多字串作業（最重要的<xref:System.String.Compare%2A>和<xref:System.String.Equals%2A>方法）都會提供<xref:System.StringComparison>可接受列舉值做為參數的多載。

每當具有<xref:System.StringComparison>參數的多載存在時，就應該使用它，而不是採用此參數的多載。 藉由明確地設定此參數，您的程式碼通常會變得更清楚且更容易維護。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請將字串比較方法變更為接受<xref:System.StringComparison>列舉做為參數的多載。 例如：將變更`String.Compare(str1, str2)`為`String.Compare(str1, str2, StringComparison.Ordinal)`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
當程式庫或應用程式適用于有限的本機物件，因此不會進行當地語系化時，可以安全地隱藏此規則的警告。

## <a name="see-also"></a>另請參閱

- [全球化警告](../code-quality/globalization-warnings.md)
- [CA1309使用序數 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)