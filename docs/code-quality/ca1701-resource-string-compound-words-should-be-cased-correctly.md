---
title: CA1701:資源字串複合字應該使用正確的大小寫
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2cc74bb7d3cc15e593d465a8c8d0d55275954ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841777"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701:資源字串複合字應該使用正確的大小寫

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|分類|Microsoft.Naming|
|中斷變更|非重大|

## <a name="cause"></a>原因

資源字串，包含似乎不正確的大小寫的複合字。

## <a name="rule-description"></a>規則描述

資源字串中的每個單字會分割成權杖為基礎的大小寫。 連續兩個語彙基元的組合都由 Microsoft 拼字檢查程式庫進行檢查。 如果可以辨識，這個字便會產生規則違規。 造成違規的複合字的範例是"CheckSum"和"MultiPart 」，這應該使用的大小寫為"Checksum"和"Multipart"，分別。 由於先前的常見用法，幾個例外狀況內建規則，並標示數個單字，例如"工具列"和"Filename"，應該使用的大小寫成兩個不同的單字。 在此範例中，就會標示 「 工具列 」 且"FileName"。

命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

## <a name="how-to-fix-violations"></a>如何修正違規

文字變更為正確的大小寫。

## <a name="change-the-dictionary-language"></a>變更的字典語言

預設情況下，會使用英文 (en) 版本的拼字檢查程式。 如果您想要變更的拼字檢查程式語言，您可以這樣做加上下列其中一個屬性到您*AssemblyInfo.cs*或是*AssemblyInfo.vb*檔案：

- 使用<xref:System.Reflection.AssemblyCultureAttribute>指定的文化特性，如果您的資源位於附屬組件。
- 使用<xref:System.Resources.NeutralResourcesLanguageAttribute>來指定*中性文化特性*您組件，如果您的資源位於與您的程式碼相同的組件。

> [!IMPORTANT]
> 如果您將文化特性設定為以英文為基礎的文化特性以外的任何項目時，此程式碼分析規則是以無訊息模式停用。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，如果拼字檢查字典所辨識的複合字的兩個部分，且其目的是要使用兩個字。

您也可以新增至拼字檢查程式的自訂字典的複合字。 自訂字典中的文字不會導致違規。 如需詳細資訊，請參閱[＜How to：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="related-rules"></a>相關的規則

- [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708:識別項應該不僅為大小寫不同](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>另請參閱

- [大小寫慣例](/dotnet/standard/design-guidelines/capitalization-conventions)
- [命名方針](/dotnet/standard/design-guidelines/naming-guidelines)