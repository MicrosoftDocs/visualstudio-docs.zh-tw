---
title: CA1821 必須：移除空白的完成項 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545349"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821:必須移除空的完成項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|類別|Microsoft。效能|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別會實作為空白的完成項、只呼叫基底型別完成項，或只呼叫有條件發出的方法。

## <a name="rule-description"></a>規則描述
 請盡可能避免使用完成項，因為追蹤物件存留期 (Lifetime) 時將會產生額外的效能負荷。 垃圾收集行程會在收集物件之前執行完成項。 這表示將需要兩個集合才能收集物件。 空白完成項會產生這項額外的額外負荷，而不會有任何好處。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除空白的完成項。 如果偵錯工具需要完成項，請將整個完成項放在指示詞中 `#if DEBUG / #endif` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則中的訊息。 無法隱藏完成會降低效能，而且不提供任何好處。

## <a name="example"></a>範例
 下列範例顯示應移除的空白完成項、應包含在指示詞中的完成項 `#if DEBUG / #endif` ，以及正確使用指示詞的完成項 `#if DEBUG / #endif` 。

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
