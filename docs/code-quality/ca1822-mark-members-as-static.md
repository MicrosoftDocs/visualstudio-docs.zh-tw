---
title: CA1822：將成員標記為靜態
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 498a3638a02891683aff1b343431418d1a82bab0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1822-mark-members-as-static"></a>CA1822：將成員標記為靜態
|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|分類|Microsoft.Performance|
|中斷變更|非中斷-成員不是組件外部可見變更不論您進行。 非中斷-如果您只要變更成員的執行個體成員為`this`關鍵字。<br /><br /> 中斷-如果您將成員從執行個體成員變更為靜態成員，而且它是在組件外部可見。|

## <a name="cause"></a>原因
 不會存取執行個體資料成員未標記為 static (在中共用[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="rule-description"></a>規則描述
 不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared)。 將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。 發出非虛擬呼叫位置將導致在執行階段針對每個呼叫，以確保目前物件指標為非 null 的檢查。 這可讓您獲得可觀的效能重視效能的程式碼。 在某些情況下，無法存取目前的物件執行個體就表示正確性發生問題。

## <a name="how-to-fix-violations"></a>如何修正違規
 標記為靜態成員 (或共用中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 或使用 'this '/' Me' 在方法主體，如果適當的話。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏先前提供之程式碼修正程式將會是一項重大變更這項規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812：避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)