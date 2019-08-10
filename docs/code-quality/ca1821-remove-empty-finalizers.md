---
title: CA1821:必須移除空的完成項
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c8c4d4ca04c7a9a21cd1e80e4dc06e8d5a92c2f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921366"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821:必須移除空的完成項

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|分類|Microsoft.Performance|
|中斷變更|不中斷|

## <a name="cause"></a>原因
型別會實作為空的完成項、只呼叫基底類型完成項, 或只呼叫有條件發出的方法。

## <a name="rule-description"></a>規則描述
請盡可能避免使用完成項，因為追蹤物件存留期 (Lifetime) 時將會產生額外的效能負荷。 垃圾收集行程會在收集物件之前執行完成項。 這表示會需要兩個集合來收集物件。 空的完成項會產生這項額外的負擔, 而不會有任何好處。

## <a name="how-to-fix-violations"></a>如何修正違規
移除空的完成項。 如果要進行偵錯工具需要完成項, 請將整個完成`#if DEBUG / #endif`項括在指示詞中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則中的訊息。 無法抑制完成會降低效能, 且不提供任何好處。

## <a name="example"></a>範例
下列範例顯示應移除的空完成項、應以指示詞括住的完成項`#if DEBUG / #endif` , 以及正確`#if DEBUG / #endif`使用指示詞的完成項。

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]