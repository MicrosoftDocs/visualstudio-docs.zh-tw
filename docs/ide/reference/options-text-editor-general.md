---
title: 一般、文字編輯器、選項
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cb2a939fb569ca9c50e6334fa7b836a6953dca4
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219155"
---
# <a name="options-text-editor-general"></a>一般、文字編輯器、選項

此對話方塊可讓您變更 Visual Studio 程式碼和文字編輯器的全域設定。 若要顯示這個對話方塊，請選取 [工具] 功能表上的 [選項]，並展開 [文字編輯器] 資料夾，然後選取 [一般]。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="settings"></a>設定

### <a name="drag-and-drop-text-editing"></a>拖放式文字編輯

選取時，您可使用滑鼠將文字拖曳到目前文件或任何其他開啟文件內的其他位置，藉此移動文字。

### <a name="automatic-delimiter-highlighting"></a>自動分隔符號反白顯示

選取時，會反白顯示用來分隔參數或項目值組的分隔符號字元，以及成對大括弧。

### <a name="track-changes"></a>追蹤變更

選取程式碼編輯器時，選取範圍邊界會出現黃色垂直線，以標示最近儲存檔案之後有所變更的程式碼。 當您儲存變更時，垂直線會變成綠色。

### <a name="auto-detect-utf-8-encoding-without-signature"></a>自動偵測無簽章 UTF-8 編碼

根據預設，編輯器會搜尋位元組順序標記或字元集標籤以偵測編碼方式。 如果目前文件中找不到編碼方式，程式碼編輯器就會嘗試掃描位元組序列以自動偵測 UTF-8 編碼。 若要停用自動偵測編碼，請清除此選項。

## <a name="display"></a>顯示器

### <a name="selection-margin"></a>選取範圍邊界

選取時，編輯器文字區域的左邊緣處會顯示垂直邊界。 您可以按一下此邊界來選取整行文字，或按一下並拖曳以選取連續文字行。

|選取範圍邊界起點|選取範圍邊界終點|
| - | - |
|![HTMLpageSelectionMarginOn 螢幕擷取畫面](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff 螢幕擷取畫面](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>指示區邊界

選取時，編輯器文字區域的左邊緣外圍會顯示垂直邊界。 當您按一下此邊界時，會顯示文字相關的圖示和工具提示。 比方說，指示區邊界會出現中斷點或工作清單捷徑。 列印時不會印出指示區邊界的資訊。

### <a name="highlight-current-line"></a>反白顯示目前的行

選取時，灰色方塊會框住游標所在的程式碼行。

## <a name="see-also"></a>另請參閱

- [所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages.md)
- [索引標籤、所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [副檔名、文字編輯器、選項](../../ide/reference/options-text-editor-file-extension.md)
- [識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [自訂編輯器](../../ide/customizing-the-editor.md)
- [使用 IntelliSense](../../ide/using-intellisense.md)