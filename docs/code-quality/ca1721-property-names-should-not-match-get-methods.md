---
title: CA1721：屬性名稱不能和其中有 get 的方法名稱相符
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29db0561f15a16bf9b449f03f209feedf80dbd88
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721：屬性名稱不能和其中有 get 的方法名稱相符
|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的成員名稱開頭為 'Get'，否則符合名稱的公用或受保護的屬性。 例如，此型別包含名為 'GetColor' 和名為 'Color' 屬性的方法違反此規則。

## <a name="rule-description"></a>規則描述
 Get 方法和屬性應該清楚區別其功能的名稱。

 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要學習新的軟體程式庫，而且會增加的程式庫由具備專業知識在開發 managed 程式碼開發的客戶信心的時間。

## <a name="how-to-fix-violations"></a>如何修正違規
 變更名稱，使它不符合加上 'Get' 方法的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

> [!NOTE]
>  如果 Get 方法因實作 IExtenderProvider 介面，可能會排除這個警告。

## <a name="example"></a>範例
 下列範例包含的方法和違反此規則的屬性。

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)