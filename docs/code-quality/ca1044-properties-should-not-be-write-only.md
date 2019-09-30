---
title: CA1044:屬性不應該為唯寫的
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0fb424627d88ede6c0677b8c45de4aab487ae498
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235823"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044:屬性不應該為唯寫的

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|分類|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因

屬性具有 set 存取子，但不具有 get 存取子。

根據預設，此規則只會查看公用類型，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

Get 存取子提供屬性的讀取權限，而 set 存取子則提供寫入存取權。 雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。 這是因為讓使用者設定值，然後防止使用者看到此值並不會提供任何安全性。 同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請將 get 存取子新增至屬性。 或者，如果需要僅限寫入屬性的行為，請考慮將此屬性轉換成方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

建議您不要隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1044.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（設計）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

在下列範例中， `BadClassWithWriteOnlyProperty`是具有寫入屬性的類型。 `GoodClassWithReadWriteProperty`包含已更正的程式碼。

[!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
[!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]