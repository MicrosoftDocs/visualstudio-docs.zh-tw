---
title: DA0013：String.Split 或 String.Substring 的高用量 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e261a0822622ec7a2c404539c3cd53f5daf9b67a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989909"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013：String.Split 或 String.Substring 的高用量

|||  
|-|-|  
|規則 ID|DA0013|  
|分類|.NET Framework 使用方式指導|  
|分析方法|取樣|  
|訊息|考慮減少使用 String.Split 和 String.Substring 函式。|  
|規則型別|警告|  

## <a name="cause"></a>原因  
 呼叫 System.String.Split 或 System.String.Substring 方法是分析資料的重要部分。 如果您要測試某個子字串是否存在字串中，請考慮使用 System.String.IndexOf 或 System.String.IndexOfAny。  

## <a name="rule-description"></a>規則描述  
 Split 方法會在 String 物件上運作，並傳回包含原始子字串之 String 的新陣列。 函式會為傳回的陣列物件配置記憶體，並為它找到的每個陣列元素配置新的 String 物件。 同樣地，Substr 方法會在 String 物件上運作，並傳回相當於所要求之子字串的新 String。  

 如果在應用程式中管理記憶體配置很重要，請考慮使用 String.Split 和 String.Substr 方法的替代方案。 例如，您可以使用 IndexOf 或 IndexOfAny 方法在字元 String 內尋找特定子字串，而不需建立新的 String 類別執行個體。  

## <a name="how-to-investigate-a-warning"></a>如何調查警告  
 按兩下 [錯誤清單] 視窗中的訊息，巡覽至取樣分析資料的[函式詳細資料檢視](../profiling/function-details-view.md)。 檢查呼叫函式，找出最常使用 System.String.Split 或 System.String.Substr 方法的程式區段。 可能的話，請使用 IndexOf 或 IndexOfAny 方法在字元 String 字串內尋找特定子字串，而不需建立新的 String 類別執行個體。