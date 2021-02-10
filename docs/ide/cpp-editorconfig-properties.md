---
title: C++ EditorConfig 格式設定慣例
titleSuffix: ''
description: 瞭解如何使用 EditorConfig 來格式化 Visual Studio 中的 c + + 程式碼。
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jmartens
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 490a7b29d6e3d8a2dc63c27b9e9d7226b5d22662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970877"
---
# <a name="c-editorconfig-formatting-conventions"></a>C++ EditorConfig 格式設定慣例

Visual Studio c + + 格式器有一組豐富的可設定設定，可供全域套用。 若要設定特定工作區的 c + + 格式化設定，請使用 [clangformat](https://clang.llvm.org/docs/ClangFormat.html) 或 [EditorConfig](https://editorconfig.org/)。 Visual Studio 和 Visual Studio Code 都有內建的全域 Visual Studio c + + 格式化設定 EditorConfig 支援，EditorConfig 設定優先。 這表示您可以將 EditorConfig 檔案新增至工作區，以便在更細微的層級上設定 c + + 格式，並且針對參與專案的每個人強制執行一致的程式碼樣式。

## <a name="c-formatting-conventions"></a>C + + 格式慣例

C + + 格式化 EditorConfig 設定前面會加上 `cpp_` 。 以下是您的 EditorConfig 檔案可能看起來的範例：

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

本檔的其餘部分會列出 Visual Studio 和 VS Code 所支援的所有 EditorConfig c + + 格式化設定。

### <a name="indentation-settings"></a>縮排設定

**縮排大括弧**

- 名稱：`cpp_indent_braces`
- 值： `true` 、 `false`

**每一行縮排相對於**

- 名稱：`cpp_indent_multi_line_relative_to`
- 值：
  - `outermost_parenthesis` -當輸入新行時，它會相對於最外層的左括弧縮排。
  - `innermost_parenthesis` -當輸入新行時，它會相對於最內層的左括弧縮排。
  - `statement_begin` -當輸入新行時，它會相對於目前語句的開頭縮排。

**在輸入括弧內時對齊新行**

- 名稱：`cpp_indent_within_parentheses`
- 值：
  - `align_to_parenthesis` -將內容對齊以開啟括弧。
  - `indent` -將新行縮排。

**在現有的程式碼中，請勿使用括弧內的新行對齊設定**

- 名稱：`cpp_indent_preserve_within_parentheses`
- 值： `true` 、 `false`

**縮排案例內容**

- 名稱：`cpp_indent_case_contents`
- 值： `true` 、 `false`

**縮排案例標籤**

- 名稱：`cpp_indent_case_labels`
- 值： `true` 、 `false`

**在 case 語句之後縮排括弧**

- 名稱：`cpp_indent_case_contents_when_block`
- 值： `true` 、 `false`

**將 lambda 的括弧縮排作為參數使用**

- 名稱：`cpp_indent_lambda_braces_when_parameter`
- 值： `true` 、 `false`

**Goto 標籤的位置**

- 名稱：`cpp_indent_goto_labels`
- 值：
  - `one_left` -左邊的一個縮排
  - `leftmost_column` -移至最左邊的資料行
  - `none` -保留縮排

**預處理器指示詞的位置**

- 名稱：`cpp_indent_preprocessor`
- 值：
  - `one_left` -左邊的一個縮排
  - `leftmost_column` -移至最左邊的資料行
  - `none` -保留縮排

**縮排存取規範**

- 名稱：`cpp_indent_access_specifiers`
- 值： `true` 、 `false`

**縮排命名空間內容**

- 名稱：`cpp_indent_namespace_contents`
- 值： `true` 、 `false`

**保留批註的縮排**

- 名稱：`cpp_indent_preserve_comments`
- 值： `true` 、 `false`

### <a name="newline-settings"></a>換行設定

**命名空間的左大括弧位置**

- 名稱：`cpp_new_line_before_open_brace_namespace`
- 值：
  - `new_line` -移至新行
  - `same_line` -保留在同一行上，但在前面加上空格
  - `ignore` -不要自動重新置放

**類型的左大括弧位置**

- 名稱：`cpp_new_line_before_open_brace_type`
- 值：
  - `new_line` -移至新行
  - `same_line` -保留在同一行上，但在前面加上空格
  - `ignore` -不要自動重新置放

**函數左大括弧的位置**

- 名稱：`cpp_new_line_before_open_brace_function`
- 值：
  - `new_line` -移至新行
  - `same_line` -保留在同一行上，但在前面加上空格
  - `ignore` -不要自動重新置放

**控制區塊的左大括弧位置**

- 名稱：`cpp_new_line_before_open_brace_block`
- 值：
  - `new_line` -移至新行
  - `same_line` -保留在同一行上，但在前面加上空格
  - `ignore` -不要自動重新置放

**Lambda 的左大括弧位置**

- 名稱：`cpp_new_line_before_open_brace_lambda`
- 值：
  - `new_line` -移至新行
  - `same_line` -保留在同一行上，但在前面加上空格
  - `ignore` -不要自動重新置放
 
**將範圍大括弧放在不同的行上**

- 名稱：`cpp_new_line_scope_braces_on_separate_lines`
- 值： `true` 、 `false`

**針對空的類型，將右大括弧移至與左大括弧相同的行**

- 名稱：`cpp_new_line_close_brace_same_line_empty_type`
- 值： `true` 、 `false`

**針對空的函式主體，將右大括弧移至與左大括弧相同的行**

- 名稱：`cpp_new_line_close_brace_same_line_empty_function`
- 值： `true` 、 `false`

**將 ' catch ' 和類似的關鍵字放在新行上**

- 名稱：`cpp_new_line_before_catch`
- 值： `true` 、 `false`

**將 ' else ' 放在新行上**

- 名稱：`cpp_new_line_before_else`
- 值： `true` 、 `false`

**在新行的 do while 迴圈中放置 ' while '**

- 名稱：`cpp_new_line_before_while_in_do_while`
- 值： `true` 、 `false`

### <a name="spacing-settings"></a>間距設定

**函數名稱和引數清單的左括弧之間的間距**

- 名稱：`cpp_space_before_function_open_parenthesis`
- 值：
  - `insert` -插入空格
  - `remove` -移除空格
  - `ignore` -不要變更空格

**在引數清單的括弧內插入空格**

- 名稱 `cpp_space_within_parameter_list_parentheses` 值： `true` 、 `false`

**當引數清單為空白時，在括弧之間插入空格**

- 名稱：`cpp_space_between_empty_parameter_list_parentheses`
- 值： `true` 、 `false`

**在控制流程語句中的關鍵字和左括弧之間插入空格**

- 名稱：`cpp_space_after_keywords_in_control_flow_statements`
- 值： `true` 、 `false`

**在控制語句的括弧內插入空格**

- 名稱：`cpp_space_within_control_flow_statement_parentheses`
- 值： `true` 、 `false`

**在 lambda 引數清單的左括弧前面插入空格**

- 名稱：`cpp_space_before_lambda_open_parenthesis`
- 值： `true` 、 `false`

**在 C 樣式轉換的括弧內插入空格**

- 名稱：`cpp_space_within_cast_parentheses`
- 值： `true` 、 `false`

**在 C 樣式轉換的右括弧後面插入空格**

- 名稱：`cpp_space_after_cast_close_parenthesis`
- 值： `true` 、 `false`

**在括號運算式的括弧內插入空格**

- 名稱：`cpp_space_within_expression_parentheses`
- 值： `true` 、 `false`

**在區塊的左大括弧前面插入空格**

- 名稱：`cpp_space_before_block_open_brace`
- 值： `true` 、 `false`

**在空白大括弧之間插入空格**

- 名稱：`cpp_space_between_empty_braces`
- 值： `true` 、 `false`

**在統一初始設定和初始化運算式清單的左大括弧前面插入空格**

- 名稱：`cpp_space_before_initializer_list_open_brace`
- 值： `true` 、 `false`

**在統一初始設定和初始化運算式清單的大括弧內插入空格**

- 名稱：`cpp_space_within_initializer_list_braces`
- 值： `true` 、 `false`

**在統一初始設定和初始化運算式清單中保留空格**

- 名稱：`cpp_space_preserve_in_initializer_list`
- 值： `true` 、 `false`

**在左方括弧前插入空格**

- 名稱：`cpp_space_before_open_square_bracket`
- 值： `true` 、 `false`

**在方括弧內插入空格**

- 名稱：`cpp_space_within_square_brackets`
- 值： `true` 、 `false`

**在空白方括弧之前插入空格**

- 名稱：`cpp_space_before_empty_square_brackets`
- 值： `true` 、 `false`

**在空的方括弧之間插入空格**

- 名稱：`cpp_space_between_empty_square_brackets`
- 值： `true` 、 `false`

**將多維度陣列的方括弧群組在一起**

- 名稱：`cpp_space_group_square_brackets`
- 值： `true` 、 `false`

**在 lambda 的方括弧內插入空格**

- 名稱：`cpp_space_within_lambda_brackets`
- 值： `true` 、 `false`

**SpaceBetweenEmptyLambdaBrackets**

- 名稱：`cpp_space_between_empty_lambda_brackets`
- 值： `true` 、 `false`

**在逗號前插入空格**

- 名稱：`cpp_space_before_comma`
- 值： `true` 、 `false`

**在逗號後插入空格**

- 名稱：`cpp_space_after_comma`
- 值： `true` 、 `false`

**移除成員運算子前後的空格**

- 名稱：`cpp_space_remove_around_member_operators`
- 值： `true` 、 `false`

**在類型宣告中的基底的冒號前面插入空格**

- 名稱：`cpp_space_before_inheritance_colon`
- 值： `true` 、 `false`

**在函式的冒號前面插入空格**

- 名稱：`cpp_space_before_constructor_colon`
- 值： `true` 、 `false`

**移除分號之前的空格**

- 名稱：`cpp_space_remove_before_semicolon`
- 值： `true` 、 `false`

**在分號後面插入空格**

- 名稱：`cpp_space_after_semicolon`
- 值： `true` 、 `false`

**移除一元運算子及其運算元之間的空格**

- 名稱：`cpp_space_remove_around_unary_operator`
- 值： `true` 、 `false`

**二元運算子的間距**

- 名稱：`cpp_space_around_binary_operator`
- 值：
  - `insert` -在二元運算子前後插入空格。
  - `remove` -移除二元運算子前後的空格。
  - `ignore` -請勿變更二元運算子前後的空格。

**指派運算子的間距**

- 名稱：`cpp_space_around_assignment_operator`
- 值：
  - `insert` -在指派運算子前後插入空格。
  - `remove` -移除指派運算子前後的空格。
  - `ignore` -請勿變更指派運算子前後的空格。

**指標/參考對齊**

- 名稱：`cpp_space_pointer_reference_alignment`
- 值：
  - `left` -靠左對齊。
  - `center` -靠上置中。
  - `right` -靠右對齊。
  - `ignore` -保持不變。

**條件運算子的間距**

- 名稱：`cpp_space_around_ternary_operator`
- 值：
  - `insert` -在條件運算子前後插入空格。
  - `remove` -移除條件運算子前後的空格。
  - `ignore` -請勿變更條件運算子前後的空格。

### <a name="wrapping-options"></a>換行選項

**區塊的包裝選項**

- 名稱：`cpp_wrap_preserve_blocks`
- 值：
  - `one_liners` -請勿包裝單行程式碼區塊。
  - `all_one_line_scopes` -請勿包裝程式碼區塊，其中的左括弧和右大括弧在下一行。
  - `never` -一律套用區塊的新行設定。

## <a name="see-also"></a>另請參閱

- [EditorConfig.org](https://editorconfig.org/)
- [為語言服務支援 EditorConfig](../extensibility/supporting-editorconfig.md)
- [程式碼編輯器的功能](writing-code-in-the-code-and-text-editor.md)
