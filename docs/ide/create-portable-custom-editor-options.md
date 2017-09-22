---
title: "使用 EditorConfig 建立可攜式自訂編輯器設定 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.technology:
- vs-ide-general
ms.translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: f377ada139d9c0e8b01b640cf603cf349dc1c3c3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/27/2017

---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>使用 EditorConfig 建立可攜式自訂編輯器設定
在 Visual Studio 中的文字編輯器設定適用於特定類型的所有專案。 因此，比方說，如果您變更 C# 文字編輯器設定，該設定會適用於 Visual Studio 中的「所有」C# 專案。 不過，在某些情況下，您可能需要使用不同於您自己的個人編輯器喜好設定的慣例。 [EditorConfig](http://editorconfig.org/) 檔案藉由根據每個專案提供一般文字編輯器選項，而讓您能做到這點。 在新增到您程式碼基底的 .editorconfig 檔案中，所包含的 EditorConfig 設定會取代全域 Visual Studio 文字編輯器設定。 這表示您可以自訂每個程式碼基底，以使用您偏好的文字編輯器設定。 不需要外掛程式即可在 Visual Studio 中使用這項功能。

## <a name="coding-consistency"></a>程式碼撰寫的一致性
EditorConfig 檔案中的設定可讓您在程式碼基底中維護語言的一致程式碼樣式和設定，例如縮排樣式、Tab 跳位寬度、行結尾字元、編碼等等，而不論您使用的編輯器或 IDE 為何。 比方說，當以 C++ 編寫程式碼時，如果您的程式碼基底慣例偏好縮排一律包含五個空白字元、文件使用 UTF-8 編碼方式，且每一行的結尾一律為 CR/LF，您可以設定 .editorconfig 檔案來做到這點。

您在個人專案上使用的編碼慣例，可能與用於小組專案的不同。 例如，您編寫程式碼時，可能會偏好按下 Tab 鍵將新增一個 TAB 字元。 不過，您的小組可能會偏好縮排時新增四個空白字元，而不是 TAB 字元。 EditorConfig 檔案讓您能擁有每個案例的組態，以解決此問題。

因為設定是包含在程式碼基底的檔案中，所以它們會隨著該程式碼基底四處移動。 只要您在符合 EditorConfig 規範的編輯器中開啟程式碼檔案，便會實作文字編輯器設定。 如需 EditorConfig 檔案的詳細資訊，請參閱 [EditorConfig.org](http://editorconfig.org/) 網站。 如果您編輯許多 .editorconfig 檔案，可能會發現 [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) (EditorConfig 語言服務) 延伸模組很有幫助。

## <a name="override-editorconfig-settings"></a>覆寫 EditorConfig 設定
當您將 .editorconfig 檔案新增到檔案階層中的資料夾時，其設定會適用於該層級和以下的所有適用檔案。 若要覆寫特定專案或程式碼基底的 EditorConfig 設定，並使用與最上層 .editorconfig 檔案不同的值或覆寫值，只要將 .editorconfig 檔案新增至您想要變更的層級。

![EditorConfig 階層](../ide/media/vside_editorconfig_hierarchy.png)

新的 .editorconfig 檔案設定將適用於它所在的層級和其所有子檔案。

## <a name="supported-settings"></a>支援的設定
Visual Studio 中的編輯器支援核心 EditorConfig 選項集合的下列值。
- indent_style
- indent_size
- tab_width
- end_of_line
- 字元集
- 根
- [程式碼樣式慣例](../ide/editorconfig-code-style-settings-reference.md)

除了 XML 以外的所有 Visual Studio 支援語言都支援 EditorConfig 設定。

## <a name="example"></a>範例
以下範例顯示 C# 程式碼片段在將 .editorconfig 檔案新增至專案之前和之後的縮排狀態。 Visual Studio 文字編輯器 [選項] 對話方塊的 [定位字元] 設定已設為在您於程式碼中按下 TAB 鍵時，會產生空白字元。

![文字編輯器定位字元設定](../ide/media/vside_editorconfig_tabsetting.png)

如同預期，在下一行按下 TAB 鍵會藉由新增四個額外的空白字元來縮排該行。

![使用 EditorConfig 前的程式碼](../ide/media/vside_editorconfig_before.png)

我們會將下列內容新增到專案中的新檔案，稱為 .editorconfig。 (`[*.cs]` 設定表示這項變更將只會適用於此專案中的 .cs 檔案。)

![新增 .editorconfig 檔案至專案](../ide/media/vside_editorconfig_addconfig.png)

現在，當您按下 TAB 鍵，您會得到定位點字元，而不是空白。

![TAB 新增定位字元](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  將 .editorconfig 檔案新增到專案或程式碼基底並不會將現有的樣式轉換為新樣式，它只適用於剛剛新增的行。 如果您從專案或程式碼基底移除 .editorconfig 檔案，必須重新載入程式碼檔案，編輯器設定才會還原成全域設定。 在 Visual Studio 中的 [錯誤] 視窗裡會報告 .editorconfig 檔案中的任何錯誤。

## <a name="support-editorconfig-for-your-language-service"></a>語言服務的 EditorConfig 支援

在大部分情況下，當您實作 Visual Studio 語言服務時，並不需要進行任何額外的作業即可支援 EditorConfig 通用屬性。 當使用者開啟檔案時，核心編輯器會自動探索並讀取 .editorconfig 檔案，然後設定適當的文字緩衝區和檢視選項。 不過，當使用者編輯或格式化文字時，有些語言服務會選擇適當的內容文字檢視選項，而不使用定位點和空格這類項目的全域設定。 在這種情況下，您必須更新語言服務才能支援 EditorConfig 檔案。

下表列出要更新語言服務以支援 EditorConfig 檔案所需的變更。

| 已被取代的全域特定語言選項 | 取代內容選項 |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs 或 Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) 或 !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize 或 Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) 或 textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize 或 Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) 或 textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

# <a name="see-also"></a>另請參閱
[使用 EditorConfig 建立可攜式自訂編輯器選項](create-portable-custom-editor-options.md)
