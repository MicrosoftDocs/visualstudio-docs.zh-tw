---
title: 尋找和取代文字，及多重游標選取
description: 瞭解「尋找和取代」功能，以及如何使用它來尋找和取代模式的實例。
ms.custom: SEO-VS-2020
ms.date: 10/17/2020
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 534d25c97977d058f0b4137955e44e3d544b3878
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932601"
---
# <a name="find-and-replace-text"></a>尋找和取代文字

您可以在 Visual Studio 編輯器中使用 [尋找和取代](#find-and-replace-control) (**Ctrl**+**F** 或 **Ctrl**+**H**) 或 [檔案中尋找/取代](#find-in-files-and-replace-in-files) (**Ctrl**+**Shift**+**F** 或 **Ctrl**+**Shift**+**H**) 來尋找和取代文字。 您也可以使用[多重游標選取](#multi-caret-selection)，僅尋找和取代模式的「某些」執行個體。

> [!TIP]
> 如果您要重新命名程式碼符號 (例如變數和方法)，比起使用尋找和取代，最好是 *[重構](../ide/reference/rename.md)* 它們。 重構是智慧型功能，可了解範圍，而尋找和取代則會盲目地取代所有執行個體。

尋找和取代功能位在編輯器的某些其他文字型視窗 (例如 [尋找結果] 視窗)、設計工具視窗 (例如 XAML 設計工具和 Windows Form 設計工具)，以及工具視窗中。

您可以將搜尋範圍設為目前文件、目前方案或一組自訂的資料夾。 您也可以指定一組副檔名來搜尋多個檔案。 請使用 .NET [規則運算式](../ide/using-regular-expressions-in-visual-studio.md)來自訂搜尋語法。

> [!TIP]
> [尋找/命令](../ide/find-command-box.md)方塊可提供作為工具列控制項，但預設為不可見。 若要顯示 [尋找/命令] 方塊，請選取 [標準] 工具列上的 [新增或移除按鈕]，然後選取 [尋找]。

## <a name="find-and-replace-control"></a>尋找和取代控制項

- 按 **Ctrl** + **F** 作為快捷方式，以在目前的檔案中 *尋找* 字串。
- 按 **Ctrl** + **H** 作為快捷方式，以 *尋找和取代* 目前檔案中的字串。

[尋找和取代] 控制項會出現在程式碼編輯器視窗的右上角。 它會立即醒目提示目前文件中每個出現的指定搜尋字串。 您可以選擇搜尋控制項上的 [找下一個] 按鈕或 [找上一個] 按鈕，以從第一個出現位置巡覽至另一個出現位置。

![Visual Studio 中的尋找和取代](media/find-and-replace-box.png)

您可以選擇 [尋找] 文字方塊旁的按鈕，以存取取代選項。 若要一次執行一個取代，請選擇 [取代] 文字方塊旁的 [取代下一個] 按鈕。 若要取代所有相符項目，請選擇 [全部取代] 按鈕。

若要變更相符項目的醒目提示色彩，請選擇 [工具] 功能表，並選取 [選項]，然後選擇 [環境]，再選取 [字型和色彩]。 在 [顯示設定] 清單中，選取 [文字編輯器]，然後在 [顯示項目] 清單中選取 [尋找醒目提示 (副檔名)]。

### <a name="search-tool-windows"></a>搜尋工具視窗

您可以選取 [編輯] > [尋找和取代] 或按 **Ctrl+F**，以使用程式碼或文字視窗中的 [尋找] 控制項 (例如 [輸出] 視窗和 [尋找結果] 視窗)。

部分工具視窗中也提供 [ **尋找** ] 控制項的版本。 例如，您可以在搜尋方塊中輸入文字，以篩選 [工具箱] 視窗中的控制項清單。 可讓您搜尋其內容的其他工具視窗包含 [方案總管]、[屬性] 視窗和 [Team Explorer]。

## <a name="find-in-files-and-replace-in-files"></a>檔案中尋找和檔案中取代

- 按 **Ctrl** + **Shift** + **F** 作為快捷方式，以在多個檔案中 *尋找* 字串。
- 按 **Ctrl** + **Shift** + **H** 做為 *尋找和取代* 多個檔案中字串的快捷方式。

[檔案中尋找/取代] 的運作方式與 [尋找和取代] 控制項類似，不同之處在於您可以定義搜尋範圍。 您不只可以在編輯器中搜尋目前開啟的檔案，還可以搜尋所有開啟的文件、整個方案、目前專案以及選取的資料夾集。 您也可以依副檔名進行搜尋。 若要存取 [檔案中尋找/取代] 對話方塊，請選取 [編輯] 功能表上的 [尋找和取代] (或按 **Ctrl**+**Shift**+**F**)。

![Visual Studio 中的檔案中尋找](media/find-in-files-box.png)

### <a name="find-results"></a>尋找結果

當您選擇 [全部尋找] 時，會開啟 [尋找結果] 視窗，並列出您搜尋的相符項目。 在清單中選取結果會顯示相關聯的檔案，並反白顯示相符項目。 如果尚未開啟檔案進行編輯，則會在索引標籤牆右側的預覽索引標籤中開啟它。 您可以使用 [尋找] 控制項來搜尋 [尋找結果] 清單。

### <a name="create-custom-search-folder-sets"></a>建立自訂搜尋資料夾集

您可以選擇 [ **選擇搜尋資料夾** ] 按鈕來定義搜尋範圍 (看 **起來像)** [ **查詢** ] 方塊旁。 在 [選擇搜尋資料夾] 對話方塊中，您可以指定一組要搜尋的資料夾，並且可以儲存規格，以在稍後重複使用。

> [!TIP]
> 如果遠端電腦的磁碟機已對應至本機電腦，您可以指定遠端電腦上要搜尋的資料夾。

### <a name="create-custom-component-sets"></a>建立自訂元件集

您可以選擇 [查詢] 方塊旁的 [編輯自訂元件集] 按鈕，將元件集定義為搜尋範圍。 您可以指定已安裝的 .NET 或 COM 元件、Visual Studio 方案中包含的專案，或是任何元件或類型程式庫 *(.dll*、 *.tlb*、 *.olb*、 *.exe* 或 *.ocx*) 。 若要搜尋參考，請選取 [查詢參考] 方塊。

## <a name="multi-caret-selection"></a>多重游標選取

> [!NOTE]
> 本節適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[區塊選取](/visualstudio/mac/block-selection)。

**已在 Visual Studio 2017 15.8 版引進**

使用「多重游標選取」，同時對兩處以上進行相同的編輯。 舉例來說，您可以同時在多個位置插入相同的文字或修改現有文字。

在下列螢幕擷取畫面中，在三個位置選取了 `-0000`；如果使用者按下 **Delete**，這三個選取範圍都會刪除：

![Visual Studio 中的 XML 檔案多重游標選取](media/multi-caret-selection.png)

若要選取多個游標，請像平常一樣按一下或選取第一個文字，然後在您於其他每個位置按一下或選取文字時，按著 **Alt**。 您也可以自動將相符的文字新增為其他選取項範圍，或選取文字方塊，在每一行以同樣方式編輯。

> [!TIP]
> 若您已在 [工具] > 選項 中選擇 **Alt** 作為按一下滑鼠「移至定義」的輔助按鍵，就會停用多重游標選取。

### <a name="commands"></a>命令

使用下列按鍵與動作可執行多重游標選取行為：

|快速鍵|動作|
|-|-|
|**Ctrl** +**Alt** + 按一下|新增第二個游標|
|**Ctrl** +**Alt** + 按兩下|新增第二個文字選取範圍|
|**Ctrl** +**Alt** + 按一下 + 拖曳|新增第二個選取範圍|
|**Shift** +**Alt** +**.**|將下一個相符文字新增為選取範圍|
|**Shift** +**Alt** +**;**|將所有相符的文字新增為選取範圍|
|**Shift** +**Alt** +**,**|移除最後一個選取項目|
|**Shift** +**Alt**+**/**|跳過下一個相符的項目|
|**Alt** + 按一下|新增方塊選取範圍|
|**Esc** 或按一下|清除所有選取範圍|

有些命令也可在 [編輯] 功能表取得，在 [多重游標]下：

:::image type="content" source="media/edit-menu-multiple-carets-find-replace.png" alt-text="Visual Studio 中 [多重游標] 飛出功能表的螢幕擷取畫面":::

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中使用正則運算式](../ide/using-regular-expressions-in-visual-studio.md)
- [在 Visual Studio 中重構程式碼](../ide/refactoring-in-visual-studio.md)
- [區塊選取 (Visual Studio for Mac)](/visualstudio/mac/block-selection)
