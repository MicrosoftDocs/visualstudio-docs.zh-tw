---
title: 使用 editorconfig 設定 .NET 程式碼品質分析器
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc237082ec1188d71241facead975db1df2cf3af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035426"
---
# <a name="configure-net-code-quality-analysis-with-editorconfig"></a>使用 EditorConfig 設定 .NET 程式碼品質分析

每個程式碼品質分析器 (其規則識別碼開頭為) 的程式碼 `CA` ，可透過可設定的選項進行調整，以套用至程式碼基底的部分。 每個選項都是藉由將機碼/值組新增至 [EditorConfig](https://editorconfig.org) 檔案來指定。 設定檔案、專案、解決方案或整個存放庫都有特定的設定檔。

> [!TIP]
> 以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**加入**  >  **新專案**]，將 editorconfig 檔案加入至專案。 在 [ **加入新專案** ] 視窗的 [搜尋] 方塊中，輸入 **editorconfig** 。 選取 **editorconfig 檔案 (預設) ** 範本，然後選擇 [ **新增**]。
>
> ![在 Visual Studio 中將 EditorConfig 檔案新增至專案](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

如需設定規則嚴重性 (例如，是否為錯誤或警告) 的詳細資訊，請參閱 [在 EditorConfig 檔中設定規則嚴重性](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)。 或者，您可以選擇其中一個內建的 [EditorConfig 檔或規則集](analyzer-rule-sets.md) ，以快速啟用或停用規則的類別。

::: moniker-end

本文的其餘部分將討論適用于精簡套用 .NET 程式碼品質分析器之選項的一般語法。

## <a name="option-scopes"></a>選項範圍

您可以針對規則類別 (（例如，安全性或設計) ）或特定規則，設定所有規則的每個精簡選項。

### <a name="all-rules"></a>所有規則

設定 *所有* 規則選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。選項名稱 = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>規則類別

為規則 *類別* 設定選項的語法 (例如 [命名]、[設計] 或 [效能) ]，如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleCategory. 選項名稱 = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>特定規則

設定 *特定* 規則選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleId. 選項名稱 = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>啟用以 EditorConfig 為基礎的設定

您可以針對下列範圍啟用以 EditorConfig 為基礎的分析器設定：

- 特定檔 (s) 
- 特定資料夾 (s) 
- 特定專案 (s) 
- 特定解決方案 (s) 
- 整個存放庫

若要啟用設定，請在對應的目錄中新增具有選項的*editorconfig 檔案。* 這個檔案也可以包含以 EditorConfig 為基礎的診斷嚴重性設定專案。 詳細資訊請看[這裡](use-roslyn-analyzers.md#configure-severity-levels)。

## <a name="enable-a-category-of-rules"></a>啟用規則的類別

分析器封裝可能包含預先定義的 [EditorConfig](use-roslyn-analyzers.md#configure-severity-levels) 和（或） [規則集](using-rule-sets-to-group-code-analysis-rules.md) 檔案，可讓您快速且輕鬆地啟用類別的規則，例如安全性或設計規則。 [CodeAnalysis. NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet 分析器套件包含 EditorConfig 檔案和規則集。 藉由啟用特定類別的規則，您可以識別目標問題和特定條件。

> [!NOTE]
> 從 Visual Studio 2019 16.3 版開始，支援使用 EditorConfig 檔來啟用分析器規則和設定其嚴重性。

NetAnalyzers NuGet 套件包含適用于下列規則類別的預先定義 EditorConfig 檔案和規則集：

- 所有規則
- 資料流程
- 設計
- 文件
- 全球化
- 互通性
- 可維護性
- 命名
- 效能
- 從 FxCop 移植
- 可靠性
- 安全性
- 使用方式

每個規則類別都有 EditorConfig 或規則集檔案，以：

- 啟用類別 (中的所有規則，並停用所有其他規則) 
- 使用每個規則的預設嚴重性，並預設為啟用 (並停用所有其他規則) 

> [!TIP]
> 「所有規則」類別具有其他 EditorConfig 或規則集檔案，以停用所有規則。 使用此檔案可快速清除專案中的任何分析器警告或錯誤。

> [!TIP]
> 如果您要從舊版的「FxCop」分析遷移至以 .NET Compiler Platform 為基礎的程式碼分析，EditorConfig 和規則集檔案可讓您繼續使用 [您先前使用](rule-set-reference.md)的類似規則設定。

## <a name="predefined-editorconfig-files"></a>預先定義的 EditorConfig 檔案

CodeAnalysis. NetAnalyzers analyzer 套件的預先定義 EditorConfig 檔位於 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \editorconfig*目錄。 例如，啟用所有安全性規則的 EditorConfig 檔案位於 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*。

將所選的 editorconfig 檔案複製到您專案的根目錄。

## <a name="predefined-rule-sets"></a>預先定義的規則集

CodeAnalysis. NetAnalyzers 分析器套件的預先定義規則集檔案位於 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \rulesets*目錄中。 例如，用來啟用所有安全性規則的規則集檔案位於 *% USERPROFILE% \\ . nuget\packages\microsoft.codeanalysis.netanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.ruleset*。

複製一或多個規則集，並將它們貼入包含 Visual Studio 專案的目錄中，或直接貼到 **方案總管**中。

您也可以 [自訂預先定義的規則集](how-to-create-a-custom-rule-set.md) 至喜好設定。 例如，您可以變更一或多個規則的嚴重性，讓違規在 **錯誤清單**中顯示為錯誤或警告。


## <a name="rule-scope-options-for-net-code-quality-analyzers"></a>.NET 程式碼品質分析器的規則範圍選項

您可以在 [EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)檔案中指定選項。 例如，您可以指定下列選項。

> [!TIP]
> 若要查看可用選項的完整清單，請參閱此 [分析器 Configuration.md](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)檔。 以下是在 *分析器 Configuration.md* 檔中記載選項的範例：
>
> 選項名稱： `sufficient_IterationCount_for_weak_KDF_algorithm`\
> 選項值：整數值 \
> 預設值：針對大部分的規則，預設值為每個可設定的規則 ( ' 100000 ') \
> 範例： `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 要分析的 API 介面的哪個部分 | `public`<br/>`internal` 或 `friend`<br/>`private`<br/>`all`<br/><br/>以逗號 ( 分隔多個值，)  | `public` | [CA1000](ca1000.md) [ca1003 必須](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [ca1024 建議](ca1024.md) [ca1027 必須](ca1027.md) [CA1028](ca1028.md)<br/>[Ca1030 建議](ca1030.md) [ca1036 必須](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[Ca1043 必須](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[Ca1063 必須](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [ca1801 必須](ca1801.md)<br/>[Ca1802 建議](ca1802.md) [>ca1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [ca2234 必須](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否忽略不會傳回值的非同步方法 | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> 在2.6.3 和更早版本的分析器封裝中，此選項的名稱為 `skip_async_void_methods` 。

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要排除規則中的單一字元 [類型參數](/dotnet/csharp/programming-guide/generics/generic-type-parameters) ， `S` 例如： `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> 在2.6.3 和更早版本的分析器封裝中，此選項的名稱為 `allow_single_letter_type_parameters` 。

## <a name="output_kind"></a>output_kind

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 指定應分析產生此類型元件之專案中的程式碼 | 列舉的一或多個欄位 <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>以逗號 ( 分隔多個值，)  | 所有輸出種類 | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 指定應分析之 Api 的必要修飾詞 | 下列允許的修飾詞資料表中有一或多個值<br/><br/>以逗號 ( 分隔多個值，)  | 相依于每個規則 | [CA1802 建議](ca1802.md) |

| 允許的修飾詞 | 摘要 |
| --- | --- |
| `none` | 無修飾元需求 |
| `static` 或 `Shared` | 必須在 Visual Basic 中宣告為 ' static ' ( ' Shared ')  |
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
| 是否要跳過 `this` 擴充方法的參數分析 | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 驗證傳遞給方法之引數的 null 檢查驗證方法名稱不是 null | 允許的方法名稱格式 (以 `|`) 分隔：<br/> -僅限方法名稱 (包含名稱的所有方法，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整名稱，具有選擇性的 `M:` 前置詞 | None | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 其他字串格式化方法的名稱 | 允許的方法名稱格式 (以 `|`) 分隔：<br/> -僅限方法名稱 (包含名稱的所有方法，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整名稱，具有選擇性的 `M:` 前置詞 | None | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 類型的名稱，因此會排除型別及其所有衍生型別以進行分析 | 允許的符號名稱格式 (以 `|`) 分隔：<br/> -僅限類型名稱 (包含名稱的所有類型，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整名稱，具有選擇性的 `T:` 前置詞 | None | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 排除用於分析的符號名稱 | 允許的符號名稱格式 (以 `|`) 分隔：<br/> -僅限符號名稱 (包含名稱的所有符號，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整限定名稱。 每個符號名稱都需要符號類型前置詞，例如 "M：" 前置詞代表方法、"T：" 前置詞代表類型、"N：" 前置詞（命名空間）等等。<br/> - `.ctor`針對函式和靜態函式 `.cctor` | None | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [ca2100 必須](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 分析內容中不允許的符號名稱 | 允許的符號名稱格式 (以 `|`) 分隔：<br/> -僅限符號名稱 (包含名稱的所有符號，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整限定名稱。 每個符號名稱都需要符號類型前置詞，例如 "M：" 前置詞代表方法、"T：" 前置詞代表類型、"N：" 前置詞（命名空間）等等。<br/> - `.ctor`針對函式和靜態函式 `.cctor` | None | [CA1031](ca1031.md) |

## <a name="see-also"></a>另請參閱

- [分析器設定](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [適用于 EditorConfig 的 .NET 編碼慣例](../ide/editorconfig-code-style-settings-reference.md)
