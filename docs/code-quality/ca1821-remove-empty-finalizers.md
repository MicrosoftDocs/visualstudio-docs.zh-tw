---
title: CA1821：必須移除空的完成項
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccd6ca16dc8a4ca2ce2f2883958ed82fa1c4b3ba
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821：必須移除空的完成項
|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|分類|Microsoft.Performance|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型會實作是空的、 只基底類型完成項，會呼叫或僅有條件發出方法呼叫完成項。

## <a name="rule-description"></a>規則描述
 請盡可能避免使用完成項，因為追蹤物件存留期 (Lifetime) 時將會產生額外的效能負荷。 它會收集物件前，記憶體回收行程會執行完成項。 這表示兩個集合都需要回收物件。 空的完成項會造成這種額外負荷，而沒有任何好處。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除空的完成項。 如果需要偵錯的完成項，括住整個完成項中的`#if DEBUG / #endif`指示詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的訊息。 若要隱藏最終處理的失敗會降低效能，並不提供任何好處。

## <a name="example"></a>範例
 下列範例會顯示空白完成項應該移除、 完成項應該包含在`#if DEBUG / #endif`指示詞和使用完成項`#if DEBUG / #endif`指示詞正確。

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]