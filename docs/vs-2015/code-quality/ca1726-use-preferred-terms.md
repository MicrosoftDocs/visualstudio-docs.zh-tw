---
title: CA1726:使用慣用的詞彙 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: 67dab4c732faa04af44800f740d78c4ce4f9dc80
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664108"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726:建議使用慣用詞彙
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新文件，請參閱[ca1726 建議：使用慣用的詞彙](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms)。  
  
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
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` 或 `Flags`|沒有任何取代詞彙。 請勿使用。|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請以慣用的替代詞彙取代的詞彙。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 只有識別項的名稱是刻意設計的而且特別是與原始詞彙，而不是慣用的詞彙，請隱藏這個規則的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [命名警告](../code-quality/naming-warnings.md)
