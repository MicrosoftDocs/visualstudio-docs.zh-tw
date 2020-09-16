---
title: EditorConfig 的 .NET 程式碼慣例設定
ms.date: 09/02/2020
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 67a9a6f7ec63686003f6e6535b213e9c6fa606f0
ms.sourcegitcommit: 5a5f31a1a91bf243852c7da872211e63ab37fdaa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90682652"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig 的 .NET 編碼慣例設定

您可以使用 [EditorConfig](../ide/create-portable-custom-editor-options.md) 檔案，在程式碼基底中定義和維護一致的程式碼樣式。 EditorConfig 包含數個核心格式設定屬性，例如 `indent_style` 和 `indent_size`。 在 Visual Studio 中，也可以使用 EditorConfig 檔案來設定 .NET 編碼慣例設定。 您可以啟用或停用個別的 .NET 編碼慣例，並設定您希望強制執行每個規則的程度 (透過嚴重性等級)。

> [!TIP]
> - 當您在 EditorConfig 檔中定義編碼慣例時，您要設定如何讓 Visual Studio 內建的程式 [代碼樣式分析器](../code-quality/roslyn-analyzers-overview.md) 分析您的程式碼。 EditorConfig 檔案是這些分析器的設定檔。
> - 您也可以在[文字編輯器的 [選項]](code-styles-and-code-cleanup.md) 對話方塊中，設定適用於 Visual Studio 的程式碼樣式喜好設定。 不過，EditorConfig 設定的優先順序和您在 [ **選項** ] 中設定的喜好設定，不會與特定專案建立關聯。

## <a name="convention-categories"></a>慣例類別

有三個支援的 .NET 程式碼慣例類別：

- [語言慣例](../ide/editorconfig-language-conventions.md)

   有關 C# 或 Visual Basic 語言的規則。 例如，您可以在定義變數或指定運算式主體成員時，指定使用 `var` 或明確類型的規則。

- [格式設定慣例](../ide/editorconfig-formatting-conventions.md)

   有關程式碼配置和結構的規則，以使其更容易閱讀。 例如，您可以指定使用 Allman 大括弧或設定控制區塊空格的規則。

- [命名規範](../ide/editorconfig-naming-conventions.md)

   有關程式碼項目的命名規則。 例如，您可以指定 `async` 方法必須以 "Async" 結尾。

::: moniker range=">=vs-2019"

## <a name="enforce-coding-conventions-on-build"></a>在組建上強制執行編碼慣例

從 Visual Studio 2019 16.8 版（包括 .NET 5.0 RC2 SDK）開始，您可以對所有 .NET 專案 [強制執行組建的 .net 程式碼慣例](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) 。 在組建階段，.NET 程式碼樣式違規將會顯示為「IDE」前置詞的警告或錯誤。 這可讓您在程式碼基底中嚴格強制執行一致的程式碼樣式。

::: moniker-end

## <a name="example-editorconfig-file"></a>EditorConfig 檔案範例

為協助您開始使用，以下是具有預設選項的 editorconfig 檔案範例 *。* 在 Visual Studio 中，您可以產生此檔案，並將其儲存至 [**工具**  >  **選項**  >  **文字編輯器**] > [**c #** 或**Basic**] > 程式**代碼樣式**  >  **一般**的專案。 然後，按一下 [設定] 按鈕中的 [ **產生 editorconfig** 檔案]。 如需詳細資訊，請參閱程式 [代碼樣式喜好](code-styles-and-code-cleanup.md)設定。

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### .NET Coding Conventions ####

# Organize usings
dotnet_separate_import_directive_groups = false
dotnet_sort_system_directives_first = false
file_header_template = unset

# this. and Me. preferences
dotnet_style_qualification_for_event = false:silent
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_property = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent

# Expression-level preferences
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_object_initializer = true:suggestion
dotnet_style_operator_placement_when_wrapping = beginning_of_line
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_compound_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:suggestion
dotnet_style_prefer_simplified_boolean_expressions = true:suggestion
dotnet_style_prefer_simplified_interpolation = true:suggestion

# Field preferences
dotnet_style_readonly_field = true:suggestion

# Parameter preferences
dotnet_code_quality_unused_parameters = all:suggestion

# Suppression preferences
dotnet_remove_unnecessary_suppression_exclusions = none

#### C# Coding Conventions ####

# var preferences
csharp_style_var_elsewhere = false:silent
csharp_style_var_for_built_in_types = false:silent
csharp_style_var_when_type_is_apparent = false:silent

# Expression-bodied members
csharp_style_expression_bodied_accessors = true:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent

# Pattern matching preferences
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_prefer_not_pattern = true:suggestion
csharp_style_prefer_pattern_matching = true:silent
csharp_style_prefer_switch_expression = true:suggestion

# Null-checking preferences
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_prefer_static_local_function = true:suggestion
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:silent

# Code-block preferences
csharp_prefer_braces = true:silent
csharp_prefer_simple_using_statement = true:suggestion

# Expression-level preferences
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
csharp_style_throw_expression = true:suggestion
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
csharp_style_unused_value_expression_statement_preference = discard_variable:silent

# 'using' directive preferences
csharp_using_directive_placement = inside_namespace:silent

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = true
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = suggestion
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i

dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case

dotnet_naming_rule.non_field_members_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.non_field_members_should_be_pascal_case.symbols = non_field_members
dotnet_naming_rule.non_field_members_should_be_pascal_case.style = pascal_case

# Symbol specifications

dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.interface.required_modifiers = 

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.types.required_modifiers = 

dotnet_naming_symbols.non_field_members.applicable_kinds = property, event, method
dotnet_naming_symbols.non_field_members.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.non_field_members.required_modifiers = 

# Naming styles

dotnet_naming_style.pascal_case.required_prefix = 
dotnet_naming_style.pascal_case.required_suffix = 
dotnet_naming_style.pascal_case.word_separator = 
dotnet_naming_style.pascal_case.capitalization = pascal_case

dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.required_suffix = 
dotnet_naming_style.begins_with_i.word_separator = 
dotnet_naming_style.begins_with_i.capitalization = pascal_case

```

> [!NOTE]
> 如需支援的 .NET 編碼慣例類別的詳細資訊，請參閱 [語言慣例](../ide/editorconfig-language-conventions.md)、 [格式化慣例](../ide/editorconfig-formatting-conventions.md)和 [命名慣例](../ide/editorconfig-naming-conventions.md) 頁面。

## <a name="see-also"></a>另請參閱

- [快速動作](../ide/quick-actions.md)
- [建立可攜式自訂編輯器選項](../ide/create-portable-custom-editor-options.md)
- [.NET Compiler Platform "Roslyn". editorconfig 檔案](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
- [.NET Compiler Platform editorconfig 檔案](https://github.com/dotnet/runtime/blob/master/.editorconfig)
