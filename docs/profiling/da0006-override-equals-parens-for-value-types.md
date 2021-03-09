---
title: DA0006-覆寫數值型別的 Equals () |Microsoft 檔
description: Equals 方法呼叫或公用實值型別的相等運算子大部分是分析資料。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6f8399dbe43c20a8c888ac4e4bac9ec8b03e9610
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466137"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006：覆寫實值型別的 Equals()

|Item|值|
|-|-|
|規則 ID|DA0006|
|類別|.NET Framework 使用方式|
|分析方法|取樣|
|訊息|覆寫實值型別的 Equals 和相等運算子。|
|訊息類型|警告|

## <a name="cause"></a>原因
 Equals 方法呼叫或公用實值型別的相等運算子大部分是分析資料。 請考慮實作更有效率的方法。

## <a name="rule-description"></a>規則描述
 對於實值型別而言，Equals 的繼承實作會使用 <xref:System.Reflection> 程式庫，並比較類型中所有欄位的內容。 但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。 如果希望使用者比較或排序執行個體，或是使用它們作為雜湊表索引鍵，則您的實值型別應該實作 Equals。 如果您的程式設計語言支援運算子多載，則也應該提供相等和不等運算子的實作。

 如需如何覆寫 Equals 和等號比較運算子的詳細資訊，請參閱[實作 Equals 和相等運算子 (==) 的方針](/dotnet/standard/design-guidelines/equality-operators)。

## <a name="how-to-investigate-a-warning"></a>如何調查警告
 如需實作 Equals 和相等運算子的範例，請參閱程式碼分析規則 [CA1815：必須覆寫實值型別上的 Equals 方法和相等運算子](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)
