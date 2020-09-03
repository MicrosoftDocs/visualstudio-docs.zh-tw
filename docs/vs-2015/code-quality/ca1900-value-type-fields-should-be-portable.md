---
title: CA1900 實：實數值型別欄位應該為可移植 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ece4788a277bfc4d16568d4014f9eae2ed4de33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545271"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900:實值類型欄位應該為可移植的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [ca1900 實：實數值型別欄位應該是可移植](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable)的。

|Item|值|
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|類別|Microsoft 可攜性|
|中斷變更|中斷-如果可以在元件外部看到欄位。<br /><br /> 非中斷-如果在元件外部看不到欄位，則為。|

## <a name="cause"></a>原因
 此規則會檢查在64位作業系統上封送處理至非受控碼時，以明確配置宣告的結構是否正確對齊。 IA-64 不允許未配置的記憶體存取，而且如果未修正此違規，進程將會損毀。

## <a name="rule-description"></a>規則描述
 具有明確配置（包含未對齊的欄位）的結構會在64位作業系統上造成當機。

## <a name="how-to-fix-violations"></a>如何修正違規
 小於8個位元組的所有欄位都必須有其大小倍數的位移，而8個位元組或更多的欄位必須有倍數的位移，而這些位移是8的倍數。 另一個解決方案是在 `LayoutKind.Sequential` 合理的情況下使用而不是 `LayoutKind.Explicit` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在錯誤發生時，才應該隱藏此警告。
