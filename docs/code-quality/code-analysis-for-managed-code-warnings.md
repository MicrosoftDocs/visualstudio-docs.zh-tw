---
title: Managed 程式碼的程式碼分析警告
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 566b9827f42f646cd9350cfc015a460485212a09
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90094326"
---
# <a name="net-code-analysis-rules"></a>.NET 程式碼分析規則
.NET 程式碼分析提供的規則指出程式碼品質違規或建議，以改善程式碼品質。 這些規則會組織成規則區域，例如設計、當地語系化、效能和安全性。 某些規則專屬於 .NET API 的使用方式，而其餘的規則則是關於一般程式碼品質。 本節提供每個規則的深入討論和範例。

 下表顯示每個診斷所提供的資訊類型。

|Item|描述|
|----------|-----------------|
|類型|規則的 TypeName。|
|RuleId|規則的唯一識別碼。 RuleId 和類別是用來隱藏來源的警告。|
|類別|警告的分類。|
|重大變更|此規則的違規修正是否為中斷變更。 中斷變更表示組件在造成違規的目標上具相依性，且該組件不會使用新的固定版本進行重新編譯，或可能由於此項變更而在執行階段失敗。 如果有多個修正程式，而且至少有一個修正程式是中斷性變更，而一個修正不是，則會同時指定「中斷」和「非中斷」。|
|原因|此特定的 Managed 程式碼讓規則產生警告。|
|描述|討論警告背後的問題。|
|如何修正違規|說明如何變更原始程式碼，以符合規則並避免其產生警告。|
|隱藏警告的時機|描述何時可安全地隱藏此規則的警告。|
|範例程式碼|違反規則的範例與經過更正且符合規則的範例。|
|相關的警告|相關的警告。|

## <a name="in-this-section"></a>本節內容

|類別|描述|
|-|-|
|[依識別碼的規則](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|依 RuleID 列出所有規則|
|[設計規則](../code-quality/design-warnings.md)|支援正確的程式庫設計的規則，如 .NET 設計指導方針所指定。|
|[檔規則](../code-quality/documentation-warnings.md)|透過正確使用 XML 檔批註來支援妥善記錄的程式庫設計的規則。|
|[全球化規則](../code-quality/globalization-warnings.md)|支援全球化程式庫和應用程式的規則。|
|[維護性規則](../code-quality/maintainability-warnings.md)|支援程式庫和應用程式維護的規則。|
|[命名規則](../code-quality/naming-warnings.md)|支援遵循 .NET 設計指導方針之命名慣例的規則。|
|[效能規則](../code-quality/performance-warnings.md)|支援高效能程式庫和應用程式的規則。|
|[可攜性和互通性規則](../code-quality/interoperability-warnings.md)|支援跨不同平臺的可攜性，以及與 COM 用戶端互動的規則。|
|[發佈規則](../code-quality/publish-warnings.md)|支援適當發行 .NET 應用程式的規則。|
|[可靠性規則](../code-quality/reliability-warnings.md)|支援程式庫和應用程式可靠性的規則，例如正確的記憶體和執行緒使用量。|
|[安全性規則](../code-quality/security-warnings.md)|支援更安全的程式庫和應用程式的規則。|
|[使用規則](../code-quality/usage-warnings.md)|支援適當使用 .NET 的規則。|
