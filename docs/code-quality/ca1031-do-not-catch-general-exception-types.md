---
title: CA1031:不要攔截一般例外狀況類型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236058"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031:不要攔截一般例外狀況類型

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|分類|Microsoft.Design|
|重大變更|不中斷|

## <a name="cause"></a>原因
一般<xref:System.Exception?displayProperty=fullName>例外狀況（例如或<xref:System.SystemException?displayProperty=fullName> ）會在`catch`語句中攔截，或使用一般 catch 子句（ `catch()`例如）。

## <a name="rule-description"></a>規則描述
不應該攔截一般例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請攔截更特定的例外狀況，或重新擲回一般例外狀況做為`catch`區塊中的最後一個語句。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 攔截一般例外狀況類型可能會隱藏程式庫使用者的執行時間問題，而且可能會使調試更困難。

> [!NOTE]
> 從 .NET Framework 4 開始，common language runtime （CLR）不再傳遞作業系統和 managed 程式碼（例如中[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]的存取違規）所發生的損毀狀態例外狀況，以供 managed 程式碼處理。 如果您想要在 .NET Framework 4 或更新版本中編譯應用程式，並維護損毀狀態例外狀況的處理，您<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>可以將屬性（attribute）套用至處理損毀狀態例外狀況的方法。

## <a name="example"></a>範例
下列範例顯示違反此規則的類型，以及可正確`catch`執行區塊的類型。

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>相關規則
[CA2200重新擲回以保留堆疊詳細資料](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)