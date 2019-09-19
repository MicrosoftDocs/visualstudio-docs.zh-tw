---
title: Managed 程式碼的程式碼分析警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d3a8c087e6b07bad34c76865bbbb852d115e055
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062428"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Managed 程式碼的程式碼分析警告
Managed 程式碼分析工具會提供警告，指出 Managed 程式碼程式庫中的規則違規。 警告會組織成規則區域，例如設計、當地語系化、效能與安全性。 每一項警告皆表示 Managed 程式碼分析規則的違規。 本節針對每個 Managed 程式碼分析警告，提供深入的討論與範例。

 下表顯示針對每個警告所提供的資訊類型。

|項目|描述|
|----------|-----------------|
|類型|規則的 TypeName。|
|CheckId|規則的唯一識別碼。 Checkid 與 Category 是用於原始程式檔內的警告隱藏。|
|Category|警告的分類。|
|中斷變更|此規則的違規修正是否為中斷變更。 中斷變更表示組件在造成違規的目標上具相依性，且該組件不會使用新的固定版本進行重新編譯，或可能由於此項變更而在執行階段失敗。 當有多項修正可用，且至少有一個是中斷變更而有一個不是時，便會指定「中斷」與「非中斷」。|
|原因|此特定的 Managed 程式碼讓規則產生警告。|
|說明|討論警告背後的問題。|
|如何修正違規|說明如何變更原始程式碼，以符合規則並避免其產生警告。|
|隱藏警告的時機|描述何時可安全地隱藏此規則的警告。|
|範例程式碼|違反規則的範例與經過更正且符合規則的範例。|
|相關的警告|相關的警告。|

## <a name="in-this-section"></a>本節內容

|||
|-|-|
|[依 CheckId 分類的警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|依據 CheckId 列出警告|
|[加密警告](../code-quality/cryptography-warnings.md)|此警告透過正確使用加密來支援更安全的程式庫與應用程式。|
|[設計警告](../code-quality/design-warnings.md)|支援 .NET 設計指導方針所指定的正確程式庫設計的警告。|
|[檔警告](../code-quality/documentation-warnings.md)|警告，透過正確使用 XML 檔批註，支援妥善記載的程式庫設計。|
|[全球化警告](../code-quality/globalization-warnings.md)|此警告支援全球化程式庫與應用程式。|
|[互通性警告](../code-quality/interoperability-warnings.md)|此警告支援與 COM 用戶端互動。|
|[維護性警告](../code-quality/maintainability-warnings.md)|此警告支援程式庫與應用程式維護。|
|[Mobility Warnings](../code-quality/mobility-warnings.md)|此警告支援有效率的用電量。|
|[命名警告](../code-quality/naming-warnings.md)|支援遵循 .NET 設計指導方針之命名慣例的警告。|
|[效能警告](../code-quality/performance-warnings.md)|此警告支援高效能程式庫與應用程式。|
|[Portability Warnings](../code-quality/portability-warnings.md)|此警告跨平台支援可攜性。|
|[可靠性警告](../code-quality/reliability-warnings.md)|此警告支援程式庫與應用程式的可靠性，例如記憶體與執行緒的正確用法。|
|[安全性警告](../code-quality/security-warnings.md)|此警告支援更安全的程式庫與應用程式。|
|[用法警告](../code-quality/usage-warnings.md)|支援適當使用 .NET 的警告。|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|若程式碼分析原則在簽入時不符合，會發生此錯誤。|
