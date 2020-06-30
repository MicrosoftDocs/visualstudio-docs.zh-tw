---
title: CA2114：方法安全性應該是類型的超集合 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534702"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114:方法安全性應該是類型的超集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別具有宣告式安全性，其中一個方法具有相同安全性動作的宣告式安全性，而且安全性動作不是[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)或[繼承要求](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)，而由型別檢查的許可權不是方法所檢查的許可權子集。

## <a name="rule-description"></a>規則描述
 方法不應該同時具有相同動作的方法層級和類型層級宣告式安全性。 這兩個檢查不會合並;只會套用方法層級的要求。 例如，如果某個型別要求許可權 `X` ，而其中一個方法要求許可權，則程式 `Y` 代碼不必擁有 `X` 執行方法的許可權。

## <a name="how-to-fix-violations"></a>如何修正違規
 請檢查您的程式碼，以確定這兩個動作都是必要的。 如果這兩個動作都是必要的，請確定方法層級動作包含在類型層級指定的安全性。 例如，如果您的型別要求許可權 `X` ，而且其方法也必須要求許可權 `Y` ，則方法應該明確地要求 `X` 和 `Y` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果方法不需要類型所指定的安全性，則可以安全地隱藏此規則的警告。 不過，這不是一般案例，而且可能表示需要謹慎的設計審查。

## <a name="example"></a>範例
 下列範例會使用環境許可權來示範違反此規則的危險。 在此範例中，應用程式程式碼會先建立安全類型的實例，再拒絕該類型所需的許可權。 在真實世界的威脅案例中，應用程式需要另一種方式來取得物件的實例。

 在下列範例中，程式庫會要求類型的寫入權限，以及方法的讀取權限。

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>範例
 下列應用程式代碼會藉由呼叫方法來示範程式庫的弱點，即使它不符合類型層級的安全性需求也一樣。

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 此範例會產生下列輸出。

 **[擁有權限] 個人資訊： 6/16/1964 12:00:00 AM** 
 **[沒有寫入權限（要求者類型）] 個人資訊： 6/16/1964 12:00:00 AM** 
 **[沒有讀取權限（方法要求）] 無法存取個人資訊：要求失敗。**
## <a name="see-also"></a>另請參閱
 [安全程式碼撰寫指導方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[繼承要求](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)化
