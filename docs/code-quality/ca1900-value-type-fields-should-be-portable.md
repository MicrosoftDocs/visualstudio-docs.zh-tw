---
title: CA1900：實值類型欄位應該為可移植的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9add21d932f7685a2dee214f396b2cbda089a5a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917211"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900：實值類型欄位應該為可移植的
|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|分類|Microsoft.Portability|
|中斷變更|中斷-可以看到在組件外部的欄位。<br /><br /> 非中斷-如果欄位不是組件外部可見。|

## <a name="cause"></a>原因
 此規則會檢查封送處理至 unmanaged 程式碼在 64 位元作業系統上時具有明確配置宣告的結構會正確地對齊。 Ia-64 不允許存取未配置的記憶體和處理程序將會損毀，如果沒有修正這種違規。

## <a name="rule-description"></a>規則描述
 具有明確配置，其中包含不當欄位會造成當機，在 64 位元作業系統上的結構。

## <a name="how-to-fix-violations"></a>如何修正違規
 小於 8 個位元組的所有欄位都必須是其大小的倍數的位移和 8 個位元組的欄位或多個都必須是 8 的倍數的位移。 另一個解決方案是使用`LayoutKind.Sequential`而不是`LayoutKind.Explicit`，如果合理。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 在發生錯誤時，才應該隱藏這個警告。