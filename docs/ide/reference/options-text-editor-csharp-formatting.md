---
title: C# 編輯器格式化選項
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8947f6e2fee2b8615c750b770ac3b0dea85bb991
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666333"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>選項對話方塊：文字編輯器 \> C# \> 程式碼樣式 \> 格式

若要設定程式碼編輯器中的程式碼格式化選項，請使用 [格式化] 選項頁面和它的子頁面 ([[縮排]](#indentation-page)、[新行]、[間距] 與 [換行])。

若要存取此 [選項] 頁面，請從功能表列選擇 [工具] > [選項]。 在 [選項] 對話方塊中，選擇 [文字編輯器] > [C#] > [程式碼樣式] > [格式化]。

> [!TIP]
> [縮排]、[新行]、[間距] 和 [換行] 子頁面都會在底部顯示預覽視窗，以顯示每個選項的效果。 若要使用預覽視窗，請選取一個格式化選項。 預覽視窗會呈現所選選項的範例。 當您選取選項按鈕或核取方塊以變更設定時，預覽視窗會更新以顯示新設定的影響。

## <a name="formatting-general-page"></a>格式化 (一般) 頁面

### <a name="general-settings"></a>一般設定

這些設定「會在」程式碼編輯器將格式化選項套用至程式碼時有影響。

|ThisAddIn|描述|
|-----------|-----------------|
|**於輸入時自動格式化**|當取消選取時，會停用 [輸入 ; 時將陳述式格式化] 及 [輸入 } 時將區塊格式化] 選項。|
|**於 ; 處將陳述式自動格式化**|選取時，系統會在陳述式完成時，根據編輯器選取的格式化選項來將陳述式格式化。|
|**於 } 處將區塊自動格式化**|選取時，系統會在您完成程式碼區塊時，根據編輯器選取的格式化選項來將程式碼區塊格式化。|
|**在傳回時自動格式化**|選取時，會在按下 **Enter** 時將文字格式化，使其符合為編輯器選取的格式化選項。|
|**貼上時自動格式化**|選取時，系統會將貼入編輯器的文字格式化，使其符合為編輯器選取的格式化選項。|

::: moniker range="vs-2019"

如果您先前是使用 Visual Studio 2017 中的 [格式化文件] 命令，對 C# 檔案套用程式碼樣式設定，該功能現在已改為 [[程式碼清除]](../code-styles-and-code-cleanup.md#apply-code-styles)。

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>將文件格式化的設定

這些設定會設定**將文件格式化**的命令，以在檔案執行額外的程式碼清理。 如需這些設定的套用方式詳細資訊，請參閱[將文件格式化的命令](../code-styles-and-code-cleanup.md#apply-code-styles)。

|ThisAddIn|描述|對應的 EditorConfig 與 [工具] > [選項] 規則|
|-----------|-----------------|-----------------|-----------------|
|**套用所有 C# 格式化規則 (縮排、換行、間距)**|**將文件格式化**的命令一律會修正格式化問題。 這項設定無法變更。| [Core EditorConfig 選項](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig 格式化選項](../../ide/editorconfig-formatting-conventions.md)<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [格式化] > [縮排] 或 [新行] 或 [間距] 或 [換行]|
|**在格式化期間執行其他程式碼清理**|如有選取，會對 **Edit.FormatDocument** 命令下指定的規則套用修正。| N/A |
|**移除不必要的 Using**|如有選取，會在 **Edit.FormatDocument** 觸發時移除不必要的 `using` 指示詞。| N/A |
|**為 Using 排序**|如有選取，會在 **Edit.FormatDocument** 觸發時為 `using` 指示詞排序。| dotnet_sort_system_directives_first<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [進階] > [在為 Using 排序時將 'System' 放在第一位] |
|**新增/移除單行控制陳述式的括號**|如有選取，會在 **Edit.FormatDocument** 觸發時從單行控制陳述式新增或移除括號。| csharp_prefer_braces<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [程式碼區塊喜好設定] > [建議使用括弧] |
|**新增協助工具修飾詞**|如有選取，會在 **Edit.FormatDocument** 觸發時新增缺少的協助工具修飾詞。| dotnet_style_require_accessibility_modifiers |
|**為存取範圍修飾詞排序**|如有選取，會在 **Edit.FormatDocument** 觸發時為協助工具修飾詞排序。| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**套用運算式/區塊主體喜好設定**|如有選取，會在 **Edit.FormatDocument** 觸發時將以運算式為主體的成員轉換成區塊主體，或反向轉換。| [以運算式為主體的成員 EditorConfig 選項](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [運算式喜好設定] > [對方法、建構函式等使用運算式主體] |
|**套用隱含/明確類型喜好設定**|如有選取，會在 **Edit.FormatDocument**觸發時將 `var` 轉換為明確類型，或反向轉換。| [明確類型 EditorConfig 選項](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [’var’喜好設定] |
|**套用內嵌 'out' 變數喜好設定**|如有選取，會在 **Edit.FormatDocument**觸發時，於可行的位置內嵌 `out` 變數。| csharp_style_inlined_variable_declaration<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [變數喜好設定] > [建議使用內嵌變數宣告] |
|**套用語言/架構類型喜好設定**|如有選取，會在 **Edit.FormatDocument** 觸發時將語言類型轉換為架構類型，或反向轉換。| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [預先定義的類型喜好設定] |
|**套用物件/集合初始設定喜好設定**|如有選取，會在 **Edit.FormatDocument** 觸發時，於可行的位置使用物件和集合初始設定式。| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [運算式喜好設定] > [建議使用物件初始設定式] 或 [建議使用集合初始設定式] |
|**套用 'this.' 限定性條件喜好設定**|如有選取，會在 **Edit.FormatDocument** 觸發時套用 `this.` 喜好設定。| [限定性條件 EditorConfig 選項](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [’this’ 喜好設定] |
|**在可行時將私人欄位設為唯讀**|如有選取，會在 **Edit.FormatDocument** 觸發時，於可行的位置將私人欄位設為 `readonly`。| dotnet_style_readonly_field<br/><br/>[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [欄位喜好設定] > [建議唯讀] |
|**移除不必要的 cast**|如有選取，會在 **Edit.FormatDocument** 觸發時移除不必要的 cast。| N/A |
|**移除未使用的變數**|如有選取，會在 **Edit.FormatDocument** 觸發時移除未使用的變數。| N/A |

![Visual Studio 中 C# 的程式碼清理設定](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>縮排頁面

此頁面的縮排選項適用於自動格式化程式碼的情況。 例如，當您將程式碼貼入檔案，同時選取 [貼上時自動格式化] 時。 ([貼上時自動格式化] 選項位於 [格式化] > [一般] 下方)。

![Visual Studio 中 C# 文字編輯器的縮排選項](media/csharp-indentation-options.png)

> [!TIP]
> 此外，還有 [文字編輯器] > [C#] > [索引標籤] 選項頁面上的縮排選項。 這些選項只會決定當您在行末按下 **Enter** 時，程式碼編輯器會在哪裡放置游標。
>
> ![Visual Studio 中 C# 文字編輯器的 [索引標籤] 選項](media/csharp-tabs-options.png)

## <a name="see-also"></a>請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)