---
title: Ca2211： 非常數非常數欄位不應該為可見 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d2e91cce74877a4160646db829ba9208410b403
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211：非常數欄位不應該為可見的
|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|分類|Microsoft.Usage|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的靜態欄位不是常數，也不是唯讀的。  
  
## <a name="rule-description"></a>規則描述  
 既非常數，亦非唯讀的靜態欄位不是安全執行緒。 這類欄位存取必須要小心控制，而且需要進階的程式設計技巧來同步處理對類別物件的存取。 這些是很困難的技巧，以了解 master，而且測試這類物件會自己所面臨的挑戰，因為靜態欄位最可用來儲存不會變更的資料。 此規則會套用到文件庫。應用程式不應該公開所有的欄位。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請靜態欄位，常數或唯讀狀態。 如果不可行，重新設計使用替代機制，例如管理的基礎欄位的安全執行緒存取具備執行緒安全屬性的類型。 請注意，例如競爭鎖定的情況和死結問題，可能會影響效能和程式庫的行為。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果您正在開發應用程式，因此有 「 完整控制存取權包含靜態欄位的型別。 程式庫設計人員不應該隱藏的警告，這項規則。使用非常數靜態欄位，可使用程式庫開發人員難以正確使用。  
  
## <a name="example"></a>範例  
 下列範例顯示違反此規則的類型。  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]