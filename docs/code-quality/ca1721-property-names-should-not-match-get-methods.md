---
title: CA1721:屬性名稱不應該和其中有 get 的方法名稱相符
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 44028caf027191846fa653db06abbe4027fdde8d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547085"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721:屬性名稱不應該和其中有 get 的方法名稱相符

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

成員的名稱開頭為 ' Get ', 否則會符合屬性的名稱。 例如, 包含名為 ' GetColor ' 之方法的類型和名為 ' Color ' 的屬性會造成規則違規。

根據預設, 此規則只會查看外部可見的成員和屬性, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

"Get" 方法和屬性的名稱應該清楚區別其功能。

命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這種一致性可減少學習新軟體程式庫所需的時間, 並增加客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規

請變更名稱, 使其不符合前面加上 ' Get ' 之方法的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

> [!NOTE]
> 如果「Get」方法是藉由執行 IExtenderProvider 介面所造成, 則可能會排除此警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (命名) 來設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例包含違反此規則的方法和屬性。

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>相關規則

- [CA1024 建議適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)