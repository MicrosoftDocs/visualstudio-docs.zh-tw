---
title: CA1044：屬性不應為唯寫
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 204108ed86d37594d7debc0a69139a7f2a28a44a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044：屬性不應為唯寫
|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的屬性 set 存取子，但沒有 get 存取子。

## <a name="rule-description"></a>規則描述
 Get 存取子會提供給屬性的讀取權限和 set 存取子提供寫入存取權。 雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。 這是因為讓使用者設定的值，然後防止使用者檢視 值不提供任何安全性。 同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將加入至屬性的 get 存取子。 或者，如果需要唯寫屬性的行為，請考慮將這個屬性轉換成方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 強烈建議您不要隱藏這個規則的警告。

## <a name="example"></a>範例
 在下列範例中，`BadClassWithWriteOnlyProperty`是唯寫屬性的類型。 `GoodClassWithReadWriteProperty` 包含已更正的程式碼。

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]