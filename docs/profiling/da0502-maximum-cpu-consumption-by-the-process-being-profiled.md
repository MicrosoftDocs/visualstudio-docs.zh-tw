---
title: DA0502-所分析進程的最大 CPU 耗用量 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 988e9576f7c5aacac4bc4335f06b08dd1176f847
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918112"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502：所分析之處理序的最大 CPU 使用量

|Item|值|
|-|-|
|規則 ID|DA0502|
|類別|資源監視|
|程式碼剖析方法|全部|
|訊息|此規則僅供參考之用。 Process()\\%Processor Time 計數器會測量所分析之處理序的 CPU 使用量。 報告的值是所有測量間隔所觀察到最大值。|
|規則型別|資訊|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="rule-description"></a>規則描述
 此訊息報告處理器忙於執行應用程式指令的最大時間百分比。 報告的值是在所分析的處理序作用中之所有測量間隔當中報告的最大值。 在有多個處理器的電腦上，百分比可以大於 100%。

## <a name="how-to-use-the-rule-data"></a>如何使用規則資料
 使用規則值可比較程式不同版本或組建的效能，或了解不同分析情節中的應用程式效能。
