---
title: CA2122:不要間接公開具有連結要求的方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8239b27cd92f66ae8f74ddb1accd95535bf56f93
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953863"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122:不要間接公開具有連結要求的方法

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用或受保護的成員都有[連結要求](/dotnet/framework/misc/link-demands)而且會呼叫不會執行任何安全性檢查的成員。

## <a name="rule-description"></a>規則描述
 連結要求只會檢查立即呼叫端的使用權限。 如果成員`X`不提出任何安全性要求，其呼叫端，和呼叫程式碼受到連結要求，呼叫端沒有必要的權限可以使用`X`存取受保護的成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 新增安全性[資料與模型化](/dotnet/framework/data/index)或連結至成員的需求，使其不再提供不安全的存取連結需要受保護成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 若要安全地隱藏此規則的警告，您必須確定，您的程式碼並未授與它的呼叫端存取作業或可以用於破壞性方式的資源。

## <a name="example-1"></a>範例 1
 下列範例顯示違反規則的程式庫和應用程式，示範程式庫的弱點。 範例程式庫提供兩種方法可一起違反規則。 `EnvironmentSetting`方法受到連結要求不受限制存取環境變數。 `DomainInformation`方法提出任何安全性要求其呼叫端之前呼叫`EnvironmentSetting`。

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>範例 2
 下列應用程式會呼叫不安全的程式庫成員。

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

這個範例會產生下列輸出：

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [連結要求](/dotnet/framework/misc/link-demands)
- [資料與模型化](/dotnet/framework/data/index)