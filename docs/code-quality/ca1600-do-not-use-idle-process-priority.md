---
title: CA1600:不要使用 Idle 處理序優先順序
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e606850298841d1d1c77435d83dbbe12c4e55d64
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921039"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600:不要使用 Idle 處理序優先順序

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|分類|Microsoft.Mobility|
|中斷變更|中斷|

## <a name="cause"></a>原因
 處理程序設定為時，就會發生這項規則`ProcessPriorityClass.Idle`。

## <a name="rule-description"></a>規則描述
 請勿將處理序優先權設定為 Idle。 處理程序`System.Diagnostics.ProcessPriorityClass.Idle`會佔用 CPU，它會處於閒置狀態，並因而阻礙待命時。

## <a name="how-to-fix-violations"></a>如何修正違規
 設定處理程序為`ProcessPriorityClass.BelowNormal`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 閒置處理序優先權，而且可以安全地忽略行動力考量時，才應該隱藏此規則。