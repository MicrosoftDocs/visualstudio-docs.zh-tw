---
title: DA0011：CompareTo 高度耗費資源 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 281bdbb3ba974b3aacb9c349575727675bb59305
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58354735"
---
# <a name="da0011-expensive-compareto"></a>DA0011：CompareTo 高度耗費資源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱 < [DA0011： 高度耗費資源](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto)docs.microsoft.com 上。  
  
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
