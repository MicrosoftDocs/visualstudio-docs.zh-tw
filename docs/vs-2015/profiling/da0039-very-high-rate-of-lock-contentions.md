---
title: DA0039：非常高比率的鎖定爭用 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5b994e14dc63d9fabe0c02b70f5df584c03067e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752405"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039：鎖定爭用的比率非常高
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 的最新文件，請參閱[DA0039:非常高比率的鎖定爭用](https://docs.microsoft.com/visualstudio/profiling/da0039-very-high-rate-of-lock-contentions)docs.microsoft.com 上。  
  
|||  
|-|-|  
|規則 ID|DA0039|  
|分類|.NET Framework 使用方式|  
|分析方法|取樣<br /><br /> 測試設備<br /><br /> .NET 記憶體|  
|訊息|發生非常高比率的 .NET 鎖定爭用。 請執行並行分析來調查此鎖定爭用的原因。|  
|規則型別|警告|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 25 個樣本才能觸發此規則。  
  
## <a name="cause"></a>原因  
 分析資料收集的系統效能資料指出，應用程式執行期間發生過高的鎖定爭用率。 請考慮使用並行分析方法再次進行分析，以尋找爭用的原因。  
  
## <a name="rule-description"></a>規則描述  
 鎖定是用來保護多執行緒應用程式中必須一次由一個執行緒依序執行的重要程式碼區段。 Microsoft .NET 通用語言執行平台 (CLR) 提供一組完整的同步處理和鎖定原始物件。 例如，C# 語言支援鎖定陳述式 (在 Visual Basic 中為 SyncLock)。 Managed 應用程式可以呼叫 System.Threading 命名空間中的 Monitor.Enter 和 Monitor.Exit 方法來直接取得及釋放鎖定。 .NET Framework 支援額外的同步處理和鎖定原始物件，包括支援 Mutexes、ReaderWriterLocks 和 Semaphores 的類別。 如需詳細資訊，請參閱 MSDN 網站上《.NET Framework 開發人員手冊》中的[同步處理原始物件概觀](http://go.microsoft.com/fwlink/?LinkId=177867)。 .NET Framework 類別本身是位於 Windows 作業系統內建之較低層級的同步處理服務之上。 這些類別包括重要區段物件以及許多不同的 Wait 和事件發送訊號函式。 如需詳細資訊，請參閱 MSDN Library 中＜Win32 和 COM 程式開發＞的[同步處理 (英文)](http://go.microsoft.com/fwlink/?LinkId=177869) 一節。  
  
 用來同步處理和鎖定的基礎 .NET Framework 類別和原生 Windows 物件兩者都是必須使用連鎖作業變更的共用記憶體位置。 連鎖作業使用硬體特定的指令在共用的記憶體位置中運作，使用不可部分完成的作業變更其狀態。 不可部分完成的作業在機器中的所有處理器則保證一致。 Locks 和 WaitHandles 是當設定或重設時會自動使用連鎖作業的 .NET 物件。 您的應用程式中可能有其他共用的記憶體資料結構，也會要求您使用連鎖作業以安全執行緒的方式進行更新。 如需詳細資訊，請參閱 MSND Library 的＜.NET Framework＞一節中的[連鎖作業](http://go.microsoft.com/fwlink/?LinkId=177870)。  
  
 同步處理和鎖定是用來確保多執行緒應用程式正確執行的機制。 多執行緒應用程式的每個執行緒都是由作業系統獨立安排的獨立執行單位。 每當嘗試取得鎖定的執行緒因為另一個執行緒正保留鎖定而延遲，就會發生鎖定爭用的情況。  
  
 鎖定經常會成巢狀結構。 當執行重要區段的執行緒執行一個當時需要另一個鎖定的函式，就會發生巢狀情形。 一定程度的鎖定巢狀結構是不可避免的。 您的重要區段可能會呼叫依賴鎖定的 .NET Framework 方法，以確保它是安全執行緒。 從應用程式中的一些重要區段呼叫也使用不同鎖定控制代碼鎖定的 Framework 方法會造成鎖定巢狀。 巢狀鎖定條件可能會導致很難解決並修正的效能問題。  
  
 在分析執行期間所做的測量指出有非常大量的鎖定爭用時，就會引發這個規則。 鎖定爭用會延遲等待鎖定的執行緒執行。 即使是在較低階的硬體上執行的單元測試或負載測試中相當少量的鎖定爭用也還是應該進行調查。  
  
> [!NOTE]
>  當分析資料中報告的鎖定爭用比率很高但不是極高時，會引發 [DA0038︰高比率的鎖定爭用](../profiling/da0038-high-rate-of-lock-contentions.md)資訊訊息而不是此警告訊息。  
  
## <a name="how-to-investigate-a-warning"></a>如何調查警告  
 按兩下訊息，瀏覽至分析資料的[標記檢視](../profiling/marks-view.md)。  尋找 **.NET CLR LocksAndThreads\Contention Rate / sec** 欄。 判斷是否有特定的程式執行階段，當中的鎖定爭用比其他階段更繁重。  
  
 只有當您不使用並行分析方法時，才會引發此規則。 並行分析方法是用來診斷應用程式中與鎖定爭用相關效能問題的最佳工具。 收集並行分析資料可了解應用程式的鎖定行為。 這包括了解哪些鎖定嚴重爭用、執行緒執行時間因為等候爭用的鎖定而延遲多久，以及哪些特定的程式碼有關係。 並行分析會收集所有鎖定爭用的資料，包括原生 Windows 功能的鎖定行為、.NET Framework 類別以及應用程式參考的其他協力廠商程式庫。 如需從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 進行並行分析的相關資訊，請參閱[收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)。 如需從命令列進行並行分析的相關資訊連結，請參閱[從命令列使用分析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)的＜使用並行方法收集資源爭用和執行緒活動資料＞一節。
