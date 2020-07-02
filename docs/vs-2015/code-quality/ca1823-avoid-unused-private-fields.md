---
title: CA1823：避免使用的私用欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 01f2ef59ceb6d10cc33276fdd3e5388f39175f8b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545297"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823:避免包含未使用的私用欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|類別|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 當程式碼中的私用欄位存在，但沒有任何程式碼路徑使用時，就會回報此規則。

## <a name="rule-description"></a>規則描述
 偵測到似乎不能在組件內存取的私用欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除欄位或加入使用它的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801:必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804:必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)
