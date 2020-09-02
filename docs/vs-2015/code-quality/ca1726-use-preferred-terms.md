---
title: CA1726 建議：使用慣用詞彙 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96e0614bc5c08c83008af4e67a2aa865f08f74f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547806"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726:建議使用慣用詞彙
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [ca1726 建議：使用慣用詞彙](/visualstudio/code-quality/ca1726-use-preferred-terms)。

|Item|值|
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|類別|Microsoft。命名|
|中斷變更|重大-在元件上引發<br /><br /> 非中斷-在類型參數上引發時|

## <a name="cause"></a>原因
 外部可見的識別項名稱包含有替代慣用詞彙存在的詞彙。 或者，此名稱包含字詞旗標或旗標。

## <a name="rule-description"></a>規則描述
 此規則會將識別碼剖析為權杖。 每個單一權杖和每個連續的雙重 token 組合都會與規則內建的詞彙和任何自訂字典的已淘汰區段進行比較。 下表顯示規則內建的詞彙及其慣用的替代方案。

|淘汰的詞彙|慣用詞彙|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` 或 `Flags`|沒有取代字詞。 請勿使用。|
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
 若要修正此規則的違規情形，請以慣用的替代字詞取代該詞彙。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有當識別碼的名稱是刻意的，且與原始詞彙（而非慣用詞彙）相關時，才會隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [命名警告](../code-quality/naming-warnings.md)
