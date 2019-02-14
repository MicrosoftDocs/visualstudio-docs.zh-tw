---
title: DA0026：過多核心 CPU 時間處理 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef0a3c42be1057bd1217ec676ae43b220d80345
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768967"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026：過多核心 CPU 時間處理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |TODO |  
|類別目錄 |分析工具使用方式 |  
|程式碼剖析方法 |取樣 |  
|訊息 |測量相對大量的核心模式 CPU 時間。 請考慮啟用 SysCall 取樣來調查來源。  
|規則類型 |資訊 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="cause"></a>原因  
 在核心模式中執行的 CPU 時間比例超過在使用者模式中所花費的時間量。 請考慮再次分析並對系統呼叫 (syscall) 取樣來判斷高核心模式執行時間的原因。  
  
## <a name="rule-description"></a>規則描述  
 應用程式花在核心模式執行很高比例的時間可能需要進一步調查。 使用者模式應用程式會轉換成核心模式以執行 I/O 作業、等候執行緒或處理同步原始物件，或執行系統呼叫。 當您根據系統呼叫選取要收集樣本呼叫堆疊的選項時，可以調查應用程式呼叫的系統呼叫種類，以及負責呼叫這些系統呼叫的函式。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要調查應用程式呼叫的系統呼叫種類，請再次執行分析並根據系統呼叫選取要收集樣本的選項。 如果您在 IDE 內執行分析工具，請參閱[如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)了解詳細資訊。 如果您要從命令列執行分析工具，請參閱分析工具命令列工具參考中 [VSPerfCmd](../profiling/vsperfcmd.md) 主題中的＜取樣間隔選項＞一節。
