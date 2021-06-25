---
title: Visual Studio 功能表的 Guid 和識別碼 |Microsoft Docs
description: 在 Visual Studio 整合式開發環境 (IDE) 所包含的 Visual Studio] 功能表列上，查看功能表和群組的 GUID 和識別碼值清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bceee5fce8a77ad5169020bd3d21896bdbc71443
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898067"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Visual Studio 功能表的 Guid 和識別碼
本文列舉 Visual Studio 功能表列上功能表和群組的 GUID 和識別碼值。 這些值會定義在 *.vsct* 檔案中，這些檔案會安裝為 Visual Studio SDK 的一部分。 如需詳細資訊，請參閱 [IDE 定義的命令、功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

 如需如何使用整合式開發環境 (IDE) *.vsct* 檔中所定義之物件的詳細資訊，請參閱 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

 Visual Studio 功能表列上的功能表和群組會使用 GUID `guidSHLMainMenu` 。 功能表列本身具有的識別碼 `IDM_VS_TOOL_MAINMENU` 。

## <a name="groups-on-the-visual-studio-menu-bar"></a>Visual Studio 功能表列上的群組
 若要將功能表新增至功能表列，請將其中一個群組設定為其父項。

|群組|識別碼|
|-----------|--------|
|檔案/編輯/查看|IDG_VS_MM_FILEEDITVIEW|
|重構|IDG_VS_MM_REFACTORING：|
|Project|IDG_VS_MM_PROJECT|
|組建|IDG_VS_MM_BUILDDEBUGRUN|
|格式/工具|IDG_VS_MM_TOOLSADDINS|
|視窗/說明/群體|IDG_VS_MM_WINDOWHELP|
|增益集|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Visual Studio 功能表列上的功能表
 若要將群組新增至現有的 Visual Studio 功能表，請將下列其中一個功能表設定為其父代。 子功能表未包含在此清單中。

|功能表|識別碼|
|----------|--------|
|檔案|IDM_VS_MENU_FILE|
|編輯|IDM_VS_MENU_EDIT|
|檢視|IDM_VS_MENU_VIEW|
|重構|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|組建|IDM_VS_MENU_BUILD|
|格式|IDM_VS_MENU_FORMAT|
|工具|IDM_VS_MENU_TOOLS|
|延伸模組|IDM_VS_MENU_EXTENSIONS|
|時間範圍|IDM_VS_MENU_WINDOW|
|增益集|IDM_VS_MENU_ADDINS|
|社群|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Visual Studio 功能表上的群組
 下列清單顯示直接從 Visual Studio 功能表列上的功能表中下降的群組。 將命令新增至 Visual Studio 功能表的最快方式，就是將其中一個群組設定為父系。 從子功能表繼承的群組不會出現在此區段中。

### <a name="file-menu-groups"></a>檔案功能表群組

|群組|識別碼|
|-----------|--------|
|新增/開啟|IDG_VS_FILE_FILE|
|加|IDG_VS_FILE_ADD|
|解決方法|IDG_VS_FILE_SOLUTION|
|其他|IDG_VS_FILE_MISC|
|儲存|IDG_VS_FILE_SAVE|
|重新命名|IDG_VS_FILE_RENAME|
|瀏覽器|IDG_VS_FILE_BROWSER|
|列印|IDG_VS_FILE_PRINT|
|最近使用的|IDG_VS_FILE_MRU|
|移動|IDG_VS_FILE_MOVE|
|結束|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>編輯功能表群組

|群組|識別碼|
|-----------|--------|
|復原/取消復原|IDG_VS_EDIT_UNDOREDO|
|剪下/複製/貼上|IDG_VS_EDIT_CUTCOPY|
|選取|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|物件|IDG_VS_EDIT_OBJECTS|
|OLE 動詞|IDG_VS_EDIT_OLEVERBS|
|命令妥善|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>重構功能表群組

|群組|識別碼|
|-----------|--------|
|通用|IDG_REFACTORING_COMMON|
|進階|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>視圖功能表群組

|群組|識別碼|
|-----------|--------|
|表單程式碼|IDG_VS_VIEW_FORMCODE|
|瀏覽器|IDG_VS_VIEW_BROWSER|
|定義視圖|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|架構設計視窗|IDG_VS_VIEW_ARCH_WINDOWS|
|組織視窗|IDG_VS_VIEW_ORG_WINDOWS|
|程式碼瀏覽器|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|開發 Windows|IDG_VS_VIEW_DEV_WINDOWS|
|工具列|IDG_VS_VIEW_TOOLBARS|
|符號|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navigate|IDG_VS_VIEW_NAVIGATE|
|小型導覽|IDG_VS_VIEW_SMALLNAVIGATE|
|物件瀏覽器|IDG_VS_VIEW_OBJBRWSR|
|命令妥善|IDG_VS_VIEW_COMMANDWELL|
|屬性頁|IDG_VS_VIEW_PROPPAGES|
|重新整理|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>專案功能表群組

|群組|識別碼|
|-----------|--------|
|其他新增|IDG_VS_PROJ_MISCADD|
|加|IDG_VS_PROJ_ADD|
|資料夾|IDG_VS_PROJ_FOLDER|
|Unload/重載|IDG_VS_PROJ_UNLOADRELOAD|
|參考|IDG_VS_PROJ_REFERENCE|
|選項|IDG_VS_PROJ_OPTIONS|
|設定|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>組建功能表群組

|群組|識別碼|
|-----------|--------|
|解決方法|IDG_VS_BUILD_SOLUTION|
|選取|IDG_VS_BUILD_SELECTION|
|特性指引最佳化|IDG_VS_PGO_SELECTION|
|其他|IDG_VS_BUILD_MISC|
|取消|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>工具功能表群組

|群組|識別碼|
|-----------|--------|
|命令列|IDG_VS_TOOLS_CMDLINE|
|程式碼片段|IDG_VS_TOOLS_SNIPPETS|
|物件子集|IDG_VS_TOOLS_OBJSUBSET|
|選項|IDG_VS_TOOLS_OPTIONS|
|其他2|IDG_VS_TOOLS_OTHER2|
|外部工具|IDG_VS_TOOLS_EXT_TOOLS|
|外部自訂|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>視窗功能表群組

|群組|識別碼|
|-----------|--------|
|新增|IDG_VS_WINDOW_NEW|
|停駐/關閉|IDG_VS_DOCKCLOSE|
|停駐/隱藏|IDG_VS_DOCKHIDE|
|排列|IDG_VS_WINDOW_ARRANGE|
|導覽|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>說明功能表群組

|群組|識別碼|
|-----------|--------|
|範例|IDG_VS_HELP_SAMPLES|
|支援|IDG_VS_HELP_SUPPORT|
|關於|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Visual Studio 功能表的子功能表
 下列階層顯示與 Visual Studio 功能表列上的功能表相關聯的子功能表。 因為只有一個群組可以有一個功能表做為其父系，所以每個子功能表都必須從功能表上的群組繼承，而不是直接從功能表中。 如需功能表、群組和子功能表之間關聯性的詳細資訊，請參閱 [在功能表中加入子功能表](../../extensibility/adding-a-submenu-to-a-menu.md)。

> [!NOTE]
> Visual Studio 功能表列上的功能表名稱不會個別顯示在此階層中，因為它們可以從 IDE 中群組的命名慣例推斷，如下所示： *IDG_VS_ \<Menu Name\> _ \<Group Name\>*。

|父群組|子|子群組|
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
|||IDG_VS_WNDO_OTRWNDWS1 .。。6|
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
- [Visual Studio 工具列的 Guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Visual Studio 命令的 Guid 和識別碼](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio 命令表格 (. .vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
