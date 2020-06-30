---
title: CA2108：查看實數值型別的宣告式安全性 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03918353b66c36698b5d17b332da052b6d95c87a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544387"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108:必須檢閱實值類型上的宣告式安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用或受保護的實值型別會受到[資料和模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化或[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)的保護。

## <a name="rule-description"></a>規則描述
 實值型別會由其預設的函式來配置及初始化，然後再執行其他的函式 如果實值型別受到需求或 LinkDemand 的保護，而且呼叫端沒有符合安全性檢查的許可權，則預設值以外的任何其他任何函式都會失敗，而且會擲回安全性例外狀況。 數值型別不會解除配置;它會保留在預設的函式所設定的狀態中。 請勿假設傳遞實數值型別之實例的呼叫端具有建立或存取實例的許可權。

## <a name="how-to-fix-violations"></a>如何修正違規
 除非您從類型移除安全性檢查，並在其位置使用方法層級安全性檢查，否則無法修正此規則的違規。 請注意，以這種方式修正違規，並不會防止許可權不足的呼叫端取得實數值型別的實例。 您必須確保實值型別的實例（其預設狀態）不會公開機密資訊，而且無法以有害的方式使用。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果任何呼叫者可以取得其預設狀態的實數值型別實例，而不會對安全性造成威脅，您可以隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示的程式庫包含違反此規則的實數值型別。 請注意， `StructureManager` 類型假設傳遞實數值型別之實例的呼叫端具有建立或存取實例的許可權。

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>範例
 下列應用程式會示範程式庫的弱點。

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 此範例會產生下列輸出。

 **結構自訂構造函式：要求失敗。** 
**新值 SecuredTypeStructure 100 100** 
**新值 SecuredTypeStructure 200 200**
## <a name="see-also"></a>另請參閱
 [連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化
