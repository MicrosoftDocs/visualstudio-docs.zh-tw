---
title: Visual Studio 選單的 GUID 和 IT |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a656d5cb9a126a9dc3988d70a290fceb3e56439e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708235"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Visual Studio 選單的 GUID 和 IT
本文在 Visual Studio 功能表欄上枚舉功能表和組的 GUID 和 ID 值。 這些值在作為可視化工作室 SDK 的一部分安裝的 *.vsct*檔中定義。 有關詳細資訊,請參閱[IDE 定義的指令、選單和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

 有關如何使用*在 .vsct*檔中定義的整合式開發環境 (IDE) 物件的詳細資訊,請參閱[延伸選單和指令](../../extensibility/extending-menus-and-commands.md)。

 Visual Studio 選單列上的選單和群組使用`guidSHLMainMenu`GUID 。 選單列本身的 ID`IDM_VS_TOOL_MAINMENU`為 。

## <a name="groups-on-the-visual-studio-menu-bar"></a>視覺工作室選單欄上的群組
 要向菜單欄添加功能表,將其中一個組設置為其父組。

|群組|ID|
|-----------|--------|
|檔案/編輯/檢視|IDG_VS_MM_FILEEDITVIEW|
|Refactoring|IDG_VS_MM_REFACTORING:|
|隨附此逐步解說的專案|IDG_VS_MM_PROJECT|
|組建|IDG_VS_MM_BUILDDEBUGRUN|
|格式/工具|IDG_VS_MM_TOOLSADDINS|
|視窗/幫助/社區|IDG_VS_MM_WINDOWHELP|
|增益集|IDG_VS_MM_MACROS|
|全螢幕列|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>視覺工作室選單欄上的功能表
 要將組添加到現有 Visual Studio 功能表,將以下功能表之一設置為其父功能表之一。 子功能表不包括在此清單中。

|功能表|ID|
|----------|--------|
|檔案|IDM_VS_MENU_FILE|
|編輯|IDM_VS_MENU_EDIT|
|檢視|IDM_VS_MENU_VIEW|
|重構|IDM_VS_MENU_REFACTORING|
|隨附此逐步解說的專案|IDM_VS_MENU_PROJECT|
|組建|IDM_VS_MENU_BUILD|
|[格式]|IDM_VS_MENU_FORMAT|
|工具|IDM_VS_MENU_TOOLS|
|延伸模組|IDM_VS_MENU_EXTENSIONS|
|時間範圍|IDM_VS_MENU_WINDOW|
|增益集|IDM_VS_MENU_ADDINS|
|社群|IDM_VS_MENU_COMMUNITY|
|説明|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>視覺工作室選單上的群組
 以下清單顯示直接從 Visual Studio 功能表列上的功能表下降的組。 向 Visual Studio 功能表添加命令的最快方法是將這些組之一設置為父組。 從子功能表下降的組不會出現在此部分中。

### <a name="file-menu-groups"></a>檔案選單組

|群組|ID|
|-----------|--------|
|新增/開啟|IDG_VS_FILE_FILE|
|加|IDG_VS_FILE_ADD|
|解決方法|IDG_VS_FILE_SOLUTION|
|其他|IDG_VS_FILE_MISC|
|儲存|IDG_VS_FILE_SAVE|
|重新命名|IDG_VS_FILE_RENAME|
|瀏覽器|IDG_VS_FILE_BROWSER|
|列印|IDG_VS_FILE_PRINT|
|最近使用|IDG_VS_FILE_MRU|
|移動|IDG_VS_FILE_MOVE|
|Exit|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>編輯選單群組

|群組|ID|
|-----------|--------|
|復原/取消復原|IDG_VS_EDIT_UNDOREDO|
|剪下/複製/貼上|IDG_VS_EDIT_CUTCOPY|
|選取|IDG_VS_EDIT_SELECT|
|跳到|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|物件|IDG_VS_EDIT_OBJECTS|
|OLE 動詞|IDG_VS_EDIT_OLEVERBS|
|命令井|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>重構選單組

|群組|ID|
|-----------|--------|
|通用|IDG_REFACTORING_COMMON|
|進階|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>檢視選單群組

|群組|ID|
|-----------|--------|
|表單代碼|IDG_VS_VIEW_FORMCODE|
|瀏覽器|IDG_VS_VIEW_BROWSER|
|定義檢視|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|架構視窗|IDG_VS_VIEW_ARCH_WINDOWS|
|組織視窗|IDG_VS_VIEW_ORG_WINDOWS|
|程式碼瀏覽器|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|開發視窗|IDG_VS_VIEW_DEV_WINDOWS|
|工具列|IDG_VS_VIEW_TOOLBARS|
|Symbols|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navigate|IDG_VS_VIEW_NAVIGATE|
|小型導航|IDG_VS_VIEW_SMALLNAVIGATE|
|物件瀏覽器|IDG_VS_VIEW_OBJBRWSR|
|命令井|IDG_VS_VIEW_COMMANDWELL|
|屬性頁|IDG_VS_VIEW_PROPPAGES|
|Refresh|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>專案選單組

|群組|ID|
|-----------|--------|
|雜項新增|IDG_VS_PROJ_MISCADD|
|加|IDG_VS_PROJ_ADD|
|資料夾|IDG_VS_PROJ_FOLDER|
|卸載/重新載入|IDG_VS_PROJ_UNLOADRELOAD|
|參考|IDG_VS_PROJ_REFERENCE|
|選項。|IDG_VS_PROJ_OPTIONS|
|設定|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>產生選單組

|群組|ID|
|-----------|--------|
|解決方法|IDG_VS_BUILD_SOLUTION|
|選取項目|IDG_VS_BUILD_SELECTION|
|特性指引最佳化|IDG_VS_PGO_SELECTION|
|其他|IDG_VS_BUILD_MISC|
|取消|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>工具選單組

|群組|ID|
|-----------|--------|
|命令列|IDG_VS_TOOLS_CMDLINE|
|程式碼片段|IDG_VS_TOOLS_SNIPPETS|
|物件子集|IDG_VS_TOOLS_OBJSUBSET|
|選項。|IDG_VS_TOOLS_OPTIONS|
|其他 2|IDG_VS_TOOLS_OTHER2|
|外部工具|IDG_VS_TOOLS_EXT_TOOLS|
|外部自訂|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>視窗選單群組

|群組|ID|
|-----------|--------|
|新增|IDG_VS_WINDOW_NEW|
|塢站/關閉|IDG_VS_DOCKCLOSE|
|碼頭/隱藏|IDG_VS_DOCKHIDE|
|排列|IDG_VS_WINDOW_ARRANGE|
|導覽|IDG_VS_WINDOW_NAVIGATION|
|清單|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>說明選單組

|群組|ID|
|-----------|--------|
|範例|IDG_VS_HELP_SAMPLES|
|支援|IDG_VS_HELP_SUPPORT|
|關於|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>視覺化工作室選單的子選單
 以下層次結構顯示與 Visual Studio 功能表列上的功能表關聯的子功能表。 由於只有組可以有一個功能表作為其父功能表,因此每個子菜單都必須從菜單上的組下降,而不是直接從菜單中下來。 有關選單、組和子選單之間的關係的詳細資訊,請參閱[向選單添加子選單](../../extensibility/adding-a-submenu-to-a-menu.md)。

> [!NOTE]
> Visual Studio 選單列上的選單名稱不單獨顯示在此層次結構中,因為它們可以從 IDE 中組的命名約定推斷出來,如下所示 *:IDG_VS_\<選單\>名稱\<= 組名稱\>*。

|父群組|子|子組|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1...6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>另請參閱
- [Visual Studio 工具列的 GUID 和 IT](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Visual Studio 指令的 GUID 和 IT](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [視覺化工作室指令表 (.vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
