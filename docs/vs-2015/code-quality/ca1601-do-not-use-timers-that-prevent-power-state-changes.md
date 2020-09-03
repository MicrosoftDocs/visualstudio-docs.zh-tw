---
title: CA1601：不使用妨礙電源狀態變更的計時器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7928b2fff8c12ca3f0cc3c58bee31fe5809517e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545635"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601:不要使用會妨礙電源狀態變更的計時器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|類別|Microsoft 行動性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 計時器的間隔設定為每秒發生一次以上。

## <a name="rule-description"></a>規則描述
 請勿每秒輪詢一次以上，或使用每秒出現頻率超過一次的計時器。 更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。

## <a name="how-to-fix-violations"></a>如何修正違規
 將計時器間隔設定為每秒發生不到一次。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在每秒引發一次以上的計時器時，才需要隱藏此規則，而且可以安全地忽略行動性考慮。
