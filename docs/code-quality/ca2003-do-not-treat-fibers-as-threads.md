---
title: "CA2003： 不要將 fiber 視為執行緒 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ca9b0649950be50dcff5103258d60f6f924f12a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003：不要將 Fiber 視為執行緒
|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|分類|Microsoft.Reliability|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 Managed 的執行緒會被視為 Win32 執行緒。  
  
## <a name="rule-description"></a>規則描述  
 請勿假設 managed 的執行緒是 Win32 執行緒。 它是 fiber。 Common language runtime (CLR) 會以 fiber 的 SQL 所擁有的實際執行緒內容中執行的 managed 的執行緒。 這些執行緒可以在 SQL Server 處理序中的跨 Appdomain 和甚至資料庫共用。 使用受管理的執行緒區域儲存區也能運作，但您可能無法使用未受管理的執行緒區域儲存區，或假設您的程式碼將會再次執行目前的作業系統執行緒上。 不會變更設定，例如執行緒的地區設定。 請勿呼叫 CreateCriticalSection 或 CreateMutex 透過 P/Invoke，因為它們需要進入鎖定的執行緒，也必須結束鎖定。 因為這不會看到當您使用 fiber，Win32 關鍵區段和 mutex 會是毫無用處的 SQL。 您安全地可能受管理的 System.Thread 物件上使用大部分的狀態。 這包括受管理的執行緒區域儲存區和執行緒的目前使用者介面 (UI) 文化特性。 不過，程式設計模型的理由，您將無法變更目前執行緒的文化特性，當您使用 SQL;這會透過新的權限來強制執行。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 檢查您的執行緒之使用量，並據以變更您的程式碼。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 您不應該隱藏此規則。