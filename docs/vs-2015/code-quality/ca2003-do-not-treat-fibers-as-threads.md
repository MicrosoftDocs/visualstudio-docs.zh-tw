---
title: CA2003： 不要將 fiber 視為執行緒 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6563537df74d9e392bad8c4f6ce28c85b8441546
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588488"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003：不要將 Fiber 視為執行緒
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2003： 不要將 fiber 視為執行緒](https://docs.microsoft.com/visualstudio/code-quality/ca2003-do-not-treat-fibers-as-threads)。

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|分類|Microsoft.Reliability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 Managed 的執行緒會被視為 Win32 執行緒。

## <a name="rule-description"></a>規則描述
 請勿假設 managed 的執行緒是 Win32 執行緒。 它是 fiber。 Common language runtime (CLR) 會以 fiber 的 SQL 所擁有的實際執行緒內容中執行的 managed 的執行緒。 這些執行緒可以共用跨 Appdomain 和甚至是資料庫，在 SQL Server 處理序。 使用受管理的執行緒本機儲存體仍可運作，但您不可能使用 unmanaged 的執行緒區域儲存區，或假設程式碼會再次執行目前的 OS 執行緒上。 不會變更設定，例如執行緒的地區設定。 請勿呼叫 CreateCriticalSection 或 CreateMutex 經由 P/Invoke，因為它們需要進入鎖定的執行緒必須一併結束鎖定。 當您在使用 fiber，這不會是大小寫，因為 Win32 關鍵區段和 mutex 將會在 SQL。 您可能安全地使用大部分狀態，受管理的 System.Thread 物件上。 這包括受控的執行緒區域儲存區和執行緒的目前使用者介面 (UI) 文化特性。 不過，基於程式設計模型考量，您將無法變更目前執行緒文化特性，當您使用 SQL;這會透過新的權限來強制執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢查您的執行緒之使用量，並據以變更您的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您不應該隱藏此規則。



