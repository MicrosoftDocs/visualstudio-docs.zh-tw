---
title: EditorConfig
description: 使用 editorconfig 檔案在 Visual Studio for Mac 中啟用一致的專案編碼樣式。
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 553a8ceeae16b660115ea3c8e32e544e903a72af
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>建立和編輯自訂的 EditorConfig 檔案

在 Visual Studio for Mac 中，您可以在專案或程式碼基底中新增 [EditorConfig](http://editorconfig.org/) 檔案，強制使用程式碼基底的所有人都使用一致的編碼樣式。 在 EditorConfig 檔案中宣告的設定優先於全域 Visual Studio 文字編輯器設定。 在您的專案或程式碼基底中使用 EditorConfig 可以讓您為專案設定編碼樣式、喜好設定和警告。 這可讓所有 Visual Studio for Mac 使用者都能更容易遵守專案的編碼方式。

許多 IDE 和程式碼編輯器 (包括Visual Studio 2017) 都支援 [EditorConfig](http://editorconfig.org/) 檔案。 

## <a name="supported-settings"></a>支援的設定

Visual Studio 中的編輯器支援 [EditorConfig 屬性](http://editorconfig.org/#supported-properties)的核心集：

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig 也支援在 C# 中使用[程式碼樣式格式設定](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference)。

## <a name="add-an-editorconfig-file-to-a-project"></a>將 EditorConfig 檔案新增至專案

### <a name="adding-a-new-editorconfig-file"></a>新增新的 EditorConfig 檔案

1. 在 Visual Studio for Mac 中開啟專案。 選取您想要新增檔案的專案節點。

2. 選取專案節點後，移至 [檔案] > [新增檔案...] 在功能表列中開啟 [新增檔案] 對話方塊。

3. 選擇 [其他] > [空白文字檔] 並在**名稱**中輸入 `.editorconfig`。 按 [新增] 來建立檔案，並在編輯器中開啟：

    ![[新增檔案] 對話方塊](media/editorconfig-image1.png)

4. 編輯檔案。 例如: 

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. 新增檔案不會自動更新您的設定。 若要反映 `.editorconfig` 檔案中的設定，請選取專案節點，然後從功能表列中選擇 [編輯] > [格式化] > [格式化文件]：

    ![格式化文件功能表項目](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>新增現有的 EditorConfig 檔案

如果您正在處理已包含 `.editorconfig` 檔案的專案或方案，則無需執行任何操作即可套用設定。 任何新的程式碼都會依照 EditorConfig 的設定進行設定格式。 請注意，雖然 Visual Studio for Mac 會在方案層級遵守 `.editorconfig` 檔案，但由於以 `.` 開頭的檔案是 macOS 中的隱藏檔案，因此它們可能不會出現在 Solution Pad 中。

建議您重複使用專案中現有的 `.editorconfig` 檔案。 若要新增現有檔案，您必須先在 **Terminal** 中輸入下列命令，以在 Finder 中顯示隱藏的檔案：

```
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

一旦 `.editorconfig` 檔案可見，請將其拖曳至您的專案節點。 出現下列對話方塊時，請選取 [將檔案複製到目錄] 選項並選取 [確定]：

![格式化文件功能表項目](media/editorconfig-image3.png)

若要反映 `.editorconfig` 檔案中的設定，請選取專案節點，然後從功能表列中選擇 [編輯] > [格式化] > [格式化文件]。

## <a name="editing-an-editorconfig-file"></a>編輯 EditorConfig 檔案

EditorConfig 檔案使用簡單的檔案版面配置來指定設定，如下列示範中的說明：


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

如同[覆寫 EditorConfig 設定](#override-editorconfig-settings)一節所述，將 `root` 設定為 `true` 會將此檔案標記為程式碼基底頂端的檔案，並且會忽略專案中任何更高層級的 `.editorconfig` 檔案。

每個區段都以正方形 (**[]**) 大括弧表示，並指定應與下列屬性有關的檔案類型資訊。

在上述範例中，某些設定將會套用於專案中的所有檔案，而其他設定僅會新增至 C# 檔案。 以下螢幕擷取畫面顯示套用 `.editorconfig` 設定之前和之後的情況：

**之前**：

![套用 editorconfig 設定之前](media/editorconfig-image4.png)

**之後**：

![套用 editorconfig 設定之後](media/editorconfig-image5.png)

如需可用之 EditorConfig 設定的詳細資訊，請參閱 [EditorConfig 的 .NET 編碼慣例設定](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) 一文，以及官方文件中的 [Supported Properties](http://editorconfig.org/#supported-properties) (支援的屬性) 一節。

## <a name="override-editorconfig-settings"></a>覆寫 EditorConfig 設定

每個方案中可以有多個 `.editorconfig` 檔案。 Visual Studio for Mac 在方案中從上到下讀取 `.editorconfig` 檔案，並依此順序新增和覆寫設定。 這表示在 `.editorconfig` 中_最接近_您正在編輯之檔案的設定將會優先。 

如果想要確保「不」套用任何較高層級 `.editorconfig` 檔案的設定到此程式碼基底組件，請在較低層級頂端的 `.editorconfig` 檔案中新增 `root=true` 屬性：

```EditorConfig
# top-most EditorConfig file
root = true
```