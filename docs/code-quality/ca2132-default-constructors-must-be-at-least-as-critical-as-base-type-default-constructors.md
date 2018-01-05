---
title: "CA2132： 預設建構函式必須至少和基底類型的預設建構函式一樣關鍵 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 752103825a25c4352ccc21730b8d2b7265f8f41b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132：預設建構函式至少必須和基底類型的預設建構函式一樣關鍵
|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
> [!NOTE]
>  這個警告只會套用至執行 CoreCLR （Silverlight Web 應用程式特有的 clr 版本） 的程式碼中。  
  
## <a name="cause"></a>原因  
 在衍生類別中的預設建構函式的透明度屬性就沒那麼重要做為基底類別的透明度。  
  
## <a name="rule-description"></a>規則描述  
 型別和成員具有<xref:System.Security.SecurityCriticalAttribute>Silverlight 應用程式程式碼無法使用。 重視安全性的類型以及成員，只能夠由 .NET Framework for Silverlight 類別庫中的受信任程式碼使用。 由於衍生類別中的公用或受保護建構所具有的透明度必須大於或等於其基底類別，因此應用程式中的類別不可衍生自標記為 SecurityCritical 的類別。  
  
 CoreCLR 平台程式碼，如果基底類型具有 public 或 protected 非透明的預設建構函式再衍生型別必須遵守預設建構函式繼承規則。 衍生的型別也必須有預設建構函式，該建構函式必須至少為關鍵預設建構函式的基底型別。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正的違規情形，移除型別或不是衍生自安全性不透明的類型。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 違反此規則應用程式碼會導致拒絕載入的型別與 CoreCLR <xref:System.TypeLoadException>。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### <a name="comments"></a>註解