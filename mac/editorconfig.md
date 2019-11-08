---
title: EditorConfig
description: 使用 editorconfig 檔案在 Visual Studio for Mac 中啟用一致的專案編碼樣式。
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 6f6241c114d636cc8cb01cf5c4bf9ba2b5106701
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73716898"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>建立和編輯自訂的 EditorConfig 檔案

在 Visual Studio for Mac 中，您可以在專案或方案中新增 [EditorConfig](https://editorconfig.org/) 檔案，強制使用程式碼基底的所有人都使用一致的編碼樣式。 在 EditorConfig 檔案中宣告的設定優先於全域 Visual Studio for Mac 文字編輯器設定。 在您的專案或程式碼基底中使用 EditorConfig 檔案可讓您為專案設定編碼樣式、喜好設定和警告。 因為檔案是程式碼基底的一部分，所以更容易讓所有使用者都遵守專案的編碼方式，不論他們使用 IDE 還是程式碼編輯器都一樣。

許多 IDE 和程式碼編輯器 (包括Visual Studio) 都支援 [EditorConfig](https://editorconfig.org/) 檔案。

## <a name="supported-settings"></a>支援的設定

Visual Studio for Mac 中的編輯器支援 [EditorConfig 屬性](https://editorconfig.org/#supported-properties)的核心集：

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig 也支援 C# 中的[編碼慣例](/visualstudio/ide/editorconfig-code-style-settings-reference)。

## <a name="add-an-editorconfig-file-to-a-project"></a>將 EditorConfig 檔案新增至專案

### <a name="adding-a-new-editorconfig-file"></a>新增新的 EditorConfig 檔案

1. 在 Visual Studio for Mac 中開啟專案。 選取您想要在其中新增 EditorConfig 檔案的方案或專案節點。 將檔案新增至方案目錄會將 .editorconfig 設定套用至方案中的所有專案。

2. 以滑鼠右鍵按一下節點，然後選取 [新增] > [新增檔案] 以開啟 [新增檔案] 對話方塊：

    ![內容功能表項目](media/editorconfig-image0.png)

3. 選擇 [其他] > [空白文字檔] 並在**名稱**中輸入 `.editorconfig`。 按 [新增] 來建立檔案，並在編輯器中開啟：

    ![[新增檔案] 對話方塊](media/editorconfig-image1.png)

    在方案層級新增項目，會自動建立它並在 [方案項目] 資料夾中將它巢狀處理：

    ![Solution Pad 中顯示的方案項目](media/editorconfig-image1a.png)

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

4. `.editorconfig` 檔案中的設定會套用至您撰寫的任何新程式碼，但可能需要重新格式化現有程式碼，以與新的設定一致。 若要將 `.editorconfig` 檔案中的設定套用至現有來源檔案，請開啟檔案，然後從功能表列中選擇 [編輯] > [格式化] > [格式化文件]：

    ![格式化文件功能表項目](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>新增現有的 EditorConfig 檔案

如果您正在處理已包含 `.editorconfig` 檔案的專案或方案，則無需執行任何操作即可套用設定。 任何新的程式碼都會依照 EditorConfig 的設定進行設定格式。

建議您重複使用專案中現有的 `.editorconfig` 檔案。 若要新增現有檔案，請執行下列作業：

1. 以滑鼠右鍵按一下您想要在其中新增它的資料夾，然後選取 [新增] > [新增檔案]。

2. 瀏覽至所需檔案的目錄。

3. 開頭為 `.` 的檔案 (例如 `.editorconfig`) 是 macOS 中的隱藏檔案，因此請按 **Command + Shift + .** 將 `.editorconfig` 檔案設為可見。

4. 選取 `.editorconfig` 檔案，然後按一下 [開啟]：

    ![新增檔案視窗](media/editorconfig-image3b.png)

5. 出現下列對話方塊時，請選取 [將檔案複製到目錄] 選項並選取 [確定]：

    ![[將檔案新增至資料夾] 對話方塊選項](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>反映 .editorconfig 設定

在您將 EditorConfig 檔案新增至程式碼基底之後，會根據指定的設定自動格式化任何新增的程式碼。 除非您格式化程式碼基底，否則現有程式碼不會自動反映設定。

若要反映 `.editorconfig` 檔案中的設定，請選取方案節點，然後從功能表列中選擇 [編輯] > [格式化] > [格式化文件]：

![功能表列中的 [格式化文件]](media/editorconfig-image3a.png)

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

每個區段都以正方形 ( **[]** ) 大括弧表示，並指定應與下列屬性有關的檔案類型資訊。

在上述範例中，某些設定將會套用於專案中的所有檔案，而其他設定僅會新增至 C# 檔案。 以下螢幕擷取畫面顯示套用 `.editorconfig` 設定之前和之後的情況：

**之前**：

![套用 editorconfig 設定之前](media/editorconfig-image4.png)

**之後**：

![套用 editorconfig 設定之後](media/editorconfig-image5.png)

如需可用之 EditorConfig 設定的詳細資訊，請參閱 [EditorConfig 的 .NET 編碼慣例設定](/visualstudio/ide/editorconfig-code-style-settings-reference) 一文，以及官方文件中的 [Supported Properties](https://editorconfig.org/#supported-properties) (支援的屬性) 一節。

## <a name="override-editorconfig-settings"></a>覆寫 EditorConfig 設定

每個方案中可以有多個 `.editorconfig` 檔案。 Visual Studio for Mac 會從上到下讀取方案中的 `.editorconfig` 檔案，並新增和覆寫進行中的設定。這表示將會優先使用「最接近」所編輯檔案之 `.editorconfig`中的設定。 設定取自相同資料夾 (若存在) 中的 `.editorconfig` 檔案，然後取自父資料夾 (若存在) 中的 `.editorconfig` 等等， 直到找到 `root=true`。

如果想要確保「不」套用任何較高層級 `.editorconfig` 檔案的設定到此程式碼基底組件，請在較低層級頂端的 `.editorconfig` 檔案中新增 `root=true` 屬性：

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>請參閱

- [使用 EditorConfig 建立自訂編輯器設定 (Windows 上的 Visual Studio)](/visualstudio/ide/create-portable-custom-editor-options)