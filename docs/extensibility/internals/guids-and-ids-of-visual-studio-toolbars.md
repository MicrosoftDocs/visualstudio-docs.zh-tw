---
title: "Guid 和 Id 的 Visual Studio 工具列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bbb14818cebb35f703ec6f5ade084d96ac383d6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Guid 和 Id 的 Visual Studio 工具列
本主題列舉的 GUID 和 ID 值的 Visual Studio 整合式的開發環境 (IDE) 中包含的工具列和包含的群組。 這些值會定義在.vsct 檔案會安裝 Visual Studio SDK 的一部分。 如需詳細資訊，請參閱[IDE-Defined 命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
> [!NOTE]
>  許多的 Visual Studio 工具列不由 Visual Studio 中，而且其 GUID 定義並不是公用的識別碼值。 本主題列出 Visual Studio SDK.vsct 檔案中定義的工具列。  
  
 如需如何使用 IDE.vsct 檔案中定義的物件的詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 Visual Studio IDE 所提供的預設工具列會使用 GUID `guidSHLMainMenu`，指定，否則使用 guid: id 語法除外。  
  
## <a name="ide-toolbars"></a>IDE 工具列  
 下列工具列會提供在 Visual Studio IDE。 可以顯示的工具列上選取它們**工具列** 子功能表**工具**功能表。 本節中不包含的工具視窗的工具列。  
  
 只有群組可以直接從工具列下降。 若要加入群組，設定其父代的 GUID 和 ID 的工具列。 若要將按鈕加入至工具列，設定其父群組工具列上。  
  
|工具列|識別碼|  
|-------------|--------|  
|標準|IDM_VS_TOOL_STANDARD|  
|組建|IDM_VS_TOOL_BUILD|  
|文字編輯器|IDM_VS_TOOL_TEXTEDITOR|  
|偵錯|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|偵錯位置|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>特殊的工具列  
 這些工具列會由 Visual Studio IDE 中，但可提供特殊的功能，且未裝載命令群組。  
  
|工具列|識別碼|  
|-------------|--------|  
|Add 命令|IDM_VS_TOOL_ADDCOMMAND|  
|未定義|IDM_VS_TOOL_UNDEFINED|  
|XML 結構描述|IDM_VS_TOOL_SCHEMA|  
|XML 資料|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>在 IDE 工具列上的群組  
 若要將按鈕加入到 [標準] 工具列中，設定下列群組的其中一個為其父系。 群組會依照為父工具列。  
  
### <a name="standard-toolbar-groups"></a>[標準] 工具列的群組  
  
|名稱|識別碼|  
|----------|--------|  
|儲存檔案/開啟|IDG_VS_TOOLSB_SAVEOPEN|  
|剪下/複製|IDG_VS_TOOLSB_CUTCOPY|  
|復原/取消復原|IDG_VS_TOOLSB_UNDOREDO|  
|執行/組建|IDG_VS_TOOLSB_RUNBUILD|  
|搜尋|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|新的視窗|IDG_VS_TOOLSB_NEWWINDOWS|  
|載入/儲存|IDG_VS_WINDOWUI_LOADSAVE|  
|量測計|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>建立工具列群組  
  
|名稱|識別碼|  
|----------|--------|  
|建置列|IDG_VS_BUILDBAR|  
|取消|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>文字編輯器 工具列上的群組  
  
|名稱|識別碼|  
|----------|--------|  
|完成|IDM_VS_TOOL_TEXTEDITOR|  
|Indent|IDG_VS_EDITTOOLBAR_INDENT|  
|註解|IDG_VS_EDITTOOLBAR_COMMENT|  
|書籤|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>偵錯 工具列的群組  
  
|名稱|識別碼|  
|----------|--------|  
|執行|IDM_DEBUG_TOOLBAR|  
|逐步執行|IDG_DEBUG_TOOLBAR_STEPPING|  
|監看式|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>偵錯位置工具列群組  
  
|名稱|識別碼|  
|----------|--------|  
|偵錯位置|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>工具視窗工具列  
 工具列會顯示直接在 IDE 中或在工具視窗例如**方案總管 中**。 因為沒有.vsct 檔案中定義工具視窗，工具視窗工具列中沒有已定義父代。 相反地，它們都放在程式碼中。 下表顯示在 ide 中工具視窗顯示的工具列和它們所包含的命令群組。  
  
> [!NOTE]
>  工具列和群組使用的 GUID `guidSHLMainMenu`，指定，否則使用 guid: id 語法除外。 指定工具列的 GUID，則它也適用於從該工具列下降的群組。  
  
|工具視窗|工具列|群組|  
|-----------------|-------------|------------|  
|底下提供說明，包括方案總管|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1...5|  
|伺服器總管|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|屬性|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|類別檢視|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|類別檢視|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|物件瀏覽器|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|物件瀏覽器|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|輸出|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|尋找和取代|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|尋找結果 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|尋找結果 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|程式碼片段|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|書籤|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|工作清單|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|使用者工作|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|錯誤清單|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|呼叫瀏覽器|IDM_VS_TOOL_CALLBROWSER1...16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|中斷點|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|反組譯碼|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|記憶體 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1...4|IDG_MEMORY_EXPRESSION1...4<br /><br /> IDG_MEMORY_COLUMNS1...4|  
|處理序|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>請參閱  
 [功能表控制器加入工具列](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [新增工具列加入工具視窗](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Visual Studio 功能表的 GUID 和 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)