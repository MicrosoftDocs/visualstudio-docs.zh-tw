---
title: DA0004：處理器使用率高 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a942a26bb4cd8ccca94fd442250fe8a239cba4ed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764034"
---
# <a name="da0004-high-processor-usage"></a>DA0004：處理器使用率高
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0004 |  
|類別目錄 |分析工具使用方式 |  
|程式碼剖析方法 |檢測取樣 |  
|訊息 |處理器使用率會高於 75%一致的方式。 請考慮針對 cpu-bound 應用程式使用取樣模式。 |  
|規則類型 |資訊 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="cause"></a>原因  
 處理器 (CPU) 使用率在使用檢測方法所收集的分析資料中明顯偏高。 分析 CPU 繫結應用程式時，請考慮使用取樣分析方法。  
  
## <a name="rule-description"></a>規則描述  
 在此分析執行期間，處理器一致地非常忙碌。 CPU 使用率過高可能表示是 CPU 繫結應用程式。 檢測的設定檔通常不是調查 CPU 使用方式情節最有效的方式。 當您分析花費許多時間在處理器上執行指令的應用程式時，取樣通常更有效率。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 除非您需要函式計時，或者您比較有興趣了解輸入/輸出而不是處理器瓶頸，否則請考慮使用取樣方法而非檢測方法再次分析您的應用程式。




