---
title: CA1724：類型名稱不應該和命名空間相符
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c178558743ca69fb3b62eccaf8164e4b49167ad3
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547564"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724：類型名稱不應該和命名空間相符
|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|類別|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型名稱符合[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]不區分大小寫的比較中的命名空間名稱。

## <a name="rule-description"></a>規則描述
 類型名稱不得符合 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Class Library 中定義的命名空間名稱。 違反此規則會降低程式庫的可用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 選取名稱不相符的型別名稱[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]類別程式庫命名空間。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 新的開發，沒有已知的情況下會發生您必須在其中隱藏此規則的警告。 隱藏警告之前，請仔細考慮如何將程式庫的使用者可能會比對名稱所混淆。 針對隨附的程式庫，您可能必須隱藏此規則的警告。