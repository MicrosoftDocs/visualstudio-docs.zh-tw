---
title: "在 VisualStudio 中使用 EditorConfig 設定 | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload: multiple
ms.openlocfilehash: 0219ff704e22ab1c27d47e312825a66cb3a15166
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>使用 EditorConfig 建立可攜式自訂編輯器設定

在 Visual Studio 2017 中，您可以在專案或程式碼基底中新增 [EditorConfig](http://editorconfig.org/) 檔案，強制使用程式碼基底的所有人都使用一致的編碼樣式。 EditorConfig 設定優先於全域 Visual Studio 文字編輯器設定。 這表示您可以自訂每個程式碼基底，以使用該專案專屬的文字編輯器設定。 您仍然可以在 Visual Studio 的 [選項] 對話方塊中設定自己的個人編輯器喜好設定。 每當您使用沒有 .editorconfig 檔案的程式碼基底時，或 .editorconfig 檔案不覆寫特定的設定時，就會套用這些設定。 縮排樣式&mdash;定位點或空格，即為這類喜好設定的範例之一。

許多程式碼編輯器和 IDE，包括 Visual Studio，都支援 EditorConfig 設定。 它是隨附於程式碼的可攜式元件，甚至可以強制規範 Visual Studio 之外的編碼樣式。

## <a name="coding-consistency"></a>程式碼撰寫的一致性

EditorConfig 檔案中的設定可讓您在程式碼基底中維持一致的編碼樣式及設定，例如縮排樣式、Tab 跳位寬度、行結尾字元、編碼等等，而不論您使用的編輯器或 IDE 為何。 比方說，當以 C++ 編寫程式碼時，如果您的程式碼基底慣例偏好縮排一律包含五個空白字元、文件使用 UTF-8 編碼方式，且每一行的結尾一律為 CR/LF，您可以設定 .editorconfig 檔案來做到這點。

您在個人專案上使用的編碼慣例，可能與用於小組專案的不同。 例如，您在編寫程式碼時，可能會偏好縮排時新增定位字元。 不過，您的小組可能會偏好縮排時新增四個空白字元，而不是定位字元。 EditorConfig 檔案讓您能擁有每個案例的組態，以解決此問題。

因為設定是包含在程式碼基底的檔案中，所以它們會隨著該程式碼基底四處移動。 只要您在符合 EditorConfig 規範的編輯器中開啟程式碼檔案，便會實作文字編輯器設定。 如需 EditorConfig 檔案的詳細資訊，請參閱 [EditorConfig.org](http://editorconfig.org/) 網站。

## <a name="override-editorconfig-settings"></a>覆寫 EditorConfig 設定

當您將 .editorconfig 檔案新增到檔案階層中的資料夾時，其設定會套用到該層級 (含) 以下的所有適用檔案。 若要覆寫特定專案或程式碼基底的 EditorConfig 設定，使其使用與最上層 .editorconfig 檔案不同的慣例，只要將 .editorconfig 檔案新增到程式碼基底的存放庫或專案目錄的根目錄即可。 請務必將 ```root=true``` 屬性放入檔案中，讓 Visual Studio 不會在目錄結構中進一步尋找 .editorconfig 檔案。 新的 EditorConfig 檔案設定會套用到相同層級和任何子目錄中的檔案。

```
# top-most EditorConfig file
root = true
```

![EditorConfig 階層](../ide/media/vside_editorconfig_hierarchy.png)

EditorConfig 檔案是由上往下讀取，而且最接近的 EditorConfig 檔案最後才讀取。 會以讀取順序套用相符 EditorConfig 區段的慣例，因此最接近之檔案的慣例優先。

## <a name="supported-settings"></a>支援的設定

Visual Studio 中的編輯器支援一組核心 [EditorConfig 屬性](http://editorconfig.org/#supported-properties)中的下列項目：

- indent_style
- indent_size
- tab_width
- end\_of_line
- 字元集
- 根

除了 XML 以外的所有 Visual Studio 支援語言都支援 EditorConfig 編輯器設定。 此外，EditorConfig 支援 C# 及 Visual Basic 的[程式碼樣式](../ide/editorconfig-code-style-settings-reference.md)及[命名](../ide/editorconfig-naming-conventions.md)慣例。

## <a name="editing-editorconfig-files"></a>編輯 EditorConfig 檔案

Visual Studio 提供一些 IntelliSense 以供編輯 .editorconfig 檔案。 如果您編輯許多 .editorconfig 檔案，可能會發現 [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) (EditorConfig 語言服務) 延伸模組很有幫助。

在編輯您的 EditorConfig 檔案後，您必須重新載入程式碼檔，新的設定才會生效。

## <a name="adding-and-removing-editorconfig-files"></a>新增及移除 EditorConfig 檔案

將 EditorConfig 檔案新增至您的專案或程式碼基底，並不會將現有的樣式轉換為新的樣式。 例如，如果您在檔案中有使用定位字元設定格式的縮排，而且您新增了以空格縮排的 EditorConfig 檔案，縮排字元就不會轉換為空格。 但是，新的程式碼會依照 EditorConfig 檔案設定格式。

如果您從專案或程式碼基底移除了 EditorConfig 檔案，就必須關閉並重新開啟任何開啟的程式碼檔案，以還原為新程式碼的全域編輯器設定。

## <a name="example"></a>範例

以下範例顯示 C# 程式碼片段在將 .editorconfig 檔案新增至專案之前和之後的縮排狀態。 Visual Studio 文字編輯器 [選項] 對話方塊的 [定位字元] 設定已設為在按下 **Tab** 鍵時，產生空白字元。

![文字編輯器定位字元設定](../ide/media/vside_editorconfig_tabsetting.png)

如同預期，在下一行按下 **Tab** 鍵會藉由新增四個額外的空白字元來縮排該行。

![使用 EditorConfig 前的程式碼](../ide/media/vside_editorconfig_before.png)

我們會將稱為 .editorconfig 的新檔案新增到專案中，其中包含下列內容。 `[*.cs]` 設定表示這項變更只會套用到此專案中的 C# 程式碼檔案。

```
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

現在，當您按下 **Tab** 鍵，會得到定位點字元，而不是空白。

![以 TAB 鍵新增定位字元](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>疑難排解 EditorConfig 設定

如果目錄結構中的任何位置或在專案位置上方有一個 EditorConfig 檔案，Visual Studio 會將該檔案中的編輯器設定套用到您的編輯器。 在此情況下，您可能會看到狀態列中出現下列訊息：

   **「此檔案類型的使用者偏好由此專案的編碼慣例覆寫。」**

這表示，如果在其中指定 [工具]、[選項]、[文字編輯器] 中任何編輯器設定 (例如縮排大小及樣式、定位點大小或編碼慣例) 的 EditorConfig 檔案等於或高於目錄結構中的專案，EditorConfig 檔案中的慣例就會覆寫 [選項] 中的設定。 您可以藉由切換 [工具]、[選項]、[文字編輯器] 中的 [遵循專案編碼慣例] 選項來控制這個行為。 取消選取此選項會關閉 Visual Studio 的 EditorConfig 支援。

![編碼選項 - 遵循專案編碼慣例](media/coding_conventions_option.png)

您可以透過開啟命令提示字元，並從包含專案的磁碟根目錄中執行下列命令，在父目錄中尋找任何 .editorconfig 檔案：

```
dir .editorconfig /s
```

您可以在存放庫根目錄或專案所在目錄的 .editorconfig 檔案中設定 ```root=true``` 屬性，藉以控制 EditorConfig 慣例範圍。 Visual Studio 會在已開啟檔案的目錄和每個父目錄中尋找名為 .editorconfig 的檔案。 達到根檔案路徑，或者如果找到 ```root=true``` 的 .editorconfig 檔案時，搜尋就會結束。

## <a name="see-also"></a>另請參閱

[.NET 程式碼樣式慣例](../ide/editorconfig-code-style-settings-reference.md)  
[為語言服務支援 EditorConfig](../extensibility/supporting-editorconfig.md)  
[EditorConfig.org](http://editorconfig.org/)  
[在編輯器中撰寫程式碼](writing-code-in-the-code-and-text-editor.md)