---
title: CA1810 必須：將參考型別靜態欄位初始化為內嵌 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c4ad2f4db9290430bb8a378bd264078370ca7b66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543828"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810:必須將參考類型內部的靜態欄位初始化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|類別|Microsoft。效能|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 參考型別會宣告明確的靜態函式。

## <a name="rule-description"></a>規則描述
 當類型宣告明確的靜態建構函式時，Just-In-Time (JIT) 編譯器會將檢查加入至類型的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。 當存取任何靜態成員或建立型別的實例時，就會觸發靜態初始化。 不過，如果您宣告類型的變數，但不使用它，則不會觸發靜態初始化，這在初始化變更全域狀態時可能很重要。

 當所有靜態資料都內嵌初始化且未宣告明確的靜態函式時，Microsoft 中繼語言 (MSIL) 編譯器會將 `beforefieldinit` 旗標和隱含靜態函式（可初始化靜態資料）新增至 msil 型別定義。 當 JIT 編譯程式遇到旗標時 `beforefieldinit` ，大部分的時候都不會加入靜態的檢查函式檢查。 靜態初始化保證會在存取任何靜態欄位之前，而不是在叫用靜態方法或實例的函式之前的某個時間進行。 請注意，在宣告類型的變數之後，任何時間都可以進行靜態初始化。

 靜態建構函式檢查會降低效能。 靜態的函式通常只會用來初始化靜態欄位，在這種情況下，您必須確定靜態初始化是在第一次存取靜態欄位之前進行。 此 `beforefieldinit` 行為適用于這些和其他大部分的類型。 只有在靜態初始化影響全域狀態，且下列其中一項為真時，才會是不當的：

- 全域狀態的影響相當昂貴，如果未使用類型，則不需要。

- 您可以存取全域狀態效果，而不需要存取型別的任何靜態欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果效能不成問題，可放心隱藏此規則的警告;或者，如果靜態初始化所造成的全域狀態變更很昂貴，或必須保證在呼叫型別的靜態方法或建立型別的實例之前發生。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別， `StaticConstructor` 以及 `NoStaticConstructor` 會以內嵌初始化取代靜態函式以滿足規則的型別。

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 請注意，在 `beforefieldinit` 類別的 MSIL 定義上新增旗標 `NoStaticConstructor` 。

 **。 class public auto ansi StaticConstructor**會**擴充 [mscorlib.dll] system.object** 
 **{** 
 **}//StaticConstructor 類別的結尾** 
 **。 class public auto ansi beforefieldinit NoStaticConstructor**會**擴充 [mscorlib.dll] system.object** 
 **{** 
 **}//class NoStaticConstructor 的結尾**
## <a name="related-rules"></a>相關規則
 [CA2207:必須將實值類型的靜態欄位內嵌初始化](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
