---
title: 程式碼剖析工具使用規則 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67d9d98ed089c8afc32cc8daba2ca029ccd99101
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987436"
---
# <a name="profiling-tools-usage-rules"></a>程式碼剖析工具使用規則
程式碼剖析工具使用分類中的效能規則提供的指引，可最有效地使用分析工具來收集資料。  


| | |
| - | - |
| [DA0002：遺漏 VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | 命令列程式碼剖析可能包含不完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 二進位檔資料。 這可能是因為沒有設定正確的環境變數所造成。 |
| [DA0003：許多核心樣本](../profiling/da0003-many-kernel-samples.md) | 記錄到許多不在目標二進位檔執行時發生的程式碼剖析樣本。 請考慮使用檢測方法，以收集更精確的資料。 |
| [DA0004：處理器使用率高](../profiling/da0004-high-processor-usage.md) | 程式碼剖析資料指出處理器在程式碼剖析執行期間持續忙碌中。 請考慮使用取樣方法，以收集更精確的資料。 |
| [DA0008：收集的樣本少](../profiling/da0008-few-samples-collected.md) | 在程式碼剖析執行時所收集的樣本數不高，統計顯著性不足。 請考慮再次進行程式碼剖析，並執行應用程式更長一段時間。 您也可以考慮使用檢測方法來收集資料。 |
| [DA0026：過多核心 CPU 時間處理](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | 在程式碼剖析執行時，有大量時間都處於處理器核心模式。 取樣時，請考慮使用系統呼叫作為度量，而不是使用時間作為度量。 |
| [DA0029：不支援的 CLR 版本](../profiling/da0029-unsupported-clr-version.md) | 分析工具不支援已進行程式碼剖析的二進位檔使用 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。 分析工具報表無法解析符號名稱。 |
| [DA0030：資料庫專案的收集階層互動度量](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | 收集到大量對 <xref:System.Data?displayProperty=fullName> 命名空間中方法的呼叫。 若要納入資料庫呼叫的相關資料，請考慮在分析執行時收集階層互動資料。 |
