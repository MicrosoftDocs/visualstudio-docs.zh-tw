---
title: "CA2114： 方法安全性應該是類型的超集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a3ff1a6be01b51f45b0ca5b5417ead2195d023bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114：方法安全性應該是類型的超集
|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 型別具有宣告式安全性，而且其中一個方法具有相同的安全性動作的宣告式安全性及安全性動作不是[連結要求](/dotnet/framework/misc/link-demands)，並沒有權限的子集這種型別所檢查的權限。檢查此方法。  
  
## <a name="rule-description"></a>規則描述  
 方法不應該都相同的動作方法層級和類型層級宣告式安全性。 不會合併兩個檢查;只有方法層級需求會套用。 例如，如果型別要求權限`X`，其中一個方法會要求權限和`Y`，程式碼沒有擁有的權限`X`執行方法。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 檢閱您的程式碼，請確定這兩個動作所需。 如果這兩個動作是必要的請確定方法層級的動作，包含指定型別層級的安全性。 例如，如果型別要求權限`X`，而且它的方法也必須要求權限`Y`，方法應該明確地要求`X`和`Y`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果此方法不需要類型所指定的安全性。 不過，這不是一般的案例，而且可能表示需要謹慎設計檢閱。  
  
## <a name="example"></a>範例  
 下列範例會使用環境的權限示範違反此規則的資訊。 在此範例中，應用程式程式碼會建立安全類型的執行個體之前拒絕類型所需的權限。 在真實世界威脅的情況下，應用程式需要另一種方式取得物件的執行個體。  
  
 在下列範例中，程式庫會要求寫入權限類型，並讀取權限的方法。  
  
 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式程式碼示範的程式庫的弱點可能會透過呼叫方法，即使它不符合類型層級安全性需求。  
  
 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 此範例會產生下列輸出。  
  
 **[所有的權限]個人資訊： 6/16/1964年 12:00:00 AM**  
**[（型別所要求） 沒有的寫入權限]個人資訊： 6/16/1964年 12:00:00 AM**  
**[（要求的方法） 沒有讀取權限]無法存取個人資訊： 要求失敗。**   
## <a name="see-also"></a>請參閱  
 [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)   
 [連結要求](/dotnet/framework/misc/link-demands)   
 [資料與模型化](/dotnet/framework/data/index)