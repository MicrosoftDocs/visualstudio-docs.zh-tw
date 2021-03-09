---
title: DA0010-昂貴的 GetHashCode |Microsoft 檔
description: 類型的 GetHashCode 方法呼叫大部分是分析資料，或方法會配置記憶體。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d44c998cabd3611e2ed393be0ad7df20e1ac49c
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469920"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010：GetHashCode 高度耗費資源

|Item|值|
|-|-|
|規則 ID|DA0010|
|類別|.NET Framework 使用方式|
|分析方法|取樣<br /><br /> .NET 記憶體|
|訊息|GetHashCode 函式應該便宜，而且不會配置任何記憶體。 盡可能降低雜湊碼函式的複雜度。|
|訊息類型|警告|

## <a name="cause"></a>原因
 類型的 GetHashCode 方法呼叫大部分是分析資料，或方法會配置記憶體。

## <a name="rule-description"></a>規則描述
 雜湊是一種技術，可快速尋找大型集合中的特定項目。 因為雜湊表可能很龐大，而且必須支援極高的存取率，所以雜湊表應該很有效率。 這項需求的含意在於 .NET Framework 中的 GetHashCode 方法不應該配置記憶體。 配置記憶體時會增加記憶體回收行程的負載，而且在因配置要求而需要執行記憶體回收時公開潛在延遲方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 降低方法的複雜性。
