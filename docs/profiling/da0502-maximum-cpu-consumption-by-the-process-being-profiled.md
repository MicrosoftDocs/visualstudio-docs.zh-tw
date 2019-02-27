---
title: DA0502：所分析之處理序的最大 CPU 使用量 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7092e6424a5f00ed4461a91ed10bbf530597082
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612253"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502：所分析之處理序的最大 CPU 使用量

|||
|-|-|
|規則 ID|DA0502|
|分類|資源監視|
|程式碼剖析方法|全部|
|訊息|此規則僅供參考之用。 Process()\\%Processor Time 計數器會測量所分析之處理序的 CPU 使用量。 報告的值是所有測量間隔所觀察到最大值。|
|規則型別|告知性|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="rule-description"></a>規則描述
 此訊息報告處理器忙於執行應用程式指令的最大時間百分比。 報告的值是在所分析的處理序作用中之所有測量間隔當中報告的最大值。 在有多個處理器的電腦上，百分比可以大於 100%。

## <a name="how-to-use-the-rule-data"></a>如何使用規則資料
 使用規則值可比較程式不同版本或組建的效能，或了解不同分析情節中的應用程式效能。