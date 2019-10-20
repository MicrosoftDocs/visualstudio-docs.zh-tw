---
title: CA1724：類型名稱不應該符合命名空間 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671601"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724：類型名稱不應該和命名空間相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型名稱符合不區分大小寫比較中的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 命名空間名稱。

## <a name="rule-description"></a>規則描述
 類型名稱不得符合 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Class Library 中定義的命名空間名稱。 違反此規則會降低程式庫的可用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 選取不符合 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類別庫命名空間名稱的類型名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 針對新的開發，在您必須隱藏此規則的警告的情況下，不會發生任何已知的狀況。 在您隱藏警告之前，請仔細考慮您的媒體櫃使用者可能會因為相符的名稱而感到困惑。 針對運送媒體櫃，您可能必須隱藏此規則的警告。
