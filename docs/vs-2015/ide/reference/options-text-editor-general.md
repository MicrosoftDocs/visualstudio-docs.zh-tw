---
title: 一般、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
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
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662254"
---
# <a name="options-text-editor-general"></a>一般、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

此對話方塊可讓您變更 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 程式碼和文字編輯器的全域設定。 若要顯示這個對話方塊，請按一下 [工具]**** 功能表上的 [選項]****，並展開 [文字編輯器]**** 資料夾，然後按一下 [一般]****。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="settings"></a>設定
 當選取時，拖放文字編輯，可讓您選取文字，然後將它拖曳到目前檔中的另一個位置，或任何其他開啟的檔中，以移動文字。

 自動分隔符號反白顯示選取時，會反白顯示分隔參數或專案值組的分隔符號，以及成對的大括弧。

 選取 [程式碼編輯器] 時追蹤變更，選取範圍邊界會出現一條垂直黃色線，以標示最近儲存檔案之後變更的程式碼。 當您儲存變更時，垂直線會變成綠色。

 依預設，自動偵測不含簽章的 UTF-8 編碼，編輯器會藉由搜尋位元組順序標記或字元集標記來偵測編碼。 如果目前文件中找不到編碼方式，程式碼編輯器就會嘗試掃描位元組序列以自動偵測 UTF-8 編碼。 若要停用自動偵測編碼，請清除此選項。

## <a name="display"></a>顯示
 選取 [選取邊界] 時，會沿著編輯器文字區域的左邊緣顯示垂直邊界。 您可以按一下此邊界來選取整行文字，或按一下並拖曳以選取連續文字行。

|選取範圍邊界起點|選取範圍邊界終點|
|-------------------------|--------------------------|
|![HTMLpageSelectionMarginOn 螢幕擷取畫面](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff 螢幕擷取畫面](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|

 選取 [指標邊界] 時，會在編輯器文字區域的左邊緣之外顯示垂直邊界。 當您按一下此邊界時，會顯示文字相關的圖示和工具提示。 比方說，指示區邊界會出現中斷點或工作清單捷徑。 列印時不會印出指示區邊界的資訊。

 選取時，垂直捲動條會顯示垂直捲動條，讓您向上和向下滾動，以查看落在編輯器的流覽區域以外的專案。 如果未顯示垂直捲軸，您可以使用 Page Up、Page Down 鍵和方向鍵來捲動。

 當選取時，水準捲軸會顯示水準捲軸，讓您從側邊移至邊緣，以查看落在編輯器的流覽區域以外的專案。 如果未顯示水平捲軸，您可以使用方向鍵捲動。

 當選取 [目前的行] 時，反白顯示目前的行，在游標所在的程式程式碼周圍顯示灰色方塊。

## <a name="see-also"></a>另請參閱
 [選項、文字編輯器、所有語言](../../ide/reference/options-text-editor-all-languages.md)[選項、文字編輯器、所有語言、](../../ide/reference/options-text-editor-all-languages-tabs.md)索引標籤[選項、文字編輯器、副檔名](../../ide/reference/options-text-editor-file-extension.md)[識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)[使用 IntelliSense](../../ide/using-intellisense.md) [自訂編輯器](../../ide/customizing-the-editor.md)
