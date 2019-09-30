---
title: CA1719:參數名稱不應該和成員名稱相符
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aa55993758df24346b78eb4d9ad022014d9d81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233979"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719:參數名稱不應該和成員名稱相符

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|分類|Microsoft.Naming|
|重大變更|中斷|

## <a name="cause"></a>原因
外部可見成員的名稱會與它的其中一個參數的名稱相符，以不區分大小寫的比較。

## <a name="rule-description"></a>規則描述
參數名稱應該要能傳達參數的意義，而成員名稱應該要能傳達成員的意義。 兩者相同屬罕見的設計。 如果將參數命名為與成員名稱相同的名稱，則不僅會不容易了解，也會讓程式庫難以使用。

## <a name="how-to-fix-violations"></a>如何修正違規
請選取不符合成員名稱的參數名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
針對新的開發，在您必須隱藏此規則的警告的情況下，不會發生任何已知的狀況。 針對運送媒體櫃，您可能必須隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
[CA1709識別碼的大小寫應該正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708識別碼應該不同于大小寫](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707識別碼不應包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)