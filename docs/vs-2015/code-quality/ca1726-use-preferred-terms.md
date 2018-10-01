---
title: Ca1726： 建議使用慣用的詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b13c43a563a158a2eeb8484e29810c5b91d110aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486683"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726：建議使用慣用詞彙
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 的最新文件，請參閱 < [ca1726 建議： 使用慣用的詞彙](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms)docs.microsoft.com 上。  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|分類|Microsoft.Naming|  
|中斷變更|中斷-時引發的組件<br /><br /> 非中斷-時引發的類型參數|  
  
## <a name="cause"></a>原因  
 外部可見的識別項名稱包含有替代慣用詞彙存在的詞彙。 或者，名稱會包含詞彙的旗標或旗標。  
  
## <a name="rule-description"></a>規則描述  
 此規則會剖析為語彙基元識別項。 每個單一的語彙基元和每個連續的雙重語彙基元組合進行比較建置成規則和任何自訂字典的已被取代區段中的條款。 下表顯示內建規則，其慣用的替代方案的條款。  
  
|過時的詞彙|慣用的詞彙|  
|-------------------|--------------------|  
|不是|後面|  
|已取消|已取消|  
|無法|無法|  
|ComPlus|EnterpriseServices|  
|無法|CouldNot|  
|Didnt|DidNot|  
|Doesnt|不|  
|不要|不要|  
|旗標或旗標|沒有任何取代詞彙。 請勿使用。|  
|還沒|HadNot|  
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
|端可|出口|  
|Wouldnt|WouldNot|  
|可寫入|可寫入|  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請以慣用的替代詞彙取代的詞彙。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 只有識別項的名稱是刻意設計的而且特別是與原始詞彙，而不是慣用的詞彙，請隱藏這個規則的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [命名警告](../code-quality/naming-warnings.md)

