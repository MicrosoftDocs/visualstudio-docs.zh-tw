---
title: CA1721：屬性名稱不應該與 get 方法相符 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 77ec48a1164c7065ba5033ef51eb704b8361dc1c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544452"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721:屬性名稱不應該和其中有 get 的方法名稱相符
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或 protected 成員的名稱以 ' Get ' 開頭，否則會符合公用或受保護屬性的名稱。 例如，包含名為 ' GetColor ' 之方法的類型和名為 ' Color ' 的屬性會違反此規則。

## <a name="rule-description"></a>規則描述
 Get 方法和屬性的名稱應該清楚區別其功能。

 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少學習新軟體程式庫所需的時間，並提高客戶對於開發 managed 程式碼的專業知識而開發之程式庫的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
 請變更名稱，使其不符合前面加上 ' Get ' 之方法的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

> [!NOTE]
> 如果 Get 方法是藉由執行 IExtenderProvider 介面所造成，則可能會排除這個警告。

## <a name="example"></a>範例
 下列範例包含違反此規則的方法和屬性。

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1024:建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)
