---
title: CA1031：不要攔截一般例外狀況類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542398"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031:不要攔截一般例外狀況類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 一般例外狀況（例如 <xref:System.Exception?displayProperty=fullName> 或 <xref:System.SystemException?displayProperty=fullName> ）會在語句中捕捉 `catch` ，或使用一般 catch 子句（例如） `catch()` 。

## <a name="rule-description"></a>規則描述
 不應該攔截一般例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請攔截更明確的例外狀況，或重新擲回一般例外狀況做為區塊中的最後一個語句 `catch` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 攔截一般例外狀況類型可以隱藏程式庫使用者的執行時間問題，並且可以使調試更困難。

> [!NOTE]
> 從開始 [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] ，common language runtime (CLR) 不再將作業系統和 managed 程式碼中發生的損毀狀態例外狀況（例如存取違規 [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] ）傳遞給 managed 程式碼處理。 如果您想要在或更新版本中編譯應用程式， [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 並維護損毀狀態例外狀況的處理，您可以將 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 屬性套用至處理損毀狀態例外狀況的方法。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別，以及正確實作為區塊的型別 `catch` 。

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2200:必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
