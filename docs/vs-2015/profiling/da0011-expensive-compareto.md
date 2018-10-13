---
title: DA0011：CompareTo 高度耗費資源 | Microsoft Docs
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
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0726ef4eb93d3e962e5fa39fe9cc7acbdbfbe8ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210440"
---
# <a name="da0011-expensive-compareto"></a>DA0011：CompareTo 高度耗費資源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 的最新文件，請參閱 < [DA0011： 高度耗費資源](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto)docs.microsoft.com 上。  
  
|||  
|-|-|  
|規則 ID|DA0011|  
|分類|.NET Framework 使用方式|  
|分析方法|取樣<br /><br /> .NET 記憶體|  
|訊息|CompareTo 函式應該便宜，而且不會配置任何記憶體。 盡可能降低 CompareTo 函式的複雜度。|  
|規則型別|警告|  
  
## <a name="cause"></a>原因  
 類型的 CompareTo 方法高度耗費資源，或配置記憶體。  
  
## <a name="rule-description"></a>規則描述  
 CompareTo 方法應該很有效率，而且不應該配置記憶體。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 降低 CompareTo 方法的複雜性。

