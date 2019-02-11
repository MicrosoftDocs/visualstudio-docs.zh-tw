---
title: CA1702:複合字應該使用正確的大小寫
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942761"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702:複合字應該使用正確的大小寫

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|分類|Microsoft.Naming|
|中斷變更|組件中斷時引發。<br /><br /> 非-中斷-引發時的類型參數。|

## <a name="cause"></a>原因

識別項的名稱包含多個單字，而其中至少有一個單字是大小寫不正確的複合字。

## <a name="rule-description"></a>規則描述

識別項的名稱會分割成文字為基礎的大小寫。 每個連續的兩個字組合會檢查 Microsoft 拼字檢查程式庫。 如果辨識出它是，識別項會產生規則的違規情形。 造成違規的複合字的範例是"CheckSum"和"MultiPart 」，這應該使用的大小寫為"Checksum"和"Multipart"，分別。 因為前一個常見的用法，幾個例外狀況內建規則，以及數個單字會加上旗標，例如"工具列"和"Filename"，，應該使用的大小寫成兩個不同的單字 （在此情況下，在"工具列"和"FileName"）。

命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規

是正確的大小寫，請變更名稱。

## <a name="language"></a>語言

拼字檢查工具目前會檢查只會針對英文版為基礎的文化特性的字典。 您可以加入，以變更您的專案在專案檔中的文化特性**CodeAnalysisCulture**項目。

例如: 

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 如果您將文化特性設定為以英文為基礎的文化特性以外的任何項目時，此程式碼分析規則是以無訊息模式停用。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，如果拼字檢查字典中，所能辨識的複合字的兩個部分，且其目的是要使用兩個字。

## <a name="related-rules"></a>相關的規則

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708:識別項應該不僅為大小寫不同](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>另請參閱

- [命名方針](/dotnet/standard/design-guidelines/naming-guidelines)
- [大小寫慣例](/dotnet/standard/design-guidelines/capitalization-conventions)