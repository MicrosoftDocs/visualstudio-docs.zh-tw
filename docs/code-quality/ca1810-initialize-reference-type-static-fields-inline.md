---
title: CA1810:必須將參考類型內部的靜態欄位初始化
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 42877ea2b3b42f0fc9bed5c88a6809ba31cab3e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996918"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810:必須將參考類型內部的靜態欄位初始化

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 參考型別宣告明確靜態建構函式。

## <a name="rule-description"></a>規則描述
 當類型宣告明確的靜態建構函式時，Just-In-Time (JIT) 編譯器會將檢查加入至類型的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。 當存取任何靜態成員，或建立類型的執行個體時，會觸發靜態初始設定。 不過，如果您宣告的型別變數，但請不要使用它，它可以是很重要，如果初始化變更全域狀態，並不觸發靜態初始設定。

 當所有靜態資料會初始化的內嵌並不宣告明確靜態建構函式時，Microsoft intermediate language (MSIL) 編譯器新增`beforefieldinit`旗標和隱含靜態建構函式，用來初始化靜態資料、 MSIL 類型定義。 當 JIT 編譯器遇到`beforefieldinit`旗標，大部分的靜態建構函式檢查不會加入的時間。 發生某個時間點存取任何靜態欄位之前，但靜態方法或執行個體建構函式會叫用之前，不保證靜態初始設定。 請注意，靜態初始設定可能會發生在任何時間之後宣告類型的變數。

 靜態建構函式檢查會降低效能。 通常會使用靜態建構函式，只是用來初始化靜態欄位的第一次存取之前發生在哪個情況下，您必須只確定靜態初始設定的靜態欄位。 `beforefieldinit`行為是適用於這些和其他大部分的類型。 當靜態初始設定會影響全域狀態，而且下列其中一項條件成立時才不適用：

- 全域狀態上的效果很昂貴，而且不需要，如果未使用的型別。

- 全域狀態效果可以存取而不需存取類型的任何靜態欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，如果不是問題; 這種效能。或如果由靜態初始設定所造成的全域狀態變更是相當費時，或必須保證會呼叫類型的靜態方法，或建立之型別的執行個體之前發生。

## <a name="example"></a>範例

下列範例顯示的型別`StaticConstructor`，，違反此規則，並為型別， `NoStaticConstructor`，可取代符合規則的內嵌初始化靜態建構函式。

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

請注意新增`beforefieldinit`旗標的 MSIL 定義`NoStaticConstructor`類別。

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>相關的規則

- [CA2207:初始化實值類型的靜態欄位內嵌](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)