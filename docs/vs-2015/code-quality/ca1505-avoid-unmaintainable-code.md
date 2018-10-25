---
title: Ca1505： 應避免撰寫無法維護的程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 089a4d45c74b1849a73c99c8065f1f67ca9b0e43
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906101"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505：應避免撰寫無法維護的程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|分類|Microsoft.Maintainability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 類型或方法的維護性指標值很低。

## <a name="rule-description"></a>規則描述
 可維護性指數的計算方式是使用下列計量： 程式碼、 計劃的磁碟區和循環複雜度。 程式磁碟區是深入了解型別或方法為基礎的運算子和程式碼中的運算元數目的困難度的量值。 循環複雜度是複雜性的結構化型別或方法的量值。 您可以深入了解在程式碼度量[測量的複雜性和可維護性的 Managed 程式碼](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)。

 低維護性指數表示的型別或方法可能難以維護，而且會重新設計的良好候選項目。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規，重新設計的類型或方法，並嘗試將它分割為較小且更受關注的型別或方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當型別或方法仍視為可維護性，儘管其大小太大，或無法分割的類型或方法時，請排除這個警告。

## <a name="see-also"></a>另請參閱
 [維護性警告](../code-quality/maintainability-warnings.md)[測量的複雜度與可維護性 Managed 程式碼](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



