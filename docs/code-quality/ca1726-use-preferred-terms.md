---
title: "Ca1726： 建議使用慣用的詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords: UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ae02d0eb136d45bc2b8af7dde5f897765493050
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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