---
title: CA1600：不要使用閒置進程優先順序 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669288"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600：不要使用 Idle 處理序優先權
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft 的行動性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 當進程設定為 `ProcessPriorityClass.Idle` 時，就會發生此規則。

## <a name="rule-description"></a>規則描述
 請勿將處理序優先權設定為 Idle。 具有 `System.Diagnostics.ProcessPriorityClass.Idle` 的進程會在 CPU 閒置時佔用 CPU，因此會封鎖待命。

## <a name="how-to-fix-violations"></a>如何修正違規
 將進程設定為 `ProcessPriorityClass.BelowNormal`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在需要閒置進程優先順序，而且可以安全地忽略行動性考慮時，才應該抑制此規則。
