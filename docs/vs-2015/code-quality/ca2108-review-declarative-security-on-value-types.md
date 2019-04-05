---
title: CA2108:必須檢閱實值型別上的宣告式安全性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b8bafb021e2a73b0a5bed7feba21fbb38fff8ce
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943240"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108:必須檢閱實值類型上的宣告式安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用或受保護的實值型別會受到[資料與模型化](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)或是[連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)。

## <a name="rule-description"></a>規則描述
 配置及其他建構函式執行之前，其預設建構函式來初始化實值型別。 如果實值型別會受到 Demand 或 LinkDemand 的比較，而且呼叫端沒有滿足安全性檢查，而任何建構函式以外的權限預設值將會失敗，並將擲回安全性例外狀況。 實值型別不會取消配置;它會處於其預設建構函式所設定的狀態。 請勿假設呼叫端傳遞實值型別的執行個體具有建立或存取執行個體的權限。

## <a name="how-to-fix-violations"></a>如何修正違規
 除非您從類型 中移除安全性檢查，並使用方法層級安全性檢查在其位置中，您無法修正此規則的違規情形。 請注意，這種方式修正違規時，會防止具有足夠的權限，無法取得實值型別的執行個體的呼叫端。 您必須確保執行個體的值型別，在其預設狀態下，不會公開機密資訊，且不能用於有害的方式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果任何呼叫端可以取得實值型別，其預設狀態中的執行個體，而不造成安全性威脅，您可以隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範包含違反這項規則實值型別程式庫。 請注意，`StructureManager`類型會假設呼叫端傳遞實值型別的執行個體具有建立或存取執行個體的權限。

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>範例
 下列應用程式示範程式庫的弱點。

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 此範例會產生下列輸出。

 **結構自訂建構函式：要求失敗。** 
**新值 SecuredTypeStructure 100 100**
**新值 SecuredTypeStructure 200 200**
## <a name="see-also"></a>另請參閱
 [連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型化](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
