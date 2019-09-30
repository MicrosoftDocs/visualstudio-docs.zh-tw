---
title: CA1716:識別項名稱不應該和關鍵字相符
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a3f030c9c64d975d93aa2aeee90d37f765a6a63
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234048"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716:識別項名稱不應該和關鍵字相符

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|分類|Microsoft.Naming|
|重大變更|中斷|

## <a name="cause"></a>原因

命名空間、類型或虛擬或介面成員的名稱符合程式設計語言中的保留關鍵字。

根據預設，此規則只會查看外部可見的命名空間、類型和成員，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

命名空間、類型和虛擬和介面成員的識別碼，不應符合以 common language runtime 為目標之語言所定義的關鍵字。 視所使用的語言和關鍵字而定，編譯器錯誤和多義性可能會使程式庫變得很容易使用。

此規則會針對下列語言的關鍵字進行檢查：

- Visual Basic
- C#
- C++/CLI

Visual Basic 關鍵字會使用不區分大小寫比較，而其他語言則會使用區分大小寫比較。

## <a name="how-to-fix-violations"></a>如何修正違規

選取不會出現在關鍵字清單中的名稱。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您確信該識別碼不會混淆 API 的使用者，而且該程式庫可在 .NET 中的所有可用語言中使用，您可以隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（命名）來設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。