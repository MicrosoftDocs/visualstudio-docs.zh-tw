---
title: CA1716:識別項名稱不應該和關鍵字相符
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: e1ecd5fc5163bfcb5a0f217e21b5aab353a074a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972936"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716:識別項名稱不應該和關鍵字相符

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

命名空間、 類型或 viritual 或介面成員的名稱符合保留的關鍵字，以程式設計的語言。

## <a name="rule-description"></a>規則描述

命名空間、 類型識別項和虛擬和介面成員不應該符合 common language runtime 為目標的語言所定義的關鍵字。 根據所使用的語言和關鍵字，編譯器錯誤和模稜兩可會讓程式庫難以使用。

此規則會檢查針對下列語言版本的關鍵字：

- Visual Basic

- C#

- C++/CLI

不區分大小寫的比較來[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]關鍵字和區分大小寫比較，用於其他語言。

## <a name="how-to-fix-violations"></a>如何修正違規

名稱，不會出現在清單中選取的關鍵字。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您說服識別碼不會混淆的 API，使用者和程式庫是使用.NET Framework 中的所有可用語言，您可以隱藏此規則的警告。