---
title: 依識別碼的效能規則 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a1c934c-4798-4df9-a8ef-eb17ef06b6a2
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78e586bdc2859364097fc03bfe4a667a481680e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737798"
---
# <a name="performance-rules-by-id"></a>依 ID 排序的效能規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

警告|描述|  
|-------------|-----------------|  
|[DA0001：使用 StringBuilder 來進行串連](../profiling/da0001-use-stringbuilder-for-concatenations.md)|對 System.String.Concat 的呼叫大部分是分析資料。 請考慮使用 <xref:System.Text.StringBuilder> 類別，從多個區段建構字串。|  
|[DA0002：遺漏 VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|分析工具在分析回合期間找不到 VSPerfCorProf.dll。 如果使用收集分析工具資料的命令列工具，而未使用 VSPerfCLREnv.cmd 工具來初始化所需的環境變數，則會發生此警告。|  
|[DA0003：許多核心樣本](../profiling/da0003-many-kernel-samples.md)|針對應用程式收集的大部分呼叫堆疊範例是以核心模式執行。 請考慮使用不同的分析方法來分析應用程式。|  
|[DA0004：處理器使用率高](../profiling/da0004-high-processor-usage.md)|處理器 (CPU) 使用率在使用檢測方法所收集的分析資料中明顯偏高。 分析 CPU 繫結應用程式時，請考慮使用取樣分析方法。|  
|[DA0005：常見的 GC2 集合](../profiling/da0005-frequent-gc2-collections.md)|數量高的 .NET 記憶體物件正在層代 2 記憶體回收中收回。|  
|[DA0006：覆寫實值型別的 Equals()](../profiling/da0006-override-equals-parens-for-value-types.md)|Equals 方法呼叫或公用實值型別的相等運算子大部分是分析資料。 請考慮實作更有效率的方法。|  
|[DA0007：避免使用例外狀況進行控制流程](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|在程式碼剖析資料呼叫的 .NET Framework 例外處理常式的比率很高。 請考慮使用其他控制流程邏輯，以減少擲回的例外狀況數量。|  
|[DA0008：收集的樣本少](../profiling/da0008-few-samples-collected.md)|在分析回合中只會收集到少量樣本。 請考慮執行較長時間或較快速的取樣率，以取得較大量的結果。|  
|[DA0009：高在 JIT 時間百分比](http://msdn.microsoft.com/en-us/b60c1767-515c-41d9-81c2-c70d0b7024fd)|應用程式執行時間的大量百分比花在 Just In Time (JIT) 編譯器中。|  
|[DA0010：GetHashCode 高度耗費資源](../profiling/da0010-expensive-gethashcode.md)|類型的 GetHashCode 方法呼叫大部分是分析資料，或方法會配置記憶體。|  
|[DA0011：CompareTo 高度耗費資源](../profiling/da0011-expensive-compareto.md)|類型的 CompareTo 方法高度耗費資源，或配置記憶體。|  
|[DA0012：大量的反射](../profiling/da0012-significant-amount-of-reflection.md)|對 System.Reflection 方法 (例如 InvokeMember 和 GetMember) 或 Type 方法 (例如 MemberInvoke) 的呼叫大部分是分析資料。 可以的話，請考慮將這些方法取代為相依組件方法的早期繫結。|  
|[DA0013：String.Split 或 String.Substring 的用量高](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|呼叫 System.String.Split 或 System.String.Substring 方法大部分是分析資料。 如果您要測試某個子字串是否存在字串中，請考慮使用 System.String.IndexOf 或 System.String.IndexOfAny。|  
|[DA0014：極高比率的使用中記憶體分頁到磁碟](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|在分析執行中收集的系統效能資料表示在整個分析執行期間發生極高比率的使用中記憶體分頁進出磁碟。 此程度的分頁比率通常會影響應用程式效能和回應性。 請考慮修改演算法減少記憶體配置。 您也必須考慮應用程式的記憶體需求。 請在有較多記憶體的電腦上再次執行分析。|  
|[DA0017：高比率的使用中記憶體分頁到磁碟](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|在分析執行中收集的系統效能資料表示在整個分析執行期間發生高比率的使用中記憶體分頁進出磁碟。 此程度的分頁比率通常會影響應用程式效能和回應性。 請考慮修改演算法減少記憶體配置。 您也必須考慮應用程式的記憶體需求。 請在有較多記憶體的電腦上再次執行分析。|  
|[DA0018：32 位元應用程式正以處理序 Managed 記憶體限制執行](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|分析回合期間所收集的系統資料指出，.NET Framework 記憶體堆積已接近 Managed 堆積在 32 位元處理序中可成長的大小上限。 報告的值是已分析處理序作用中時，堆積的最大觀察值。 請考慮最佳化應用程式對 Managed 資源的使用。|  
|[DA0021：高比率的 Gen 1 記憶體回收](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|分析期間所收集的系統效能資料表示，相較於第 0 代資料回收，大部分 .NET Framework 物件的記憶體是在記憶體回收的第 1 代回收。|  
|[DA0022：高比率的 Gen 2 記憶體回收](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|分析期間所收集的系統效能資料表示，相較於第 0 代和第 1 代的記憶體回收，大部分 .NET Framework 物件的記憶體是在記憶體回收的第 2 代回收。|  
|[DA0023：高記憶體回收 CPU 時間](../profiling/da0023-high-gc-cpu-time.md)|分析期間收集的系統效能資料指出，相較於應用程式總處理時間，花費在記憶體回收的時間量極高。|  
|[DA0024：過度的記憶體回收 CPU 時間](../profiling/da0024-excessive-gc-cpu-time.md)|分析期間收集的系統效能資料指出，相較於應用程式總處理時間，花費在記憶體回收的時間量過高。|  
|[DA0026：過多核心 CPU 時間處理](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|在核心模式中執行的 CPU 時間比例超過在使用者模式中所花費的時間量。 請考慮再次分析並對系統呼叫 (syscall) 取樣來判斷高核心模式執行時間的原因。|  
|[DA0029：不支援的 CLR 版本](../profiling/da0029-unsupported-clr-version.md)|您嘗試使用分析工具不支援的 .NET Framework 1.1 版來分析應用程式。|  
|[DA0030：資料庫專案的收集階層互動度量](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|<xref:System.Data> 方法呼叫大部分是分析資料，您還不會在執行分析中收集階層互動資料。 請考慮再次進行分析，並加入階層互動資料。|  
|[DA0038：高比率的鎖定爭用](../profiling/da0038-high-rate-of-lock-contentions.md)|程式碼剖析資料收集的系統效能資料指出，應用程式執行期間發生極高的鎖定爭用率。 請考慮使用並行程式碼剖析方法再次進行程式碼剖析，以尋找爭用的原因。|  
|[DA0039：鎖定爭用的比率非常高](../profiling/da0039-very-high-rate-of-lock-contentions.md)|程式碼剖析資料收集的系統效能資料指出，應用程式執行期間發生過高的鎖定爭用率。 請考慮使用並行分析方法再次進行分析，以尋找爭用的原因。|  
|[DA0501：所分析之處理序的平均 CPU 消耗](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|此訊息報告處理器忙於執行應用程式指令的時間百分比。 報告的值是所分析的處理序作用中之所有測量間隔的平均。 在有多個處理器的電腦上，值可以大於 100%。|  
|[DA0502：所分析之處理序的最大 CPU 消耗](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|此訊息報告處理器忙於執行應用程式指令的最大時間百分比。 報告的值是在所分析的處理序作用中之所有測量間隔當中報告的最大值。 在有多個處理器的電腦上，百分比可以大於 100%。|  
|[DA0503：所分析的處理序的平均工作集 (以位元組為單位)](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|此訊息報告處理序目前使用的實體記憶體平均數量，以位元組 (工作集) 為單位。 處理序工作集表示目前位於實體記憶體中之處理序位址空間的頁面。|  
|[DA0504：所分析的處理序的最大工作集 (以位元組為單位)](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|此訊息報告處理序目前使用的實體記憶體最大數量 (以位元組為單位)。 處理序工作集表示目前位於實體記憶體中之處理序位址空間的頁面。 此規則回報分析進行時，處理序工作集的最大值。|  
|[DA0505：為所分析的處理序配置的平均私用位元組](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|此訊息報告處理序目前已配置的虛擬記憶體平均數量，以位元組 (私用位元組) 為單位。 私用位元組表示只能由處理序內執行的執行緒存取的處理序所配置的虛擬記憶體位置。|  
|[DA0506：為所分析的處理序配置的最大私用位元組](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|此訊息報告處理序目前已配置的虛擬記憶體最大數量，以位元組 (私用位元組) 為單位。 私用位元組表示只能由處理序內執行的執行緒存取的處理序所配置的虛擬記憶體位置。|



