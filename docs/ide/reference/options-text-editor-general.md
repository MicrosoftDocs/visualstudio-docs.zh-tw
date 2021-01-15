---
title: 一般、文字編輯器、選項
description: 瞭解如何使用 [一般] 頁面來變更 Visual Studio 程式碼和文字編輯器的全域設定。
ms.custom: SEO-VS-2020
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.Advanced
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c76ea1729fa84bee97458f131e18f64281b76567
ms.sourcegitcommit: 4ee20054afe7bcf5c0aed504dec01e18059fbbd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226496"
---
# <a name="options-dialog-box-text-editor--general"></a>選項對話方塊：文字編輯器 \> 一般

此對話方塊可讓您變更 Visual Studio 程式碼和文字編輯器的全域設定。 若要顯示這個對話方塊，請選取 [工具] 功能表上的 [選項]，並展開 [文字編輯器] 資料夾，然後選取 [一般]。

## <a name="settings"></a>設定

### <a name="drag-and-drop-text-editing"></a>拖放式文字編輯

選取時，您可使用滑鼠將文字拖曳到目前文件或任何其他開啟文件內的其他位置，藉此移動文字。

### <a name="automatic-delimiter-highlighting"></a>自動分隔符號反白顯示

選取時，會反白顯示用來分隔參數或項目值組的分隔符號字元，以及成對大括弧。

### <a name="track-changes"></a>追蹤變更

選取程式碼編輯器時，選取範圍邊界會出現黃色垂直線，以標示最近儲存檔案之後有所變更的程式碼。 當您儲存變更時，垂直線會變成綠色。

### <a name="auto-detect-utf-8-encoding-without-signature"></a>自動偵測無簽章 UTF-8 編碼

根據預設，編輯器會搜尋位元組順序標記或字元集標籤以偵測編碼方式。 如果目前文件中找不到編碼方式，程式碼編輯器就會嘗試掃描位元組序列以自動偵測 UTF-8 編碼。 若要停用自動偵測編碼，請取消選取此選項。

### <a name="follow-project-coding-conventions"></a>遵循專案編碼慣例

選取時，專案的指定程式碼慣例會覆寫您用於個人專案的任何程式碼慣例。

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>啟用按一下滑鼠即執行前往定義

選取時，您可以按下 **Ctrl** 並暫留在元素上，同時按一下滑鼠。 這樣會帶您前往所選取元素的定義。 您也可以從 [使用輔助按鍵] 下拉式清單選擇 [Alt] 或 [Ctrl + Alt]。

選取 [在預覽檢視中開啟定義] 核取方塊，以在視窗中顯示元素的定義，而不需從您目前在程式碼編輯器中的位置尋覽到他處。

## <a name="display"></a>顯示

### <a name="selection-margin"></a>選取範圍邊界

選取時，編輯器文字區域的左邊緣處會顯示垂直邊界。 您可以按一下此邊界來選取整行文字，或按一下並拖曳以選取連續文字行。

|選取範圍邊界起點|選取範圍邊界終點|
| - | - |
|![HTMLpageSelectionMarginOn 螢幕擷取畫面](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff 螢幕擷取畫面](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>指示區邊界

選取時，編輯器文字區域的左邊緣外圍會顯示垂直邊界。 當您按一下此邊界時，會顯示文字相關的圖示和工具提示。 比方說，指示區邊界會出現中斷點或工作清單捷徑。 列印時不會印出指示區邊界的資訊。

### <a name="highlight-current-line"></a>反白顯示目前的行

選取時，灰色方塊會框住游標所在的程式碼行。

### <a name="show-structure-guide-lines"></a>顯示結構輔助線

選取時，編輯器中會出現對齊結構化程式碼區塊的垂直線，可讓您輕鬆地識別個別程式碼區塊。

### <a name="show-file-health-indicator"></a>顯示檔案健康情況指標

選取時，會在編輯器的左下角顯示檔案健康情況指標狀態 (錯誤、警告) 列和程式碼清除選項。

## <a name="see-also"></a>請參閱

- [所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages.md)
- [索引標籤、所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [選項、文字編輯器、副檔名](../../ide/reference/options-text-editor-file-extension.md)
- [識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [自訂編輯器](../how-to-change-text-case-in-the-editor.md)
- [使用 IntelliSense](../../ide/using-intellisense.md)
