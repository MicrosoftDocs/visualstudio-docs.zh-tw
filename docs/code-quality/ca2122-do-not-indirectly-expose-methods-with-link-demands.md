---
title: "CA2122： 不要間接公開具有連結要求方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fc1d8c2ea663862e44b3092b0e2b8489eff3df6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122：不要間接公開具有連結要求的方法
|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|分類|Microsoft.Security|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的成員具有[連結要求](/dotnet/framework/misc/link-demands)而且會呼叫不會執行任何安全性檢查的成員。  
  
## <a name="rule-description"></a>規則描述  
 連結要求只會檢查立即呼叫端的使用權限。 如果成員`X`不提出任何安全性要求，其呼叫端和呼叫程式碼受到連結要求，呼叫端沒有必要的權限可以使用的`X`存取受保護的成員。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 將安全性新增[資料與模型化](/dotnet/framework/data/index)或將需求連結至該成員，以便它不再提供的連結要求保護的成員不安全的存取。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 若要安全地隱藏此規則的警告，您必須確定，您的程式碼不授予其呼叫端存取作業或可以用於破壞性方式的資源。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的程式庫和應用程式，示範媒體櫃中的弱點。 範例程式庫會提供兩種方法都會違反此規則。 `EnvironmentSetting`方法受到連結要求不受限制存取環境變數。 `DomainInformation`方法提出任何安全性要求其呼叫端之前呼叫`EnvironmentSetting`。  
  
 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式會呼叫不安全的程式庫成員。  
  
 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 此範例會產生下列輸出。  
  
 **從受保護成員的值： seattle.corp.contoso.com**   
## <a name="see-also"></a>請參閱  
 [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)   
 [連結要求](/dotnet/framework/misc/link-demands)   
 [資料與模型化](/dotnet/framework/data/index)