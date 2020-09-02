---
title: CA1307：指定 StringComparison |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538914"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307:必須指定 StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|類別|Microsoft。全球化|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 字串比較作業使用未設定參數的方法多載 <xref:System.StringComparison> 。

## <a name="rule-description"></a>規則描述
 許多字串作業（最重要的 <xref:System.String.Compare%2A> 和 <xref:System.String.Equals%2A> 方法）都會提供接受 <xref:System.StringComparison> 列舉值做為參數的多載。

 每當有接受參數的多載存在時 <xref:System.StringComparison> ，就應該使用它，而不是未採用此參數的多載。 藉由明確設定此參數，您的程式碼通常更清楚且更容易維護。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將字串比較方法變更為接受 <xref:System.StringComparison> 列舉作為參數的多載。 例如：變更 `String.Compare(str1, str2)` 為 `String.Compare(str1, str2, StringComparison.Ordinal)` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當程式庫或應用程式適用于有限的本機物件，因此不會進行當地語系化時，可放心隱藏此規則的警告。

## <a name="see-also"></a>另請參閱
 [全球化警告](../code-quality/globalization-warnings.md) [CA1309：使用序數 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)
