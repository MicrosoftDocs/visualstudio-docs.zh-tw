---
title: CA2130:安全性關鍵常數應該是透明的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d3b5389bb080dee6e550c4bc0e6c035fd15db2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154325"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130:安全性關鍵常數應該是透明的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 常數欄位或列舉的成員會標示<xref:System.Security.SecurityCriticalAttribute>。

## <a name="rule-description"></a>規則描述
 因為編譯器內嵌常數的值，所以沒有針對常數值強制透明度，因此在執行階段不需要查詢。 常數欄位應該具備安全性透明，程式碼檢閱者才不會假設透明程式碼無法存取常數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除的 SecurityCritical 屬性值的欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，列舉值`EnumWithCriticalValues.CriticalEnumValue`和常數`CriticalConstant`會引發此警告。 若要修正問題，請移除 [`SecurityCritical`] 屬性可讓它們的安全性透明。

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]
