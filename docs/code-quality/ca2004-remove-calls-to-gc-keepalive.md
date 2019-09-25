---
title: CA2004:必須移除對 GC.KeepAlive 的呼叫
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c495357b837c4ae10d4dfe1e25237d6caaefcc4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233119"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004:必須移除對 GC.KeepAlive 的呼叫

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|分類|Microsoft.Reliability|
|重大變更|不中斷|

## <a name="cause"></a>原因
類別使用`SafeHandle`但仍包含對`GC.KeepAlive`的呼叫。

## <a name="rule-description"></a>規則描述
如果您要轉換為`SafeHandle`使用方式，請移除對`GC.KeepAlive` （object）的所有呼叫。 在此情況下，類別應該不需要呼叫`GC.KeepAlive`，假設它們沒有完成項，而是`SafeHandle`依賴來完成它們的 OS 控制碼。  雖然以效能測量來進行呼叫`GC.KeepAlive`的成本可能是可忽略的，但是對的`GC.KeepAlive`呼叫是必要或足以解決可能不再存在的存留期問題，讓程式碼更難保證.

## <a name="how-to-fix-violations"></a>如何修正違規
移除對`GC.KeepAlive`的呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
只有在技術上不正確，才能轉換成`SafeHandle`類別中的使用方式時，您才可以隱藏這個警告。