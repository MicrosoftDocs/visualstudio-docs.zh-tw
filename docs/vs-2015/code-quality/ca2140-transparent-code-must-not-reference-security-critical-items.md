---
title: CA2140：透明程式碼不能參考安全性關鍵專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6f11125f43fd06b0442d1c40cbd4da41e346fd1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546454"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140:透明程式碼不可以參考安全性關鍵項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法：

- 處理安全性重大安全性例外狀況類型

- 具有標示為安全性關鍵類型的參數

- 具有具有安全性關鍵條件約束的泛型參數

- 具有安全性關鍵類型的本機變數

- 參考標示為安全性關鍵的類型

- 呼叫標記為安全性關鍵的方法

- 參考標示為安全性關鍵的欄位

- 傳回標示為安全性關鍵的類型

## <a name="rule-description"></a>規則描述
 以屬性標示的程式碼專案 <xref:System.Security.SecurityCriticalAttribute> 是安全性關鍵。 透明方法不能使用安全性關鍵項目。 如果透明類型嘗試使用安全性關鍵類型 <xref:System.TypeAccessException> ， <xref:System.MethodAccessException> <xref:System.FieldAccessException> 則會引發、或。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請執行下列其中一項動作：

- 將使用安全性關鍵程式碼的程式碼元素標示為 <xref:System.Security.SecurityCriticalAttribute> 屬性

     \- 或 -

- <xref:System.Security.SecurityCriticalAttribute>從標示為安全性關鍵的程式碼元素中移除屬性，並使用或屬性來標示 <xref:System.Security.SecuritySafeCriticalAttribute> <xref:System.Security.SecurityTransparentAttribute> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，透明方法會嘗試參考安全性關鍵泛型集合、安全性關鍵字段和安全性關鍵方法。

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
