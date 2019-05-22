---
title: EditorConfig 設定
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9426b2b7cd9467353f129e9376b0f83cf2f620a3
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65845998"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>使用 EditorConfig 建立可攜式自訂編輯器設定

您可以在專案或程式碼基底中新增 [EditorConfig](http://editorconfig.org/) 檔案，強制使用程式碼基底的所有人都使用一致的編碼樣式。 EditorConfig 設定優先於全域 Visual Studio 文字編輯器設定。 這表示您可以自訂每個程式碼基底，以使用該專案專屬的文字編輯器設定。 您仍然可以在 Visual Studio 的 [選項] 對話方塊中設定自己的個人編輯器喜好設定。 每當您使用沒有 *.editorconfig* 檔案的程式碼基底時，或 *.editorconfig* 檔案不覆寫特定設定時，就會套用那些設定。 縮排樣式&mdash;定位點或空格，即為這類喜好設定的範例之一。

許多程式碼編輯器和 IDE，包括 Visual Studio，都支援 EditorConfig 設定。 它是隨附於程式碼的可攜式元件，甚至可以強制規範 Visual Studio 之外的編碼樣式。

當您在 Visual Studio 中將 EditorConfig 新增到專案時，除非您將文件格式化 ([編輯] > [進階] > [將文件格式化] 或在預設設定檔中按 **Ctrl**+**K**、**Ctrl**+**D**)，否則現有程式碼的格式設定不會變更。 但是，新的程式碼會依照 EditorConfig 的設定進行設定格式。

::: moniker range="vs-2017"

您可在 [[格式化](reference/options-text-editor-csharp-formatting.md#format-document-settings)] 選項頁面定義您希望**將文件格式化**套用哪些 EditorConfig 設定。

::: moniker-end

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的 EditorConfig](/visualstudio/mac/editorconfig)。

## <a name="code-consistency"></a>程式碼一致性

EditorConfig 檔案中的設定可讓您在程式碼基底中維持一致的編碼樣式及設定，例如縮排樣式、Tab 跳位寬度、行結尾字元、編碼等等，而不論您使用的編輯器或 IDE 為何。 例如，當以 C++ 撰寫程式碼時，如果您的程式碼基底慣例偏好縮排一律包含五個空白字元、文件使用 UTF-8 編碼方式，且每一行的結尾一律為 CR/LF，您可以設定 *.editorconfig* 檔案來做到這點。

您在個人專案上使用的編碼慣例，可能與用於小組專案的不同。 例如，您在編寫程式碼時，可能會偏好縮排時新增定位字元。 不過，您的小組可能會偏好縮排時新增四個空白字元，而不是定位字元。 EditorConfig 檔案讓您能擁有每個案例的組態，以解決此問題。

因為設定是包含在程式碼基底的檔案中，所以它們會隨著該程式碼基底四處移動。 只要您在符合 EditorConfig 規範的編輯器中開啟程式碼檔案，便會實作文字編輯器設定。 如需 EditorConfig 檔案的詳細資訊，請參閱 [EditorConfig.org](http://editorconfig.org/) 網站。

> [!NOTE]
> 由於建置錯誤或警告，目前無法在 CI/CD 管線中強制執行 EditorConfig 中設定的慣例。 任何樣式偏差只會顯示在 Visual Studio 編輯器中和 [錯誤清單] 中。

## <a name="supported-settings"></a>支援的設定

Visual Studio 中的編輯器支援 [EditorConfig 屬性](http://editorconfig.org/#supported-properties)的核心集：

- indent_style
- indent_size
- tab_width
- end\_of_line
- 字元集
- trim\_trailing_whitespace
- insert\_final_newline
- 根

除了 XML 以外的所有 Visual Studio 支援語言都支援 EditorConfig 編輯器設定。 此外，EditorConfig 支援 C# 及 Visual Basic 的[程式碼樣式](../ide/editorconfig-code-style-settings-reference.md)及[命名](../ide/editorconfig-naming-conventions.md)慣例。

## <a name="add-and-remove-editorconfig-files"></a>新增及移除 EditorConfig 檔案

將 EditorConfig 檔案新增至您的專案或程式碼基底，並不會將現有的樣式轉換為新的樣式。 例如，如果您在檔案中有使用定位字元設定格式的縮排，而且您新增了以空格縮排的 EditorConfig 檔案，縮排字元不會自動轉換為空格。 但是，新的程式碼會依照 EditorConfig 檔案設定格式。 此外，如果您想要設定文件的格式 ([編輯] > [進階] > [格式化文件] 或 **Ctrl**+**K**、**Ctrl**+**D**)，EditorConfig 檔案中的設定會套用到現有的程式碼。

如果您從專案或程式碼基底移除了 EditorConfig 檔案，就必須關閉並重新開啟任何開啟的程式碼檔案，以還原為新程式碼的全域編輯器設定。

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>將 EditorConfig 檔案新增至專案或解決方案

1. 在 Visual Studio 中開啟專案或解決方案。 選取專案或解決方案節點，視您的 *.editorconfig* 設定應套用至解決方案中的所有專案或僅只一個專案而定。 您也可以選取專案或解決方案中的資料夾，將 *.editorconfig* 檔案新增到此資料夾。

1. 從功能表列選擇 [專案] > [新增項目]，或按 **Ctrl**+**Shift**+**A**。

   [新增項目] 對話方塊隨即開啟。

1. 在左側的類別中，選擇 [一般]，然後選擇 [文字檔] 範本。 在 [名稱] 文字方塊中輸入 `.editorconfig`，然後選擇 [新增]。

   *.editorconfig* 檔案隨即出現在 [方案總管] 中，並在編輯器中開啟。

   ![方案總管中的 .editorconfig 檔案](media/editorconfig-in-solution-explorer.png)

1. 依需要編輯檔案，例如：

   ```ini
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

### <a name="other-ways-to-add-an-editorconfig-file"></a>新增 EditorConfig 檔案的其他方式

將 EditorConfig 檔案新資到您專案的方式有數種：

- 安裝 [EditorConfig 語言服務延伸模組](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) \(英文\) 以更輕鬆地將空白的 *.editorconfig* 檔案新增到您的專案。 安裝此延伸模組之後，只要在方案節點、專案節點或 [方案總管] 中的任何資料夾上，按一下滑鼠右鍵或從快顯功能表選擇 [加入] > [.editorconfig 檔案]。 此延伸模組也會改善 *.editorconfig* 檔案編輯體驗。

   ![新增具有延伸模組的 .editorconfig 檔案](media/editorconfig-extension-add.png)

- 嘗試 [適用於 Visual Studio 的 IntelliCode 延伸模組](/visualstudio/intellicode/intellicode-visual-studio)。 此實驗性延伸模組會從現有的程式碼推斷您的程式碼樣式，然後使用已定義的程式碼樣式喜好設定來建立非空白的 *.editorconfig* 檔案。

## <a name="file-hierarchy-and-precedence"></a>檔案階層和優先順序

當您將 *.editorconfig* 檔案新增到檔案階層中的資料夾時，其設定會套用到該層級 (含) 以下的所有適用檔案。 您也可以覆寫特定專案、程式碼基底，或程式碼基底組件的 EditorConfig 設定，這樣它就會使用和其他程式碼基底組件不同的慣例。 當您納入來自其他地方的程式碼，但不想變更其慣例時，這非常有用。

若要覆寫部分或全部的 EditorConfig 設定，請將 *.editorconfig* 檔案新增至您想要套用這些覆寫設定的檔案階層層級。 新的 EditorConfig 檔案設定會套用到相同層級和任何子目錄中的檔案。

![EditorConfig 階層](../ide/media/vside_editorconfig_hierarchy.png)

如果要覆寫部分而不是全部設定，請在 *.editorconfig* 檔案中僅指定那些設定。 只有明確列在較低層級檔案中的屬性才會被覆寫。 較高層級 *.editorconfig* 檔案中的其他設定仍繼續套用。 如果想要確保「不」套用「任何」較高層級 *.editorconfig* 檔案的設定到此程式碼基底組件，請在較低層級的 *.editorconfig* 檔案中新增 ```root=true``` 屬性：

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

將名為 *.editorconfig* 的新檔案新增到專案中，其中包含下列內容。 `[*.cs]` 設定表示這項變更只會套用到此專案中的 C# 程式碼檔案。

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

現在，當您按下 **Tab** 鍵，會得到定位點字元，而不是空白。

![以 TAB 鍵新增定位字元](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>疑難排解 EditorConfig 設定

如果目錄結構中的任何位置或在專案位置上方有一個 EditorConfig 檔案，Visual Studio 會將該檔案中的編輯器設定套用到您的編輯器。 在此情況下，您可能會看到狀態列中出現下列訊息：

   **「此檔案類型的使用者偏好由此專案的編碼慣例覆寫。」**

這表示，如果 [工具] > [選項] > [文字編輯器] 中的任何編輯器設定 (例如縮排大小及樣式、定位點大小或編碼慣例) 是在 EditorConfig 檔案中等於或高於目錄結構中的專案位置所指定，EditorConfig 檔案中的慣例就會覆寫 [選項] 中的設定。 您可以透過切換 [工具] > [選項] > [文字編輯器] 中的 [遵循專案編碼慣例] 選項來控制這個行為。 取消選取此選項會關閉 Visual Studio 的 EditorConfig 支援。

![編碼選項 - 遵循專案編碼慣例](media/coding_conventions_option.png)

您可以透過開啟命令提示字元，並從包含專案的磁碟根目錄中執行下列命令，以在父目錄中尋找任何 *.editorconfig* 檔案：

```Shell
dir .editorconfig /s
```

您可以在存放庫根目錄或專案所在目錄的 *.editorconfig* 檔案中設定 ```root=true``` 屬性，以控制 EditorConfig 慣例範圍。 Visual Studio 會在已開啟檔案的目錄和每個父目錄中尋找名為 *.editorconfig* 的檔案。 達到根檔案路徑，或者如果找到 ```root=true``` 的 *.editorconfig* 檔案時，搜尋就會結束。

## <a name="see-also"></a>另請參閱

- [.NET 程式碼樣式慣例](../ide/editorconfig-code-style-settings-reference.md)
- [.NET 命名慣例](../ide/editorconfig-naming-conventions.md)
- [為語言服務支援 EditorConfig](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](http://editorconfig.org/)
- [程式碼編輯器的功能](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio for Mac)](/visualstudio/mac/editorconfig)