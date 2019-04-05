---
title: CA2004:移除對 GC 的呼叫。KeepAlive |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e75ab22212945e5a6b4465e1e1f64ca48a9daa4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941163"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004:必須移除對 GC.KeepAlive 的呼叫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|分類|Microsoft.Reliability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 類別會使用`SafeHandle`但仍會包含呼叫`GC.KeepAlive`。

## <a name="rule-description"></a>規則描述
 如果您要將它轉換成`SafeHandle`使用方式，移除所有呼叫`GC.KeepAlive`（物件）。 在此情況下，類別應該不需要呼叫`GC.KeepAlive`，假設它們沒有完成項但依賴`SafeHandle`完成作業系統控制代碼。  雖然呼叫中保留的成本`GC.KeepAlive`可能不明顯所認知的效能測量，呼叫`GC.KeepAlive`是必要的或足以解決可能不再存在的問題，會讓程式碼更難的存留期維護。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除對呼叫`GC.KeepAlive`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有不是要轉換成正確的技術上來說，您可以隱藏這個警告`SafeHandle`類別中的使用方式。
