---
title: CA1726：建議使用慣用詞彙
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41cb61db3916bdb5879931de28d6b87ccdde4853
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1726-use-preferred-terms"></a>CA1726：建議使用慣用詞彙
|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|分類|Microsoft.Naming|
|中斷變更|中斷-時引發的組件<br /><br /> 非-中斷-時引發型別參數|

## <a name="cause"></a>原因
 外部可見的識別項名稱包含有替代慣用詞彙存在的詞彙。 或者，該名稱包含詞彙的旗標或旗標。

## <a name="rule-description"></a>規則描述
 此規則會識別項剖析為語彙基元。 每個單一的語彙基元和每個連續的雙重語彙基元組合進行比較內建在規則中的任何自訂字典的已過時 > 一節中的條款。 下表顯示規則以及其慣用的替代項目內建的詞彙。

|過時的詞彙|慣用的詞彙|
|-------------------|--------------------|
|不是|部署|
|已取消|已取消|
|無法|無法|
|ComPlus|EnterpriseServices|
|Couldnt|CouldNot|
|Didnt|DidNot|
|Doesnt|微處理器|
|不要|沒有|
|旗標或旗標|沒有任何取代詞彙。 請勿使用。|
|以往|HadNot|
|尚未|HasNot|
|您尚未|HaveNot|
|索引|Indexes|
|不是|IsNot|
|登入|登入|
|登出|登出|
|Shouldnt|ShouldNot|
|登入|登入|
|登出|登出|
|Wasnt|WasNot|
|未|WereNot|
|時會|出口|
|Wouldnt|WouldNot|
|可寫入|可寫入|

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請以慣用的替代詞彙取代的詞彙。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有當的識別項名稱是刻意設計，特別是與相關原始詞彙，而不是慣用詞彙隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則
 [命名警告](../code-quality/naming-warnings.md)