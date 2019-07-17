---
title: CA1719:參數名稱不應該和成員名稱相符 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: daaa856ccbc5915bcaad937a504ea2600a089c1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189094"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719:參數名稱不應該和成員名稱相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見成員的名稱中不區分大小寫的比較，其中一個參數的名稱比對。

## <a name="rule-description"></a>規則描述
 參數名稱應該要能傳達參數的意義，而成員名稱應該要能傳達成員的意義。 兩者相同屬罕見的設計。 如果將參數命名為與成員名稱相同的名稱，則不僅會不容易了解，也會讓程式庫難以使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 選取的成員名稱不相符的參數名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 新的開發，沒有已知的情況下會發生您必須在其中隱藏此規則的警告。 針對隨附的程式庫，您可能必須隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708:識別項應該不僅為大小寫不同](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707:識別項不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
