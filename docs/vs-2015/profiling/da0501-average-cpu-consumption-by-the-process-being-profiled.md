---
title: DA0501：進行程式碼剖析之處理序所需的平均 CPU 使用量。 | Microsoft Docs
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
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e2a270195a4d3689b2a5756c4633654bd3f06ae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194204"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501：進行程式碼剖析之處理序所需的平均 CPU 使用量。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA501 |  
|類別目錄 |資源監視 |  
|程式碼剖析方法 |所有 |  
|訊息 |正在分析之處理序的 CPU 耗用量的平均。 |  
|規則類型 |資訊 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="rule-description"></a>規則描述  
 此訊息報告處理器忙於執行應用程式指令的時間百分比。 報告的值是所分析的處理序作用中之所有測量間隔的平均。 在有多個處理器的電腦上，值可以大於 100%。  
  
## <a name="how-to-use-rule-data"></a>如何使用規則資料  
 使用規則值可比較程式不同版本或組建的效能，或了解不同測試情節中的應用程式效能。



