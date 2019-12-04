---
title: FxCop 分析器設定選項
ms.date: 09/23/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2d97552a79b520bd522cb8ec768d7d36fe2fb052
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74809804"
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

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 要分析之 API 介面的哪個部分 | `public`<br/>`internal` 或 `friend`<br/>`private`<br/>`all`<br/><br/>以逗號（，）分隔多個值 | `public` | [CA1000](ca1000.md) [ca1003 必須](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [ca1024 建議](ca1024.md) [ca1027 必須](ca1027.md) [CA1028](ca1028.md)<br/>[Ca1030 建議](ca1030.md) [ca1036 必須](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[Ca1043 必須](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[Ca1063 必須](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [ca1801 必須](ca1801.md)<br/>[Ca1802 建議](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [ca2234 必須](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要忽略不會傳回值的非同步方法 | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> 在 [版本 2.6.3] 和舊版的分析器套件中，此選項的名稱為 `skip_async_void_methods`。

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要排除規則中的單一字元[類型參數](/dotnet/csharp/programming-guide/generics/generic-type-parameters)，例如，中的 `S` `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> 在 [版本 2.6.3] 和舊版的分析器套件中，此選項的名稱為 `allow_single_letter_type_parameters`。

## <a name="output_kind"></a>output_kind

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 指定要分析專案中產生此類型元件的程式碼 | <xref:Microsoft.CodeAnalysis.OutputKind> 列舉的一或多個欄位<br/><br/>以逗號（，）分隔多個值 | 所有輸出類型 | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 為應該分析的 Api 指定必要的修飾詞 | 下列允許的修飾詞資料表中的一或多個值<br/><br/>以逗號（，）分隔多個值 | 視每個規則而定 | [CA1802 建議](ca1802.md) |

| 允許的修飾詞 | 總結 |
| --- | --- |
| `none` | 無修飾詞需求 |
| `static` 或 `Shared` | 必須宣告為 ' static ' （在 Visual Basic 中為 ' Shared '） |
| `const` | 必須宣告為 ' const ' |
| `readonly` | 必須宣告為 ' readonly ' |
| `abstract` | 必須宣告為 ' abstract ' |
| `virtual` | 必須宣告為 ' virtual ' |
| `override` | 必須宣告為 ' override ' |
| `sealed` | 必須宣告為 ' sealed ' |
| `extern` | 必須宣告為 ' extern ' |
| `async` | 必須宣告為 ' async ' |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要略過擴充方法之 `this` 參數的分析 | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| Null 檢查驗證方法的名稱，可驗證傳遞至方法的引數是否為非 null | 允許的方法名稱格式（以 `|`分隔）：<br/> -僅限方法名稱（包含所有具有名稱的方法，不論包含的類型或命名空間為何）<br/> -符號的[檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)中的完整名稱，具有選擇性的 `M:` 前置詞 | None | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 其他字串格式化方法的名稱 | 允許的方法名稱格式（以 `|`分隔）：<br/> -僅限方法名稱（包含所有具有名稱的方法，不論包含的類型或命名空間為何）<br/> -符號的[檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)中的完整名稱，具有選擇性的 `M:` 前置詞 | None | [CA2241 必須](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 類型的名稱，因此會排除類型及其所有衍生類型以進行分析 | 允許的符號名稱格式（以 `|`分隔）：<br/> -僅限類型名稱（包含所有具有名稱的類型，不論包含的類型或命名空間為何）<br/> -符號的[檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)中的完整名稱，具有選擇性的 `T:` 前置詞 | None | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 排除以進行分析的符號名稱 | 允許的符號名稱格式（以 `|`分隔）：<br/> -僅限符號名稱（包含所有具有名稱的符號，不論包含的類型或命名空間為何）<br/> -符號[檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整名稱。 每個符號名稱都需要符號種類前置詞，例如 "M：" 前置詞用於方法，"T：" 首碼用於類型，"N：" 前置詞用於命名空間等等。<br/> - `.ctor` 用於靜態的函式和 `.cctor` | None | [CA1062](ca1062.md) [CA1303](ca1303.md) [ca2000 必須](ca2000.md) [ca2100 必須](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 在分析內容中不允許的符號名稱 | 允許的符號名稱格式（以 `|`分隔）：<br/> -僅限符號名稱（包含所有具有名稱的符號，不論包含的類型或命名空間為何）<br/> -符號[檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整名稱。 每個符號名稱都需要符號種類前置詞，例如 "M：" 前置詞用於方法，"T：" 首碼用於類型，"N：" 前置詞用於命名空間等等。<br/> - `.ctor` 用於靜態的函式和 `.cctor` | None | [CA1031](ca1031.md) |

