---
title: ： Ca2108 實值型別宣告式安全性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba05728d1b12cee50512185e0875be12fa55b957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108：必須檢查實值類型上的宣告式安全性
|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|分類|Microsoft.Security|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 在公用或受保護的實值類型受到[資料與模型化](/dotnet/framework/data/index)或[連結要求](/dotnet/framework/misc/link-demands)。  
  
## <a name="rule-description"></a>規則描述  
 配置及其他建構函式執行之前，由其預設建構函式初始化實值類型。 如果實值類型受到 Demand 或 LinkDemand，而且呼叫端沒有滿足安全性檢查，任何建構函式以外的權限預設值將會失敗，並將擲回安全性例外狀況。 實值型別不會取消配置。它會處於其預設建構函式所設定的狀態。 請勿假設呼叫端傳遞實值類型的執行個體具有建立或存取執行個體的權限。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 您無法修正此規則的違規情形，除非您移除安全性檢查從型別，並使用方法層級安全性檢查其所在位置。 請注意，違規修正這種方式將不會防止呼叫者以取得實值類型的執行個體的權限不足。 您必須確定執行個體的值類型，在其預設狀態下，不會公開機密資訊，也不能有害的方式。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果任何呼叫端可以取得其預設狀態中之值型別的執行個體，而不造成安全性威脅，您可以隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會示範包含違反此規則的實值類型的程式庫。 請注意，`StructureManager`類型假設傳遞實值類型的執行個體的呼叫端若要建立或存取執行個體的權限。  
  
 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式示範媒體櫃中的弱點。  
  
 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 此範例會產生下列輸出。  
  
 **結構的自訂建構函式： 要求失敗。**  
**新值 SecuredTypeStructure 100 100**  
**新值 SecuredTypeStructure 200 200**   
## <a name="see-also"></a>另請參閱  
 [連結要求](/dotnet/framework/misc/link-demands)   
 [資料與模型化](/dotnet/framework/data/index)