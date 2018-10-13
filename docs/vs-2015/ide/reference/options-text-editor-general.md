---
title: 一般、文字編輯器、選項 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 47fb93aebeecf50ae20616fc47033be60724cd45
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257825"
---
# <a name="options-text-editor-general"></a>一般、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
此對話方塊可讓您變更 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 程式碼和文字編輯器的全域設定。 若要顯示這個對話方塊，請按一下 [工具] 功能表上的 [選項]，並展開 [文字編輯器] 資料夾，然後按一下 [一般]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="settings"></a>設定  
 拖放式文字編輯  
 選取時，您可使用滑鼠將文字拖曳到目前文件或任何其他開啟文件內的其他位置，藉此移動文字。  
  
 自動分隔符號反白顯示  
 選取時，會反白顯示用來分隔參數或項目值組的分隔符號字元，以及成對大括弧。  
  
 追蹤變更  
 選取程式碼編輯器時，選取範圍邊界會出現黃色垂直線，以標示最近儲存檔案之後有所變更的程式碼。 當您儲存變更時，垂直線會變成綠色。  
  
 自動偵測無簽章 UTF-8 編碼  
 根據預設，編輯器會搜尋位元組順序標記或字元集標籤以偵測編碼方式。 如果目前文件中找不到編碼方式，程式碼編輯器就會嘗試掃描位元組序列以自動偵測 UTF-8 編碼。 若要停用自動偵測編碼，請清除此選項。  
  
## <a name="display"></a>顯示器  
 選取範圍邊界  
 選取時，編輯器文字區域的左邊緣處會顯示垂直邊界。 您可以按一下此邊界來選取整行文字，或按一下並拖曳以選取連續文字行。  
  
|選取範圍邊界起點|選取範圍邊界終點|  
|-------------------------|--------------------------|  
|![HTMLpageSelectionMarginOn 螢幕擷取畫面](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff 螢幕擷取畫面](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 指示區邊界  
 選取時，編輯器文字區域的左邊緣外圍會顯示垂直邊界。 當您按一下此邊界時，會顯示文字相關的圖示和工具提示。 比方說，指示區邊界會出現中斷點或工作清單捷徑。 列印時不會印出指示區邊界的資訊。  
  
 垂直捲軸  
 選取時，會顯示垂直捲軸；您可以上下捲動來檢視位於編輯器檢視區域外的項目。 如果未顯示垂直捲軸，您可以使用 Page Up、Page Down 鍵和方向鍵來捲動。  
  
 水平捲軸  
 選取時，會顯示水平捲軸；您可以左右捲動來檢視位於編輯器檢視區域外的項目。 如果未顯示水平捲軸，您可以使用方向鍵捲動。  
  
 反白顯示目前的行  
 選取時，灰色方塊會框住游標所在的程式碼行。  
  
## <a name="see-also"></a>另請參閱  
 [所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages.md)   
 [索引標籤、所有語言、文字編輯器、選項](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [副檔名、文字編輯器、選項](../../ide/reference/options-text-editor-file-extension.md)   
 [識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [自訂編輯器](../../ide/customizing-the-editor.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)



