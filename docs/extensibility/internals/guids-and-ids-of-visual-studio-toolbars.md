---
title: Visual Studio 工具列的 Guid 和識別碼 |Microsoft Docs
description: 查看 Visual Studio 整合式開發環境 (IDE) 中包含的工具列和識別碼值的清單，以及它們所包含的群組。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b44cda401faa0d7e34bf9ce7579aa3cca026fa13
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480378"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Visual Studio 工具列的 Guid 和識別碼
本主題列舉 Visual Studio 整合式開發環境中包含的工具列 GUID 和識別碼值 (IDE) 以及它們所包含的群組。 這些值會定義在 *.vsct* 檔案中，這些檔案會安裝為 Visual Studio SDK 的一部分。 如需詳細資訊，請參閱 [IDE 定義的命令、功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

> [!NOTE]
> 許多可用來 Visual Studio 的工具列都不是由 Visual Studio 所定義，而且其 GUID 和識別碼值不是公用的。 本主題只會列出 Visual Studio *.vsct* 檔案中定義的工具列。

 如需如何使用 *.vsct* 檔中所定義之 IDE 物件的詳細資訊，請參閱 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

 Visual Studio IDE 所提供的預設工具列會使用 GUID `guidSHLMainMenu` ，但在其他情況下，則是使用語法來指定 `GUID:ID` 。

## <a name="ide-toolbars"></a>IDE 工具列
 下列是 Visual Studio IDE 所提供的工具列。 您可以在 [**工具**] 功能表的 [**工具列**] 子功能表上選取工具列，以顯示工具列。 工具視窗中的工具列不包含在此區段中。

 只有群組可以直接從工具列中進行。 若要加入群組，請將其父系設定為工具列的 GUID 和識別碼。 若要將按鈕加入至工具列，請將其父系設定為工具列上的群組。

|工具列|識別碼|
|-------------|--------|
|標準|IDM_VS_TOOL_STANDARD|
|組建|IDM_VS_TOOL_BUILD|
|文字編輯器|IDM_VS_TOOL_TEXTEDITOR|
|偵錯|guidVSDebugGroup： IDM_DEBUG_TOOLBAR|
|調試位置|guidVSDebugGroup： IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>特殊工具列
 這些工具列是由 Visual Studio IDE 所定義，但它們會提供特殊功能，而不會裝載命令群組。

|工具列|識別碼|
|-------------|--------|
|Add 命令|IDM_VS_TOOL_ADDCOMMAND|
|未定義|IDM_VS_TOOL_UNDEFINED|
|XML 結構描述|IDM_VS_TOOL_SCHEMA|
|XML 資料|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>IDE 工具列上的群組
 若要將按鈕加入至標準工具列，請將下列其中一個群組設定為其父代。 群組會依父工具列排序。

### <a name="standard-toolbar-groups"></a>標準工具列群組

|名稱|ID|
|----------|--------|
|儲存/開啟|IDG_VS_TOOLSB_SAVEOPEN|
|剪下/複製|IDG_VS_TOOLSB_CUTCOPY|
|復原/取消復原|IDG_VS_TOOLSB_UNDOREDO|
|執行/組建|IDG_VS_TOOLSB_RUNBUILD|
|搜尋|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|新視窗|IDG_VS_TOOLSB_NEWWINDOWS|
|載入/儲存|IDG_VS_WINDOWUI_LOADSAVE|
|量測計|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>組建工具列群組

|名稱|ID|
|----------|--------|
|組建列|IDG_VS_BUILDBAR|
|取消|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>文字編輯器工具列群組

|名稱|ID|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|縮排|IDG_VS_EDITTOOLBAR_INDENT|
|註解|IDG_VS_EDITTOOLBAR_COMMENT|
|書籤|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>調試工具列群組

|名稱|ID|
|----------|--------|
|執行|IDM_DEBUG_TOOLBAR|
|逐步執行|IDG_DEBUG_TOOLBAR_STEPPING|
|觀看|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>調試位置工具列群組

|名稱|ID|
|----------|--------|
|調試位置|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>工作視窗工具列
 您可以直接在 IDE 或工具視窗中（例如 **方案總管**）顯示工具列。 由於工具視窗並未定義于 *.vsct* 檔案中，因此工具視窗工具列並沒有定義的父代。 相反地，它們會置於程式碼中。 下表顯示在 IDE 中的工具視窗中顯示的工具列，以及它們所包含的命令群組。

> [!NOTE]
> `guidSHLMainMenu`除了使用 guid： ID 語法來指定以外，工具列和群組也會使用 guid。 當針對工具列指定 GUID 時，也會套用至從該工具列繼承的群組。

|工具視窗|工具列|群組|
|-----------------|-------------|------------|
|方案總管|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1。.5|
|Server Explorer|guid_SE_MenuGroup： IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|屬性|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|類別檢視|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|類別檢視|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|物件瀏覽器|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|物件瀏覽器|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|輸出|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|尋找和取代|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|尋找結果1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|尋找結果2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|程式碼片段|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|書籤|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|工作清單|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|使用者工作|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|錯誤清單|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|呼叫瀏覽器|IDM_VS_TOOL_CALLBROWSER1。16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|中斷點|guidVSDebugGroup： IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|反組譯碼|guidVSDebugGroup： IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|記憶體1-4|guidVSDebugGroup： IDM_MEMORY_WINDOW_TOOLBAR1 .。。億|IDG_MEMORY_EXPRESSION1。億<br /><br /> IDG_MEMORY_COLUMNS1。億|
|處理序|guidVSDebugGroup： IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>另請參閱
- [將功能表控制器新增至工具列](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [將工具列新增至工具視窗](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Visual Studio 功能表的 Guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
