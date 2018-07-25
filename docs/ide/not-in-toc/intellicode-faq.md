---
title: IntelliCode 問與答
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079307"
---
# Visual Studio IntelliCode 常見問題集

感謝您對 Visual Studio IntelliCode 的關注！ 希望此簡短的常見問題集能夠回答您可能遇到的一些問題。

## 問： 什麼是 Visual Studio IntelliCode？

在 2018 組建中，Microsoft 宣告了 Visual Studio IntelliCode，其為一種使用 AI 來增強軟體開發的新功能。 IntelliCode 可幫助開發人員及小組有自信地編碼、更快地發現問題、專注於程式碼檢閱。

IntelliCode 示範了如何以下列方式增強軟體開發過程的早期檢視：

- 提供內容感知程式碼完成
- 引導開發人員遵守所屬小組的模式與風格
- 發現難以捕捉的程式碼問題
- 透過將注意力放在真正重要的區域，從而專注於程式碼檢閱

開發人員可以在 [https://aka.ms/intellicode](https://aka.ms/intellicode) 取得更多資訊，並註冊相關新聞與未來的個人預覽版。

## 問： Visual Studio IntelliCode 可以讓客戶做些什麼？

Visual Studio IntelliCode 具一系列功能，可通過人工智慧 (AI) 提供新的生產力增強功能。

開發人員可以針對 Visual Studio 2017 15.7 和更新版本[下載實驗性延伸模組](https://go.microsoft.com/fwlink/?linkid=872707)。 目前提供的延伸模組：

- AI 增強的 IntelliSense 可預測最可能正確的 API 給開發人員使用，而不僅僅是按字母順序排列來呈現成員清單。 會使用開發人員的目前程式碼內容和模式，以提供動態清單。

- 程式碼樣式和格式設定慣例的推斷，藉由從您的程式碼基底動態建立 [.editorconfig 檔案](../create-portable-custom-editor-options.md)來定義程式碼樣式與格式的方式，協助您保持程式碼的一致。 這些慣例允許 Visual Studio 提供自動化的樣式和格式修正來清除您的文件。

接下來的幾個月，我們會以更多功能來更新延伸模組。

## 問： EditorConfig 推斷為什麼在檔名前面加上 1？

Visual Studio 擴充性的已知問題會造成 1 附加在 .editorconfig 檔名的前面，當您按一下滑鼠右鍵，然後選擇 [新增] > [新增項目] 建立它時。 Visual Studio 的 editorconfig 處理器無法辨識以此方式命名的檔案。 Visual Studio 2017 15.8 版 Preview 4 會解決此問題，在此之前，您可以在 [新增項目] 對話方塊中移除 1 來解決問題。

## 問： 為什麼我的 EditorConfig 慣例不生效？
此問題發生，有幾個常見的原因：

- 在 Visual Studio 2017 15.8 版 Preview 3 之前的版本中，您必須關閉再重新開啟所有開啟的文件，才會看到您在 EditorConfig 檔案中建立的慣例生效。 15.8 Preview 3 版本已修正此問題。
- 格式設定慣例絕不會出現在**錯誤清單**中，或在程式碼中顯示為「波浪線」。 不過，它們可以在 Visual Studio 2017 15.8 版 Preview 3 或更新版本中使用新的格式文件 (Ctrl+K、Ctrl+D) 延伸模組來修正

## 問： 為什麼格式化文件未修正我的樣式慣例？
此問題發生，有幾個常見的原因：

- 您使用的版本可能不是 Visual Studio 2017 15.8 版 Preview 3 或更新版本。 您需要這個版本才能使用擴充的「格式文件」命令來執行額外的程式碼清除目前的文件。
- 您可能未選擇加入樣式修正。 格式化文件之修正慣例問題功能的擴充功能僅涵蓋已修正的問題集。 您可以在 [文字編輯器] > [C#] > [程式碼樣式] > [格式] > [一般] > [格式文件設定 (實驗)] 下的 [工具] - [選項] 中變更修正的問題。 請注意，預設設定不會修正某些樣式慣例。 您可以透過 [工具] > [選項] 選擇加入它們。 例如 [套用隱含/明確類型喜好設定] 會執行有關使用 `var` 的樣式規則。

## 問： Visual Studio IntelliCode 可以推斷哪些 EditorConfig 慣例？

這項功能目前還在實驗階段，所以尚不支援[程式碼樣式設定參考](../editorconfig-code-style-settings-reference.md)中記載的完整慣例集。

IntelliCode 目前可以推斷下列慣例：

格式設定慣例：

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

樣式慣例
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## 問： 是否有其他功能加入 Visual Studio IntelliCode 延伸模組？

我們正積極處理一些功能，很高興能夠在它們變成可用時，公開地分享它們。 您可以在 [https://aka.ms/intellicode](https://aka.ms/intellicode) 註冊消息和更新，以便在我們推出新功能時搶先知道。

## 問：由 IntelliCode 提供的「AI 輔助 IntelliSense」優於一般的 IntelliSense 要素為何？

使用 IntelliCode，完成清單可為開發人員提供最可能正確的 API，而不僅僅是按字母順序排列來呈現成員清單。 會使用開發人員目前的程式碼內容，以及基於 GitHub 上 2000 個高品質開放來源專案 (每個皆超過 100 顆星) 的模式，來提供此動態清單。 結果會形成一個能預測最可能和最相關之 API 呼叫的模型。

## Q：IntelliCode 完成建議好用嗎？

雖然最後還是得取決這些建議在您編碼時的實用度， 但我們已經在 Microsoft 內部使用 IntelliCode 的建議一段時間了，並認為這些建議很實用。 我們希望您給 Visual Studio [IntelliCode 延伸模組](https://go.microsoft.com/fwlink/?linkid=872707)一個機會。 請讓我們了解您的使用情形，並傳送意見反應給我們。 我們也會根據您在建議中挑選的項目來訓練模型，並在模型改善時更新延伸模組。

> [!NOTE]
> 我們並不會收集任何使用者定義的程式碼。 請參閱[隱私權](#privacy)上的問題。

## 問： IntelliCode 的未來是什麼？

我們正在探索使用 AI 和其他先進技術來提高開發人員生產力的各種方法。 在 Microsoft Build 2018 中，我們示範了一些我們認為 AI 能幫助開發人員之案例的早期檢視，但還有更多其他的！ 對於開發人員使用我們示範的內容來進行之實驗，我們有興趣了解，請在 [https://aka.ms/intellicode](https://aka.ms/intellicode) 註冊相關新聞與更新。

## 問： 費用是多少？

目前我們沒有關於定價的公告。

## 問： 何時會發行 IntelliCode？

IntelliCode 的 AI 輔助 IntelliSense 目前為第一個實驗性預覽版本。 我們會持續更新實驗性延伸模組，未來將進一步新增功能。 我們沒有最終版本的發行時間表，但我們歡迎來自開發人員的意見反應，幫助我們提供最佳的體驗。 您可以在 [https://aka.ms/intellicode](https://aka.ms/intellicode) 註冊相關新聞與更新。

## 問： 這項體驗只能在 Visual Studio 中以 C# 使用嗎？

在 C# 程式碼基底之 Visual Studio 2017 中的 2018 組建中已示範體驗。 但是，我們期待未來將 IntelliCode 擴展到 Visual Studio 系列的更多語言和工具中。

## 問： <a name="whynointellisense"/> 我在我的 C# 編輯經驗中看不到 IntelliCode 建議 - 這是為什麼？

IntelliCode 建議會出現在 C# 的標準 Visual Studio IntelliSense UI 中。 覆寫該 UI 的延伸模組會防止 IntelliCode「已加星號」的建議出現在清單頂端。 您可以藉由關閉延伸模組，然後再試一次 IntelliSense，確認延伸模組是否造成此行為。

如果這不會為您解決問題，請透過 Visual Studio 的[回報問題](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)功能回報您的問題，並在報表中提到 IntelliCode。

## 問： 我需要哪個版本的 Visual Studio 才能執行此延伸模組？

Visual Studio 2017 15.7 版 Preview 5 和更新版本 (所有 SKU) 均支援 Visual Studio IntelliCode 延伸模組。 如果您未安裝最低需求的版本， 那麼延伸模組的安裝會停止並出現「此延伸模組並不適用於任何目前安裝的產品。」

## 問： 這項體驗只提供英文版嗎？

IntelliCode 目前是預覽延伸模組，我們相當希望了解這些功能對我們廣泛的客群而言有多麼實用。 當我們結束 IntelliCode 的預覽階段後，必定會根據您的意見反應來考量應該優先支援哪些語言，以及支援套件的封裝方式。

## <a name="privacy"/> Q：隱私權方面呢？ 是否會將我的程式碼傳送到雲端？ 哪些客戶資料會傳送給 Microsoft？

我們邀請開發人員體驗 Visual Studio IntelliCode 作為實驗性預覽版本延伸模組。 延伸模組的目的是使開發人員能夠測試 IntelliCode 功能並向產品小組提供意見反應。

我們從延伸模組中擷取一些匿名的使用方式和錯誤報告資料，以幫助改善產品。 沒有任何使用者定義的程式碼會傳送給 Microsoft，但我們會收集您使用 IntelliCode 結果的相關資訊。 資料只會包含您從 IntelliCode 建議清單中選擇的開放來源和 .NET 類型與成員。 開發人員可以選擇退出 [Visual Studio 經驗改進計畫](../../ide/visual-studio-experience-improvement-program.md)，這會關閉 IntelliCode 延伸模組的資料收集。 從功能表列中，選取 [協助] > [傳送意見反應] > [設定]。 在 [Visual Studio 經驗改進計畫] 對話方塊中，選取 [否，我不願意參與]，然後選取 [確定]。

IntelliCode 延伸模組可能會定期要求開發人員完成一份問卷調查，該調查也是匿名的。 使用者可以註冊相關新聞和未來的個人預覽版，但目前不需要這麼做，即可使用實驗性延伸模組。

未來的功能可能將需要註冊以取得服務的存取權。 當個人預覽版已準備好這些功能時，我們將發佈更多詳細資料。
