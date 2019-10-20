---
title: CA1821 必須：移除空的完成項 |Microsoft Docs
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
ms.openlocfilehash: 3d340d69ee32de20142abf740f7fedc871c9733a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657480"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821：必須移除空的完成項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 型別會實作為空的完成項、只呼叫基底類型完成項，或只呼叫有條件發出的方法。

## <a name="rule-description"></a>規則描述
 請盡可能避免使用完成項，因為追蹤物件存留期 (Lifetime) 時將會產生額外的效能負荷。 垃圾收集行程會在收集物件之前執行完成項。 這表示會需要兩個集合來收集物件。 空的完成項會產生這項額外的負擔，而不會有任何好處。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除空的完成項。 如果要進行偵錯工具需要完成項，請在 `#if DEBUG / #endif` 指示詞中括住整個完成項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則中的訊息。 無法抑制完成會降低效能，且不提供任何好處。

## <a name="example"></a>範例
 下列範例顯示應移除的空完成項、應以 `#if DEBUG / #endif` 指示詞括住的完成項，以及正確使用 `#if DEBUG / #endif` 指示詞的完成項。

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
