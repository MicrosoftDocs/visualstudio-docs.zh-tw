---
title: CA2122：不要間接公開具有連結要求的方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 846ce010cddfd505bb967ec612a5c31dd8321977
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544322"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122:不要間接公開具有連結要求的方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用或受保護的成員具有 [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) ，並由未執行任何安全性檢查的成員呼叫。

## <a name="rule-description"></a>規則描述
 連結要求只會檢查立即呼叫端的使用權限。 如果成員對 `X` 其呼叫端沒有任何安全性要求，並呼叫受連結要求保護的程式碼，則沒有必要許可權的呼叫端可以用 `X` 來存取受保護的成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 將安全性 [資料和模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) 化或連結要求新增至成員，使其不再提供不安全的存取權給連結要求保護的成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏此規則的警告，您必須確定您的程式碼不會授與呼叫者存取可以破壞性方式使用之作業或資源的存取權。

## <a name="example"></a>範例
 下列範例顯示違反規則的程式庫，以及示範程式庫弱點的應用程式。 範例程式庫提供兩個同時違反規則的方法。 `EnvironmentSetting`方法會受到連結要求保護，以不受限制地存取環境變數。 `DomainInformation`方法在呼叫之前，不會對其呼叫端提出安全性需求 `EnvironmentSetting` 。

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>範例
 下列應用程式會呼叫不安全的程式庫成員。

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 此範例會產生下列輸出。

 **來自不安全成員的值： seattle.corp.contoso.com**
## <a name="see-also"></a>另請參閱
 [安全程式碼撰寫方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料和模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化
