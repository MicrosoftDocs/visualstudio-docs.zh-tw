---
title: CA2003:不要將 Fiber 視為執行緒
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8faaf3c6557065188c795d75ea9bbe4e78998709
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806983"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003:不要將 Fiber 視為執行緒

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|分類|Microsoft.Reliability|
|中斷變更|非重大|

## <a name="cause"></a>原因

Managed 的執行緒會被視為 Win32 執行緒。

## <a name="rule-description"></a>規則描述

請不要假設 managed 的執行緒是 Win32 執行緒;它是 fiber。 Common language runtime (CLR) 會以 fiber 的 SQL 所擁有的實際執行緒內容中執行的 managed 的執行緒。 這些執行緒可以共用跨 Appdomain 和甚至是資料庫，在 SQL Server 處理序。 使用受管理的執行緒本機儲存體的運作方式，但您不可能使用 unmanaged 的執行緒區域儲存區，或假設程式碼會再次執行目前的 OS 執行緒上。 不會變更設定，例如執行緒的地區設定。 請勿呼叫 CreateCriticalSection 或 CreateMutex 經由 P/Invoke，因為它們需要進入鎖定的執行緒必須一併結束鎖定。 當您在使用 fiber，進入鎖定的執行緒不結束鎖定，因為 Win32 關鍵區段和 mutex 是毫無用處的 SQL。 您可能會以安全地使用大部分狀態上 managed<xref:System.Threading.Thread>物件，包括 managed 的執行緒區域儲存區和執行緒的目前使用者介面 (UI) 文化特性。 不過，基於程式設計模型考量，您無法再變更目前執行緒文化特性，當您使用 SQL。 透過新的權限，將會強制執行這項限制。

## <a name="how-to-fix-violations"></a>如何修正違規

檢查您的執行緒之使用量，並據以變更您的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這項規則。