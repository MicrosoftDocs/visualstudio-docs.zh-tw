---
title: CA1031： 不要攔截一般例外狀況類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab2b235037e68d7c824d144d29dfb58ac8c5c066
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031：不要攔截一般例外狀況類型
|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|CheckId|CA1031|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 一般的例外狀況，例如<xref:System.Exception?displayProperty=fullName>或<xref:System.SystemException?displayProperty=fullName>陷入`catch`陳述式或這類的一般 catch 子句`catch()`用。  
  
## <a name="rule-description"></a>規則描述  
 不應該攔截一般例外狀況。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，攔截更特定的例外狀況，或重新擲回一般例外狀況中的最後一個陳述式`catch`區塊。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 攔截一般例外狀況類型，可以隱藏執行階段對程式庫使用者的問題，並會會使得偵錯更加困難。  
  
> [!NOTE]
>  從開始[!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)]，common language runtime (CLR) 不再提供中的作業系統和 managed 程式碼，例如存取違規發生的損毀的狀態例外狀況[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]、 要處理的 managed 程式碼。 如果您想要編譯的應用程式在[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]或更新版本及維護的損毀的狀態例外狀況處理，您可以套用<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性設處理損毀的狀態例外狀況的方法。  
  
## <a name="example"></a>範例  
 下列範例顯示違反此規則的類型，以及正確實作的型別`catch`區塊。  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA2200：必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)