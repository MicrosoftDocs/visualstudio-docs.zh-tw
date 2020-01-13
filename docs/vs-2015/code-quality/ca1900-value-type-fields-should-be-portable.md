---
title: CA1900 實：實數值型別欄位應該是可移植的 |Microsoft Docs
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
ms.openlocfilehash: 23b5705b7ee81e56945050fe63dd2f086894bd08
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917923"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900：實值類型欄位應該為可移植的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱[ca1900 實：數值型別欄位應該是可移植](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable)的。

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|分類|Microsoft 可攜性|
|中斷變更|中斷-如果欄位可以在元件外部顯示。<br /><br /> 不中斷-如果在元件外部看不到該欄位。|

## <a name="cause"></a>原因
 此規則會檢查在64位作業系統上封送處理至未受管理的程式碼時，以明確配置宣告的結構是否會正確對齊。 IA-64 不允許未配置的記憶體存取，如果未修正此違規，進程將會損毀。

## <a name="rule-description"></a>規則描述
 具有明確配置的結構（包含未對齊的欄位）會導致64位作業系統當機。

## <a name="how-to-fix-violations"></a>如何修正違規
 小於8個位元組的所有欄位都必須有其大小倍數的位移，而且8個位元組以上的欄位必須有8個倍數的位移。 另一個解決方法是使用 `LayoutKind.Sequential`，而不是 `LayoutKind.Explicit`（如果合理的話）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在發生錯誤時，才應該抑制此警告。
