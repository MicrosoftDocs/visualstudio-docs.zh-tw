---
title: CA2114:方法安全性應該是類型的超集 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9e0024ae6db5af3f1cf23c07fe29fbac8e4827d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944001"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114:方法安全性應該是類型的超集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別具有宣告式安全性和其中一個方法具有相同的安全性動作的宣告式安全性的安全性動作不是[連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)或是[繼承要求](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)，以及權限檢查由型別不是方法所檢查的權限的子集。

## <a name="rule-description"></a>規則描述
 方法不應該已經在兩個相同的動作方法層級和類型層級宣告式安全性。 不會合併兩個檢查;套用方法層級需求。 例如，如果型別要求的權限`X`，和其中一個方法會要求權限`Y`，不需要具有權限的程式碼`X`執行方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 檢閱您的程式碼，藉此確定這兩個動作所需。 如果這兩個動作是必要的請確定方法層級的動作，包含指定型別層級的安全性。 比方說，如果您的型別會要求權限`X`，而且它的方法也必須要求權限`Y`，此方法應該明確地要求`X`和`Y`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果方法不需要指定類型的安全性。 不過，這不是一般的案例，並可能表示需要謹慎設計檢閱。

## <a name="example"></a>範例
 下列範例會使用環境的權限，來示範違反此規則的危險性。 在此範例中，應用程式程式碼會建立安全類型的執行個體之前拒絕類型所需的權限。 在真實世界的威脅的案例中，應用程式需要另一種方式取得物件的執行個體。

 在下列範例中，程式庫會要求寫入類型的權限和讀取權限的方法。

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>範例
 下列應用程式程式碼示範的程式庫的弱點可能會藉由呼叫的方法，即使它不符合類型層級安全性需求。

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 此範例會產生下列輸出。

 **[所有的權限]個人資訊：6/16/1964年 12:00: 00AM**
 **[（型別所要求） 沒有的寫入權限] 的個人資訊：6/16/1964年 12:00: 00AM**
 **[（方法要求） 沒有讀取權限] 無法存取個人資訊：要求失敗。**
## <a name="see-also"></a>另請參閱
 [安全程式碼撰寫指導方針](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[繼承要求](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)[連結要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[資料與模型化](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
