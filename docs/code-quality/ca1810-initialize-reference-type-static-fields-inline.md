---
title: ： Ca1810 必須初始化參考類型的靜態欄位 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e49e346594a8546c6808e718ee7b4d7c78c10b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810：必須初始化參考類型內部的靜態欄位
|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 參考類型宣告明確靜態建構函式。  
  
## <a name="rule-description"></a>規則描述  
 當類型宣告明確的靜態建構函式時，Just-In-Time (JIT) 編譯器會將檢查加入至類型的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。 當存取任何靜態成員，或建立類型的執行個體時，系統會觸發靜態初始設定。 不過，如果您宣告類型的變數，但不要使用它，它可以是重要事項如果初始化變更全域狀態，會不觸發靜態初始設定。  
  
 Microsoft intermediate language (MSIL) 編譯器後的所有靜態資料初始化的內嵌未宣告明確靜態建構函式，加入`beforefieldinit`旗標和隱含靜態建構函式，用來初始化靜態資料、 MSIL 類型定義。 當 JIT 編譯器遇到`beforefieldinit`旗標，大部分的情況下不會新增靜態建構函式檢查。 發生在一些時間，存取任何靜態欄位之前，但只有在叫用靜態方法或執行個體建構函式之前不保證靜態初始設定。 請注意，靜態初始設定可能會發生在任何時間之後宣告類型的變數。  
  
 靜態建構函式檢查會降低效能。 通常靜態建構函式是只能用來初始化發生之前的靜態欄位的第一次存取的情況下，您必須只確定靜態初始設定的靜態欄位。 `beforefieldinit`行為是適用於這些和其他大部分的類型。 當靜態初始設定會影響全域狀態，而且下列其中一項條件成立時才不適用：  
  
-   全域狀態上的效果是高度耗費資源，而且不需要，如果未使用型別。  
  
-   全域狀態效果可以存取而不存取任何類型的靜態欄位。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 安全地隱藏此規則的警告，如果效能不重要的考量。或是全域狀態變更所造成的靜態初始設定是相當費時，否則必須保證之前呼叫靜態方法的型別，或建立類型的執行個體。  
  
## <a name="example"></a>範例  
 下列範例顯示型別， `StaticConstructor`，違反此規則，並為型別，`NoStaticConstructor`的靜態建構函式取代符合規則的內嵌初始化。  
  
 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 請注意新增`beforefieldinit`旗標的 MSIL 定義`NoStaticConstructor`類別。  
  
 **公用.class 自動 ansi StaticConstructor**  
 **擴充 [mscorlib]System.Object**  
**{**  
**} / 結束 / StaticConstructor 類別的**  
**.class 公用自動 ansi beforefieldinit NoStaticConstructor**  
 **擴充 [mscorlib]System.Object**  
**{**  
**} / 結束 / NoStaticConstructor 類別的**   
## <a name="related-rules"></a>相關的規則  
 [CA2207：必須初始化實值型別的靜態欄位內嵌](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)