---
title: CA1708:識別項名稱不應該只靠大小寫區別
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5098e2feadc6d67c466e31ab19d059ac70c7d833
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547407"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708:識別項名稱不應該只靠大小寫區別

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

當兩個類型、成員、參數或完整命名空間的名稱轉換成小寫時, 兩者都是相同的。

根據預設, 此規則只會查看外部可見的類型、成員和命名空間, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。 例如, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]是廣為使用的不區分大小寫語言。

此規則只會在公開可見的成員上引發。

## <a name="how-to-fix-violations"></a>如何修正違規

當與其他識別碼比較不區分大小寫的方式時, 請選取唯一的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 媒體櫃可能無法在 .NET 中使用所有可用的語言。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca1708.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (命名) 來設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example-of-a-violation"></a>違規的範例

下列範例示範此規則的違規。

[!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>相關規則

- [CA1709識別碼的大小寫應該正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)