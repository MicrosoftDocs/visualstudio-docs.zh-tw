---
title: CA1811：避免使用未呼叫私用程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ccc439e0d84d1fced4ba0359385a6964356d5df6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668453"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811：避免使用未呼叫的私用程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Category|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 私用或內部（元件層級）成員在元件中沒有呼叫端，不是由 common language runtime 叫用，而且不是由委派叫用。 此規則不會檢查下列成員：

- 明確介面成員。

- 靜態的函式。

- 序列化的函式。

- 標記為 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 的方法。

- 覆寫的成員。

## <a name="rule-description"></a>規則描述
 如果目前未由規則邏輯識別的進入點出現，此規則可以報告錯誤的陽性。 此外，編譯器可能會發出 noncallable 程式碼到元件中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除 noncallable 程式碼或加入呼叫它的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1812：避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801：必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)
