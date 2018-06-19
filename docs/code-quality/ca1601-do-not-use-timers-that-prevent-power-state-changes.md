---
title: CA1601：不要使用會妨礙電源狀態變更的計時器
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 669f0ffc2e61d67bd57e965a4030b17af1eb1bb2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914584"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601：不要使用會妨礙電源狀態變更的計時器
|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|分類|Microsoft.Mobility|
|中斷變更|中斷|

## <a name="cause"></a>原因
 計時器已設定一個以上的時間，每秒的間隔。

## <a name="rule-description"></a>規則描述
 不進行輪詢頻率超過一次，每個第二個或一個以上的使用計時器以上每秒的時間。 更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。

## <a name="how-to-fix-violations"></a>如何修正違規
 設定計時器的間隔發生少於一秒的時間。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有當引發計時器每秒超過一次是必要項，而且可以放心地忽略行動力的考量應該隱藏此規則。