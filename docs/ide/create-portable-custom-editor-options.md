---
title: EditorConfig 設定
description: 瞭解如何將 EditorConfig 檔案新增至您的專案或程式碼基底，以針對程式碼基底中的每個人強制執行一致的編碼樣式。
ms.custom: SEO-VS-2020
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.openlocfilehash: 8ab90fda1f14521d59982ef7b5d20998cf61e505
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956837"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>使用 EditorConfig 建立可攜式自訂編輯器設定

您可以將 EditorConfig 檔案新增至您的專案或程式碼基底，以針對程式碼基底中的所有人，強制執行一致的編碼樣式。 EditorConfig 設定優先於全域 Visual Studio 文字編輯器設定。 這表示您可以自訂每個程式碼基底，以使用該專案專屬的文字編輯器設定。 您仍然可以在 Visual Studio 的 [選項] 對話方塊中設定自己的個人編輯器喜好設定。 每當您使用沒有 *.editorconfig* 檔案的程式碼基底時，或 *.editorconfig* 檔案不覆寫特定設定時，就會套用那些設定。 縮排樣式&mdash;定位點或空格，即為這類喜好設定的範例之一。

許多程式碼編輯器和 IDE，包括 Visual Studio，都支援 EditorConfig 設定。 它是隨附於程式碼的可攜式元件，甚至可以強制規範 Visual Studio 之外的編碼樣式。

::: moniker range=">=vs-2019"

當您將 EditorConfig 檔案新增至 Visual Studio 中的專案時，會根據 EditorConfig 設定將新的程式程式碼格式化。 除非您執行下列其中一個命令，否則不會變更現有程式碼的格式：

 - 程式 [代碼清除](../ide/code-styles-and-code-cleanup.md) (**ctrl** + **K**、 **ctrl** + **E**) ，它會套用任何空白字元設定，例如縮排樣式和選取的程式碼樣式設定，例如如何排序指示詞 `using` 。
 - **編輯** >**Advanced** >將檔 **格式化** (或 **ctrl** + **K**、 **ctrl** + **D** （預設設定檔) 中），此設定檔只會套用空白字元設定，例如縮排樣式。

 ::: moniker-end

::: moniker range="=vs-2017"

