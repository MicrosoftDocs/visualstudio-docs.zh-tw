---
title: DA0011-昂貴的 CompareTo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aef8135e48b07946803832266ed9dff9e843d3ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916815"
---
# <a name="da0011-expensive-compareto"></a>DA0011：CompareTo 高度耗費資源

|Item|值|
|-|-|
|規則 ID|DA0011|
|類別|.NET Framework 使用方式|
|分析方法|取樣<br /><br /> .NET 記憶體|
|訊息|CompareTo 函式應該便宜，而且不會配置任何記憶體。 盡可能降低 CompareTo 函式的複雜度。|
|規則型別|警告|

## <a name="cause"></a>原因
 類型的 CompareTo 方法高度耗費資源，或配置記憶體。

## <a name="rule-description"></a>規則描述
 CompareTo 方法應該很有效率，而且不應該配置記憶體。

## <a name="how-to-fix-violations"></a>如何修正違規
 降低 CompareTo 方法的複雜性。
