---
title: CA1701：資源字串複合字應該使用正確的大小寫
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: b875a22cf070ac433206e8b404dfd71aa64d3acd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701：資源字串複合字應該使用正確的大小寫

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|分類|Microsoft.Naming|
|中斷變更|非中斷|

## <a name="cause"></a>原因

資源字串包含不正確的大小寫的複合字。

## <a name="rule-description"></a>規則描述

每個單字的資源字串分割成語彙基元，根據其大小寫。 連續兩個語彙基元的組合都由 Microsoft 拼字檢查程式庫進行檢查。 如果可以辨識，這個字便會產生規則違規。 造成違規的複合字的範例是"CheckSum"和"MultiPart"，這應該大小寫慣例為"Checksum"和"Multipart"，分別。 因為前一個常見的用法，幾個例外狀況內建規則，並且標示數個單字，例如 「 工具列 」 和 「 檔案名稱 」，應該為兩個不同的字大小寫慣例。 在此範例中，就會標示 「 工具列 」 和 「 檔案名稱 」。

命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。

## <a name="how-to-fix-violations"></a>如何修正違規

文字變更為正確的大小寫。

## <a name="change-the-dictionary-language"></a>變更的字典語言

根據預設，會使用拼字檢查程式的英文 (en) 版。 如果您想要變更的拼字檢查程式語言，您可以藉由新增下列其中一種屬性，將因此您*AssemblyInfo.cs*或*AssemblyInfo.vb*檔案：

- 使用<xref:System.Reflection.AssemblyCultureAttribute>指定文化特性，如果您的資源的附屬組件中。
- 使用<xref:System.Resources.NeutralResourcesLanguageAttribute>指定*中性文化特性*如果資源位於相同的組件程式碼組件。

> [!IMPORTANT]
> 如果您將文化特性設定為英文的文化特性以外的任何項目時，此程式碼分析規則以無訊息模式已停用。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可以安全地隱藏此規則的警告，如果拼字檢查字典所辨識的複合字的兩個部分，且其目的是要使用兩個字。

您也可以加入至拼字檢查程式的自訂字典的複合字。 自訂字典中的文字不會造成違規。 如需詳細資訊，請參閱[How to： 自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="related-rules"></a>相關的規則

- [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>另請參閱

- [大小寫慣例](/dotnet/standard/design-guidelines/capitalization-conventions)
- [命名方針](/dotnet/standard/design-guidelines/naming-guidelines)