當您將 EditorConfig 檔案新增至 Visual Studio 中的專案時，會根據 EditorConfig 設定將新的程式程式碼格式化。 除非您將檔案格式化 (在  >    >  預設設定檔) 中編輯 Advanced **format 檔** 或 **ctrl** + **K**、 **ctrl** + **D** ，否則不會變更現有程式碼的格式。 除非您已設定格式檔以 [執行額外的程式碼清除](../ide/code-styles-and-code-cleanup.md#apply-code-styles)，否則檔的格式設定只會影響泛空白字元設定，例如縮排樣式。

 ::: moniker-end

::: moniker range="vs-2017"

您可在 [[格式化](reference/options-text-editor-csharp-formatting.md#format-document-settings)] 選項頁面定義您希望 **將文件格式化** 套用哪些 EditorConfig 設定。

::: moniker-end

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的 EditorConfig](/visualstudio/mac/editorconfig)。

## <a name="code-consistency"></a>程式碼一致性

EditorConfig 檔案中的設定可讓您在程式碼基底中維持一致的編碼樣式及設定，例如縮排樣式、Tab 跳位寬度、行結尾字元、編碼等等，而不論您使用的編輯器或 IDE 為何。 例如，當以 C++ 撰寫程式碼時，如果您的程式碼基底慣例偏好縮排一律包含五個空白字元、文件使用 UTF-8 編碼方式，且每一行的結尾一律為 CR/LF，您可以設定 *.editorconfig* 檔案來做到這點。

您在個人專案上使用的編碼慣例，可能與用於小組專案的不同。 例如，您在編寫程式碼時，可能會偏好縮排時新增定位字元。 不過，您的小組可能會偏好縮排時新增四個空白字元，而不是定位字元。 EditorConfig 檔案讓您能擁有每個案例的組態，以解決此問題。

因為設定是包含在程式碼基底的檔案中，所以它們會隨著該程式碼基底四處移動。 只要您在符合 EditorConfig 規範的編輯器中開啟程式碼檔案，便會實作文字編輯器設定。 如需 EditorConfig 檔案的詳細資訊，請參閱 [EditorConfig.org](https://editorconfig.org/) 網站。

> [!NOTE]
> 由於建置錯誤或警告，目前無法在 CI/CD 管線中強制執行 EditorConfig 中設定的慣例。 任何樣式偏差只會顯示在 Visual Studio 編輯器中和 [錯誤清單] 中。

## <a name="supported-settings"></a>支援的設定

Visual Studio 中的編輯器支援 [EditorConfig 屬性](https://editorconfig.org/#supported-properties)的核心集：

- indent_style
- indent_size
- tab_width
- end\_of_line
- 字元集
- trim\_trailing_whitespace
- insert\_final_newline
- root

除了 XML 以外的所有 Visual Studio 支援語言都支援 EditorConfig 編輯器設定。 此外，EditorConfig 支援[程式碼樣式](/dotnet/fundamentals/code-analysis/code-style-rule-options)慣例，包括 C# 和 Visual Basic 的[語言](/dotnet/fundamentals/code-analysis/style-rules/language-rules)、[格式](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)和[命名](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) 慣例。

## <a name="add-and-remove-editorconfig-files"></a>新增及移除 EditorConfig 檔案

當您將 EditorConfig 檔案新增至專案或程式碼基底之後，您撰寫的任何新程式碼都會根據 EditorConfig 檔案設定格式。 不過，在您格式化檔或執行程式 [代碼清除](../ide/code-styles-and-code-cleanup.md)之前，新增 EditorConfig 檔案並不會將現有的樣式轉換為新的樣式。 例如，如果您在檔案中使用了定位字元設定格式的縮排，而且新增了以空格縮排的 EditorConfig 檔案，縮排字元不會自動轉換為空格。 當您將檔案格式化 (**編輯**  >  **Advanced**  >  **format 檔** 或 **ctrl** + **K**、 **ctrl** + **D**) 時，EditorConfig 檔案中的空白字元設定會套用至現有的程式程式碼。

如果您從專案或程式碼基底移除了 EditorConfig 檔案，且想要依照全域編輯器設定為新的程式碼設定格式，就必須關閉並重新開啟任何開啟的程式碼檔案。

### <a name="add-an-editorconfig-file-to-a-project"></a>將 EditorConfig 檔案新增至專案

1. 在 Visual Studio 中開啟專案或解決方案。 選取專案或解決方案節點，視您的 *.editorconfig* 設定應套用至解決方案中的所有專案或僅只一個專案而定。 您也可以選取專案或解決方案中的資料夾，將 *.editorconfig* 檔案新增到此資料夾。

1. 從功能表列中，選擇 [ **Project**  >  **加入新專案**] 或按 **Ctrl** + **Shift** + **A**。

   [ **加入新專案** ] 對話方塊隨即開啟。

1. 在搜尋方塊中搜尋 **editorconfig**。

   搜尋結果中會顯示兩個 **editorconfig 檔案** 項目範本。

   ![Visual Studio 中的 EditorConfig 檔案項目範本](media/editorconfig-item-templates.png)

1. 選取 **editorconfig 檔案 (預設值)** 範本，以新增已填入兩個核心 EditorConfig 選項 (縮排樣式和大小) 的 EditorConfig 檔案。 或者，選取 **editorconfig 檔案 (.NET)** 範本，以新增已填入兩個預設 [.NET 程式碼樣式、格式和命名慣例](/dotnet/fundamentals/code-analysis/code-style-rule-options)的 EditorConfig 檔案。

   *.editorconfig* 檔案隨即出現在 [方案總管] 中，並在編輯器中開啟。

   ![方案總管和編輯器中的 .editorconfig 檔案](media/editorconfig-dotnet.png)

1. 依需要編輯檔案。

### <a name="other-ways-to-add-an-editorconfig-file"></a>新增 EditorConfig 檔案的其他方式

將 EditorConfig 檔案新資到您專案的方式有數種：

- Visual Studio 中 IntelliCode 的[程式碼推斷功能](/visualstudio/intellicode/code-style-inference)可從現有程式碼推斷程式碼樣式。 然後它會使用已定義的程式碼樣式喜好設定來建立非空白的 EditorConfig 檔案。

- 從 Visual Studio 2019 開始，您可以[以 [工具] > [選項] 中的程式碼樣式設定為基礎產生 EditorConfig 檔案](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)。

## <a name="file-hierarchy-and-precedence"></a>檔案階層和優先順序

當您將 *editorconfig* 檔案新增到檔案階層中的資料夾時，其設定會套用到該層級和以下層級的所有適用檔案。 您也可以覆寫特定專案、程式碼基底，或程式碼基底組件的 EditorConfig 設定，這樣它就會使用和其他程式碼基底組件不同的慣例。 當您納入來自其他地方的程式碼，但不想變更其慣例時，這非常有用。

若要覆寫部分或全部的 EditorConfig 設定，請將 *.editorconfig* 檔案新增至您想要套用這些覆寫設定的檔案階層層級。 新的 EditorConfig 檔案設定會套用到相同層級和任何子目錄中的檔案。

![EditorConfig 階層](../ide/media/vside_editorconfig_hierarchy.png)

如果您想要覆寫部分（而非全部）設定，請只在 *editorconfig* 檔中指定這些設定。 只有明確列在較低層級檔案中的屬性才會被覆寫。 較高層級 *editorconfig* 檔案中的其他設定仍會繼續套用。 如果想要確保「不」套用「任何」較高層級 *.editorconfig* 檔案的設定到此程式碼基底組件，請在較低層級的 *.editorconfig* 檔案中新增 ```root=true``` 屬性：

```ini
# top-most EditorConfig file
root = true
```

EditorConfig 檔案會由上到下讀取。 如果有多個具有相同名稱的屬性，則最近找到具有該名稱的屬性優先。

## <a name="edit-editorconfig-files"></a>編輯 EditorConfig 檔案

Visual Studio 可透過提供 IntelliSense 完成清單協助您編輯 *.editorconfig* 檔案。

![.editorconfig 檔案中的 IntelliSense](media/editorconfig-intellisense-no-extension.png)

在編輯您的 EditorConfig 檔案後，您必須重新載入程式碼檔，新的設定才會生效。

如果您編輯許多 *.editorconfig* 檔案，可能會發現 [EditorConfig 語言服務延伸模組](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)很有幫助。 這項延伸模組有部分功能包括語法反白顯示、 改善的 IntelliSense、驗證和程式碼格式化。

![具有 EditorConfig 語言服務延伸模組的 IntelliSense](media/editorconfig-intellisense.png)

## <a name="example"></a>範例

下列範例顯示 C# 程式碼片段在將 *.editorconfig* 檔案新增至專案之前和之後的縮排狀態。 Visual Studio 文字編輯器 [選項] 對話方塊的 [定位字元] 設定已設為在按下 **Tab** 鍵時，產生空白字元。

![文字編輯器定位字元設定](../ide/media/vside_editorconfig_tabsetting.png)

如同預期，在下一行按下 **Tab** 鍵會透過新增四個額外的空白字元來縮排該行。

![使用 EditorConfig 前的程式碼](../ide/media/vside_editorconfig_before.png)

將名為 *editorconfig* 的新檔案新增至專案，並包含下列內容。 `[*.cs]` 設定表示這項變更只會套用到此專案中的 C# 程式碼檔案。

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

現在，當您按下 **tab** 鍵時，就會得到定位字元而不是空格。

![以 TAB 鍵新增定位字元](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>疑難排解 EditorConfig 設定

如果目錄結構中的任何位置或在專案位置上方有一個 EditorConfig 檔案，Visual Studio 會將該檔案中的編輯器設定套用到您的編輯器。 在此情況下，您可能會看到狀態列中出現下列訊息：

   **「此檔案類型的使用者偏好由此專案的編碼慣例覆寫。」**

這表示，如果 [**工具**  >  **選項**  >  **文字編輯器**] 中的任何編輯器設定 (例如，縮排大小和樣式、索引標籤大小或編碼慣例) 是在目錄結構中專案的 EditorConfig 檔中指定，則 EditorConfig 檔中的慣例會覆寫 [**選項**] 中的設定。 您可以透過切換 [工具] > [選項] > [文字編輯器] 中的 [遵循專案編碼慣例] 選項來控制這個行為。 取消選取此選項會關閉 Visual Studio 的 EditorConfig 支援。

![編碼選項 - 遵循專案編碼慣例](media/coding_conventions_option.png)

您可以藉由開啟命令提示字元，並從包含專案的磁片根目錄中執行下列命令，在父目錄中尋找任何 *editorconfig* 檔案：

```Shell
dir .editorconfig /s
```

您可以在存放庫根目錄或專案所在目錄的 *.editorconfig* 檔案中設定 ```root=true``` 屬性，以控制 EditorConfig 慣例範圍。 Visual Studio 會在已開啟檔案的目錄和每個父目錄中尋找名為 *.editorconfig* 的檔案。 達到根檔案路徑，或者如果找到 ```root=true``` 的 *.editorconfig* 檔案時，搜尋就會結束。

## <a name="see-also"></a>另請參閱

- [.NET 程式碼樣式慣例](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [為語言服務支援 EditorConfig](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [程式碼編輯器的功能](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio for Mac)](/visualstudio/mac/editorconfig)
