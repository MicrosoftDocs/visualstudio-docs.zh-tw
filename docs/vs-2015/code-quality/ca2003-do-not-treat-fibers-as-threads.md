---
title: CA2003：不要將纖維視為執行緒 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a8172490b267949686dd3390c85ed6d86531b192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521170"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003:不要將 Fiber 視為執行緒
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|類別|Microsoft 可靠性|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 Managed 執行緒被視為 Win32 執行緒。

## <a name="rule-description"></a>規則描述
 請勿假設 managed 執行緒是 Win32 執行緒。 它是光纖。 Common language runtime (CLR) 將會在 SQL 所擁有的真實執行緒內容中，以纖程的形式執行 managed 執行緒。 這些執行緒可以在 Appdomain 之間共用，甚至是在 SQL Server 進程中的資料庫之間共用。 使用 managed 執行緒本機儲存體將可運作，但您可能不會使用非受控執行緒區域儲存區，或假設您的程式碼會再次在目前的 OS 執行緒上執行。 請勿變更設定，例如執行緒的地區設定。 請勿透過 P/Invoke 呼叫 CreateCriticalSection 或 CreateMutex，因為必須要有進入鎖定的執行緒也必須離開鎖定。 因為當您使用纖維時，不會發生這種情況，因此 Win32 重要區段和 mutex 在 SQL 中將毫無用處。 您可以安全地在 managed 系統上使用大部分的狀態。 Thread 物件。 這包括 managed 執行緒區域儲存區，以及執行緒的目前使用者介面 (UI) 文化特性。 不過，基於程式設計模型的原因，您將無法在使用 SQL 時變更執行緒的目前文化特性;這會透過新的許可權強制執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢查執行緒的使用情形，並據以變更您的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您不應該隱藏此規則。
