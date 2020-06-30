---
title: CA2004 必須：移除對 GC 的呼叫。KeepAlive |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521195"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004:必須移除對 GC.KeepAlive 的呼叫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|類別|Microsoft 可靠性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 類別使用 `SafeHandle` 但仍包含對 `GC.KeepAlive` 的呼叫。

## <a name="rule-description"></a>規則描述
 如果您要轉換為 `SafeHandle` 使用方式，請移除對 `GC.KeepAlive` （object）的所有呼叫。 在此情況下，類別應該不需要呼叫 `GC.KeepAlive` ，假設它們沒有完成項，而是依賴 `SafeHandle` 來完成它們的 OS 控制碼。  雖然對的呼叫所花費的成本 `GC.KeepAlive` 可能會因效能而被忽略，但是對的呼叫 `GC.KeepAlive` 是必要或足以解決可能不再存在的存留期問題，而使得程式碼更難維護。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除對 `GC.KeepAlive` 的呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在技術上不正確，才能轉換成 `SafeHandle` 類別中的使用方式時，您才可以隱藏這個警告。
