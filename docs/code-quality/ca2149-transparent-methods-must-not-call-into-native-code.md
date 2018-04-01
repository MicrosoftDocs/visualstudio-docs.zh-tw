---
title: CA2149： 透明方法不可以呼叫至原生程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9377a30d2fc56c8acef16b6bcf1187d0e9fa8741
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149：透明方法不可以呼叫機器碼
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 方法會呼叫的方法虛設常式，例如 P/Invoke 透過原生函式。  
  
## <a name="rule-description"></a>規則描述  
 任何直接呼叫機器碼的透明方法都會引發此規則，例如透過 P/Invoke。 違反此規則會導致<xref:System.MethodAccessException>層級 2 透明度模型，而完整的要求，如<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>在層級 1 透明度模型。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，將方法呼叫原生程式碼，以標示<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]