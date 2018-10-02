---
title: DA0008：收集的樣本少 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 205bedf2baa7c9fa1e1c5f40ccbaa4041427074b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500409"
---
# <a name="da0008-few-samples-collected"></a>DA0008：收集的樣本少
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[DA0008： 收集的樣本少](https://docs.microsoft.com/visualstudio/profiling/da0008-few-samples-collected)。  
  
規則 Id |DA0008 |  
|類別目錄 |分析工具使用方式 |  
|程式碼剖析方法 |取樣 |  
|訊息 |收集到只有少數範例。 請考慮較大量的結果較長或更快的取樣率。 |  
|規則類型 |資訊 |  
  
## <a name="cause"></a>原因  
 在執行分析中只收集到少量樣本。  
  
## <a name="rule-description"></a>規則描述  
 使用取樣方法時，您應該收集統計顯著的樣本數目，以確保資料代表實際的程式行為。 若要讓取樣錯誤降到最少，您應該嘗試至少收集 1000個程式指令執行行為的樣本。 如果您沒有收集到足夠的樣本，對分析資料進行分析時，可能會被誤導。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 請考慮分析較長的應用程式執行時間，或使用更快速的取樣率來取得統計顯著的結果。 如需如何在 Visual Studio IDE 中變更取樣率的詳細資訊，請參閱[如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)。 如需如何使用分析工具命令列變更取樣率的詳細資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 參考中的[計時器](../profiling/timer.md)。



