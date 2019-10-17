---
title: CA1711：識別項名稱不應該使用不正確的後置字元
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a2ae438091c55c9e0e6b14350ca2527907ab33c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443915"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711：識別項名稱不應該使用不正確的後置字元

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|分類|Microsoft. 命名|
|重大變更|中斷|

## <a name="cause"></a>原因

識別碼的尾碼不正確。

根據預設，此規則只會查看外部可見的識別碼，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

依照慣例，只有擴充特定基底類型或會執行特定介面的類型名稱，或是從這些類型衍生的類型，才應該以特定的保留尾碼做為結尾。 其他類型名稱不得使用這些保留的後置字元。

下表列出保留尾碼，以及與它們相關聯的基底類型和介面。

|尾碼|基底類型/介面|
|------------|--------------------------|
|屬性|<xref:System.Attribute?displayProperty=fullName>|
|集合|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|字典|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|事件處理常式委派|
|例外|<xref:System.Exception?displayProperty=fullName>|
|權限|<xref:System.Security.IPermission?displayProperty=fullName>|
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|
|堆疊|<xref:System.Collections.Stack?displayProperty=fullName>|
|資料流|<xref:System.IO.Stream?displayProperty=fullName>|

此外，**不**應使用下列尾碼：

- `Delegate`

- `Enum`

- `Impl` （改用 `Core`）

- `Ex` 或類似的尾碼，以與相同類型的舊版進行區別

命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規

請從類型名稱中移除尾碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

除非後置字元在應用程式定義域中具有明確的意義，否則請不要隱藏這項規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1711.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（命名）來設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相關規則

- [CA1710：識別項應該使用正確的後置字元](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>請參閱

- [屬性](/dotnet/standard/design-guidelines/attributes)
- [處理和引發事件](/dotnet/standard/events/index)
