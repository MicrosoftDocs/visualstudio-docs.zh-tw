---
title: CA1600:不要使用 Idle 處理序優先順序
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 686929471ee8b6b5d1896f61bcbcd97a59135462
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234371"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600:不要使用 Idle 處理序優先順序

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|分類|Microsoft.Mobility|
|重大變更|中斷|

## <a name="cause"></a>原因
當進程設定為時， `ProcessPriorityClass.Idle`就會發生此規則。

## <a name="rule-description"></a>規則描述
請勿將處理序優先權設定為 Idle。 當處理常式`System.Diagnostics.ProcessPriorityClass.Idle`會閒置時，將會佔用 CPU，因此會封鎖待命。

## <a name="how-to-fix-violations"></a>如何修正違規
將處理常式`ProcessPriorityClass.BelowNormal`設定為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
只有在需要閒置進程優先順序，而且可以安全地忽略行動性考慮時，才應該抑制此規則。