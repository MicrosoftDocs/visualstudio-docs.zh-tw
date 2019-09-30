---
title: CA1601:不要使用會妨礙電源狀態變更的計時器
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1300b733cbd4808359089787ceebeb0750de6723
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234350"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601:不要使用會妨礙電源狀態變更的計時器

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|分類|Microsoft.Mobility|
|重大變更|中斷|

## <a name="cause"></a>原因
計時器的間隔設定為每秒發生一次以上。

## <a name="rule-description"></a>規則描述
不要每秒輪詢一次以上，或使用每秒發生頻率超過一次的計時器。 更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。

## <a name="how-to-fix-violations"></a>如何修正違規
將計時器間隔設定為每秒不到一次。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
只有在每秒引發計時器超過一次，而且可以安全地忽略行動性考慮時，才應該抑制此規則。