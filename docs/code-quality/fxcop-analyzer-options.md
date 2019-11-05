---
title: FxCop 分析器設定選項
ms.date: 09/23/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5ac9c395936ae23bdf94e006a002fb994d8c8cd
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568794"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>FxCop 分析器的規則範圍選項

某些 FxCop 分析器規則可讓您精簡程式碼基底中應該套用的部分。 此頁面會列出可用的範圍設定選項、其允許的值，以及它們可以套用的規則。 若要使用這些選項，請在[EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)檔案中指定它們。

這些設定選項可從[CodeAnalysis FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 套件的版本2.6.3 中取得。

> [!TIP]
> 若要查看特定 FxCopAnalyzers 封裝版本可用的完整選項清單，請查看*套件的檔資料夾中*的*分析器 Configuration.md*檔案。 檔案位於 *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<版本\>\documentation\Analyzer Configuration.md*。 此設定檔檔案包含在套件的每個版本中，從版本2.6.5 開始。 以下是在*分析器 Configuration.md*檔中記載選項的範例：
>
> 選項名稱： `sufficient_IterationCount_for_weak_KDF_algorithm`\
> 選項值：整數值 \
> 預設值：針對每個可設定的規則（預設為最多規則為 ' 100000 '） \
> 範例：`dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| 說明 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 要分析之 API 介面的哪個部分 | `public`<br/>`internal` 或 `friend`<br/>`private`<br/>`all`<br/><br/>以逗號（，）分隔多個值 | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003 必須](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024 建議](ca1024-use-properties-where-appropriate.md)<br/>[CA1027 必須](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030 建議](ca1030-use-events-where-appropriate.md)<br/>[CA1036 必須](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043 必須](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063 必須](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802 建議](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217.md)<br/>[CA2225](ca2225.md)<br/>[CA2226](ca2226.md)<br/>[CA2231](ca2231.md)<br/>[CA2234 必須](ca2234.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| 說明 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要忽略不會傳回值的非同步方法 | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> 在 [版本 2.6.3] 和舊版的分析器套件中，此選項的名稱為 `skip_async_void_methods`。

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| 說明 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要排除規則中的單一字元[類型參數](/dotnet/csharp/programming-guide/generics/generic-type-parameters)，例如，中的 `S` `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> 在 [版本 2.6.3] 和舊版的分析器套件中，此選項的名稱為 `allow_single_letter_type_parameters`。

## <a name="output_kind"></a>output_kind

| 說明 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 指定要分析專案中產生此類型元件的程式碼 | <xref:Microsoft.CodeAnalysis.OutputKind> 列舉的一或多個欄位<br/><br/>以逗號（，）分隔多個值 | 所有輸出類型 | [CA2007](ca2007.md) |
