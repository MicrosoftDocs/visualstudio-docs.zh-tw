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
ms.openlocfilehash: 47bbb39cadb6a092f71ebd7b3907f34fcc2782ce
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842055"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716:識別項名稱不應該和關鍵字相符

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

命名空間、 類型、 名稱或虛擬或介面成員符合保留的關鍵字，以程式設計的語言。

根據預設，此規則只會查看外部可見的命名空間、 類型和成員，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

命名空間、 類型識別項和虛擬和介面成員不應該符合 common language runtime 為目標的語言所定義的關鍵字。 根據所使用的語言和關鍵字，編譯器錯誤和模稜兩可會讓程式庫難以使用。

此規則會檢查針對下列語言版本的關鍵字：

- Visual Basic
- C#
- C++/CLI

不區分大小寫的比較使用 Visual Basic 關鍵字，並用其他語言的區分大小寫比較。

## <a name="how-to-fix-violations"></a>如何修正違規

名稱，不會出現在清單中選取的關鍵字。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您已經相信識別碼不會混淆的 API，使用者和程式庫是可用於在.NET 中的所有可用語言，您可以隱藏此規則的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

此類別 （命名） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。