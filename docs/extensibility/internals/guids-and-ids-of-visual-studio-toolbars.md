---
title: Visual Studio 工具列的 GUID 和 IT |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe42821cdacc038d767e52373d45ddd7b8954323
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708233"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Visual Studio 工具列的 GUID 和 IT
本主題枚舉 Visual Studio 整合式開發環境 (IDE) 中包含的工具列的 GUID 和 ID 值及其包含的群組。 這些值在作為可視化工作室 SDK 的一部分安裝的 *.vsct*檔中定義。 有關詳細資訊,請參閱[IDE 定義的指令、選單和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

> [!NOTE]
> Visual Studio 提供的許多工具列不是由 Visual Studio 定義的,並且其 GUID 和 ID 值不為公共。 本主題僅列出在 Visual Studio SDK *.vsct*檔案中定義的工具列。

 有關如何處理*在 .vsct*檔中定義的 IDE 物件的詳細資訊,請參閱[延伸選單和指令](../../extensibility/extending-menus-and-commands.md)。

 Visual Studio IDE 提供的預設工具列使用`guidSHLMainMenu`GUID, 除非使用`GUID:ID`語法以其他方式指定。

## <a name="ide-toolbars"></a>IDE 工具列
 以下工具列由可視化工作室 IDE 提供。 工具列可以通過在 **「工具**」功能表的**工具列**子功能表上選擇來顯示它們。 工具視窗中的工具列不包括在此部分中。

 只有組可以直接從工具列下降。 要添加組,應將其父級設置為工具列的 GUID 和 ID。 要向工具列添加按鈕,將其父項設置為工具列上的組。

|工具列|ID|
|-------------|--------|
|標準|IDM_VS_TOOL_STANDARD|
|組建|IDM_VS_TOOL_BUILD|
|文字編輯器|IDM_VS_TOOL_TEXTEDITOR|
|偵錯|吉德VS調試組:IDM_DEBUG_TOOLBAR|
|除錯位置|吉德VS調試組:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>專用工具列
 這些工具列由 Visual Studio IDE 定義,但它們提供專用功能,不承載命令組。

|工具列|ID|
|-------------|--------|
|Add 命令|IDM_VS_TOOL_ADDCOMMAND|
|未定義|IDM_VS_TOOL_UNDEFINED|
|XML 結構描述|IDM_VS_TOOL_SCHEMA|
|XML 資料|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>IDE 工具列上的群組
 要向標準工具列添加按鈕,將以下組之一設置為其父組。 組按父工具列排序。

### <a name="standard-toolbar-groups"></a>標準工具列群組

|名稱|ID|
|----------|--------|
|儲存/開啟|IDG_VS_TOOLSB_SAVEOPEN|
|剪下/複製|IDG_VS_TOOLSB_CUTCOPY|
|復原/取消復原|IDG_VS_TOOLSB_UNDOREDO|
|執行/產生|IDG_VS_TOOLSB_RUNBUILD|
|搜尋|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|新視窗|IDG_VS_TOOLSB_NEWWINDOWS|
|載入/儲存|IDG_VS_WINDOWUI_LOADSAVE|
|量測計|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>建置工具列群組

|名稱|ID|
|----------|--------|
|產生欄|IDG_VS_BUILDBAR|
|取消|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>文字編輯器工具列群組

|名稱|ID|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Indent|IDG_VS_EDITTOOLBAR_INDENT|
|註解|IDG_VS_EDITTOOLBAR_COMMENT|
|書籤|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>除錯工具列群組

|名稱|ID|
|----------|--------|
|執行|IDM_DEBUG_TOOLBAR|
|逐步執行|IDG_DEBUG_TOOLBAR_STEPPING|
|監看式|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>除錯位置工具列群組

|名稱|ID|
|----------|--------|
|除錯位置|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>工作視窗工具列
 工具列可以直接出現在 IDE 或工具視窗中(如**解決方案資源管理員**)。 由於工具視窗未在 *.vsct*檔中定義,因此工具視窗工具列沒有定義的父控件。 相反,它們被放置在代碼中。 下表顯示了 IDE 中工具視窗中顯示的工具列及其包含的命令組。

> [!NOTE]
> 工具列和組使用 GUID `guidSHLMainMenu`,除非使用 GUID:ID 語法另有說明。 如果為工具列指定 GUID,它也適用於從該工具列下降的組。

|工具視窗|工具列|群組|
|-----------------|-------------|------------|
|方案總管|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.5|
|Server Explorer|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|屬性|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|類別檢視|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|類別檢視|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|物件瀏覽器|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|物件瀏覽器|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Output|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|尋找和取代|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|尋找結果 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|尋找結果 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|程式碼片段|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|書籤|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|工作清單|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|使用者工作|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|錯誤清單|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|呼叫瀏覽器|IDM_VS_TOOL_CALLBROWSER1.16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|中斷點|吉德VS調試組:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|反組譯碼|吉德VS調試組:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|記憶體 1-4|吉德VS調試組:IDM_MEMORY_WINDOW_TOOLBAR1...4|IDG_MEMORY_EXPRESSION1.4<br /><br /> IDG_MEMORY_COLUMNS1.4|
|處理序|吉德VS調試組:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRLIDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>另請參閱
- [將選單控制器加入工具列](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [加入工具視窗加入工具列](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Visual Studio 選單的 GUID 和 IT](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
