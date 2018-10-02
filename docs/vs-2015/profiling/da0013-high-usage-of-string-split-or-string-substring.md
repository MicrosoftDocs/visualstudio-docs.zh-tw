---
title: DA0013：String.Split 或 String.Substring 的用量高 | Microsoft Docs
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
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8f835e120f730f9c223477959e9c93dfefa240
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497429"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013：String.Split 或 String.Substring 的用量高
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[DA0013： 或 String.Substring 的用量高使用量](https://docs.microsoft.com/visualstudio/profiling/da0013-high-usage-of-string-split-or-string-substring)。  
  
規則 Id |DA0013 |  
|類別目錄 |。NET Framework 使用方式指導 |  
|程式碼剖析方法 |取樣 |  
|訊息 |請考慮減少使用 String.Split 和 String.Substring 函式。 |  
|規則類型 |警告 |  
  
## <a name="cause"></a>原因  
 呼叫 System.String.Split 或 System.String.Substring 方法是分析資料的重要部分。 如果您要測試某個子字串是否存在字串中，請考慮使用 System.String.IndexOf 或 System.String.IndexOfAny。  
  
## <a name="rule-description"></a>規則描述  
 Split 方法會在 String 物件上運作，並傳回包含原始子字串之 String 的新陣列。 函式會為傳回的陣列物件配置記憶體，並為它找到的每個陣列元素配置新的 String 物件。 同樣地，Substr 方法會在 String 物件上運作，並傳回相當於所要求之子字串的新 String。  
  
 如果在應用程式中管理記憶體配置很重要，請考慮使用 String.Split 和 String.Substr 方法的替代方案。 例如，您可以使用 IndexOf 或 IndexOfAny 方法在字元 String 內尋找特定子字串，而不需建立新的 String 類別執行個體。  
  
## <a name="how-to-investigate-a-warning"></a>如何調查警告  
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至取樣分析資料的[函式詳細資料檢視](../profiling/function-details-view.md)。 檢查呼叫函式，找出最常使用 System.String.Split 或 System.String.Substr 方法的程式區段。 可能的話，請使用 IndexOf 或 IndexOfAny 方法在字元 String 字串內尋找特定子字串，而不需建立新的 String 類別執行個體。



