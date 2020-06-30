---
title: CA1409： Com 可見類型應該是可自行執行 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547325"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409:Com 可見類型應該是可建立的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|類別|Microsoft. 互通性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 特別標示為「元件物件模型（COM）可見」的參考型別包含公用參數化的函式，但不包含公用預設（無參數）的函式。

## <a name="rule-description"></a>規則描述
 COM 用戶端無法建立沒有公用預設函式的類型。 不過，如果有另一種方法可用來建立型別，並將它傳遞給用戶端（例如，透過方法呼叫的傳回值），則 COM 用戶端仍然可以存取型別。

 此規則會忽略衍生自的類型 <xref:System.Delegate?displayProperty=fullName> 。

 根據預設，COM 會看到下列內容：元件、公用類型、公用類型中的公用實例成員，以及公用實數值型別的所有成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請新增公用預設的函式，或 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 從類型移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果提供其他方式來建立物件並將其傳遞給 COM 用戶端，則可以安全地隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1017:組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱
 [限定用於互通的 .Net 類型](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)可[與非受控程式碼](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)交互操作
