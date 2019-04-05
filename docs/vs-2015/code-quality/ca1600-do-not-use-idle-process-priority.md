---
title: CA1600:不要使用 idle 處理序優先權 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4002e17e3988ca3b449e141394ce762f95ffc78b
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58939837"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600:不要使用 Idle 處理序優先順序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
