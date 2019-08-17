---
title: CA1051:不要宣告可見的執行個體欄位
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5dd8a4b2d0b32a8c52f75dee6fd765a7ea6ec9a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547563"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051:不要宣告可見的執行個體欄位

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

類型具有非私用實例欄位。

根據預設, 此規則只會查看外部可見的類型, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

欄位的主要用法應該是當做實作詳細資料。 欄位應該是`private`或`internal` , 而且應該使用屬性來公開。 存取欄位的方式很簡單, 因為它是用來存取欄位, 而屬性存取子中的程式碼可能會隨著類型的擴充功能而變更, 而不會引入中斷性變更。 只傳回私用或內部欄位值的屬性, 已經過優化, 可在存取欄位時進行比對。在屬性上使用外部可見的欄位, 幾乎不會有太大的效能提升。

`public`外部可見指的是`protected`、和`protected internal` (`Public` `Protected`Visual Basic 中的`Protected Friend` 、和) 存取範圍層級。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規, 請將欄位`private`設`internal`為或, 並使用外部可見的屬性加以公開。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 外部可見欄位不會提供屬性無法使用的任何好處。 此外, 公用欄位無法受到[連結要求](/dotnet/framework/misc/link-demands)的保護。 請[參閱 CA2112:受保護的類型不應該](../code-quality/ca2112-secured-types-should-not-expose-fields.md)公開欄位。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (設計) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示違反此規則的`BadPublicInstanceFields`類型 ()。 `GoodPublicInstanceFields`顯示已更正的程式碼。

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>相關規則

- [CA2112受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>另請參閱

- [連結要求](/dotnet/framework/misc/link-demands)