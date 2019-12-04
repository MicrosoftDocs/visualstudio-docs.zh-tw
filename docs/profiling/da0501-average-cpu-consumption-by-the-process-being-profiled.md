---
title: DA0501：進行程式碼剖析之處理序所需的平均 CPU 使用量。 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9835ad1965d1fd9a31113117eeb07ed62fd8ec4
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777459"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501：所分析之處理序的平均 CPU 使用量。

|||
|-|-|
|規則識別碼|DA501|
|Category|資源監視|
|程式碼剖析方法|全部|
|訊息|所分析之處理序的平均 CPU 消耗。|
|規則類型|資訊|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="rule-description"></a>規則描述
 此訊息報告處理器忙於執行應用程式指令的時間百分比。 報告的值是所分析的處理序作用中之所有測量間隔的平均。 在有多個處理器的電腦上，值可以大於 100%。

## <a name="how-to-use-rule-data"></a>如何使用規則資料
 使用規則值可比較程式不同版本或組建的效能，或了解不同測試情節中的應用程式效能。
