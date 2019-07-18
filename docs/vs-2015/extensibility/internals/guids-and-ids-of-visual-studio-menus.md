---
title: 功能表的 Guid 和 Id |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d10549867c355018e301afa14cf2ba3a8f113e4d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436299"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Visual Studio 功能表的 GUID 和識別碼
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題列舉的 GUID 和 ID 值的功能表和 Visual Studio 功能表列上的群組。 在安裝 Visual Studio SDK 的一部分的.vsct 檔案中定義這些值。 如需詳細資訊，請參閱 < [IDE-Defined 命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。

 如需如何使用.vsct 檔案中定義的整合式的開發環境 (IDE) 物件的詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。

 功能表和 Visual Studio 功能表列上的群組會使用 GUID `guidSHLMainMenu`。 在功能表列本身的 ID 為`IDM_VS_TOOL_MAINMENU`。

## <a name="groups-on-the-visual-studio-menu-bar"></a>在 Visual Studio 功能表列上的群組
 若要加入功能表的功能表列中，設定其中一個群組作為其父代。

|群組|識別碼|
|-----------|--------|
|檔案/編輯/檢視表|IDG_VS_MM_FILEEDITVIEW|
|重構|IDG_VS_MM_REFACTORING:|
|專案|IDG_VS_MM_PROJECT|
|組建|IDG_VS_MM_BUILDDEBUGRUN|
|格式/工具|IDG_VS_MM_TOOLSADDINS|
|視窗/說明/社群|IDG_VS_MM_WINDOWHELP|
|增益集|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>在 Visual Studio 功能表列上的功能表
 若要將群組新增至現有的 Visual Studio 功能表中，設定下列功能表的其中一個做為其父系。 這份清單中不包含子功能表。

|功能表|識別碼|
|----------|--------|
|檔案|IDM_VS_MENU_FILE|
|編輯|IDM_VS_MENU_EDIT|
|檢視|IDM_VS_MENU_VIEW|
|重構|IDM_VS_MENU_REFACTORING|
|專案|IDM_VS_MENU_PROJECT|
|組建|IDM_VS_MENU_BUILD|
|格式|IDM_VS_MENU_FORMAT|
|工具|IDM_VS_MENU_TOOLS|
|視窗|IDM_VS_MENU_WINDOW|
|增益集|IDM_VS_MENU_ADDINS|
|社群|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>在 Visual Studio 功能表上的群組
 下列清單會顯示在 Visual Studio 功能表列直接從功能表下降的群組。 將命令新增至 Visual Studio 功能表的最快方式是其中一個群組設定為父代。 在本節中看不到從子功能表下降的群組。

### <a name="file-menu-groups"></a>檔案功能表群組

|群組|識別碼|
|-----------|--------|
|開啟新 /|IDG_VS_FILE_FILE|
|新增|IDG_VS_FILE_ADD|
|方案|IDG_VS_FILE_SOLUTION|
|其他|IDG_VS_FILE_MISC|
|儲存|IDG_VS_FILE_SAVE|
|重新命名|IDG_VS_FILE_RENAME|
|瀏覽器|IDG_VS_FILE_BROWSER|
|的|IDG_VS_FILE_PRINT|
|最常使用|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|結束|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>編輯功能表群組

|群組|識別碼|
|-----------|--------|
|復原/取消復原|IDG_VS_EDIT_UNDOREDO|
|剪下/複製/貼上|IDG_VS_EDIT_CUTCOPY|
|Select|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|物件|IDG_VS_EDIT_OBJECTS|
|OLE 指令動詞|IDG_VS_EDIT_OLEVERBS|
|命令的格式|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>重構的功能表群組

|群組|識別碼|
|-----------|--------|
|通用|IDG_REFACTORING_COMMON|
|進階|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>檢視功能表群組

|群組|識別碼|
|-----------|--------|
|表單程式碼|IDG_VS_VIEW_FORMCODE|
|瀏覽器|IDG_VS_VIEW_BROWSER|
|定義檢視|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|架構設計人員的 Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|組織的 Windows|IDG_VS_VIEW_ORG_WINDOWS|
|程式碼的瀏覽器|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|開發 Windows|IDG_VS_VIEW_DEV_WINDOWS|
|工具列|IDG_VS_VIEW_TOOLBARS|
|符號|IDG_VS_VIEW_SYMBOLNAVIGATE|
|瀏覽|IDG_VS_VIEW_NAVIGATE|
|小型瀏覽|IDG_VS_VIEW_SMALLNAVIGATE|
|物件瀏覽器|IDG_VS_VIEW_OBJBRWSR|
|命令的格式|IDG_VS_VIEW_COMMANDWELL|
|屬性頁|IDG_VS_VIEW_PROPPAGES|
|重新整理|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>專案功能表群組

|群組|識別碼|
|-----------|--------|
|其他新增|IDG_VS_PROJ_MISCADD|
|新增|IDG_VS_PROJ_ADD|
|資料夾|IDG_VS_PROJ_FOLDER|
|卸載/重新載入|IDG_VS_PROJ_UNLOADRELOAD|
|參考資料|IDG_VS_PROJ_REFERENCE|
|選項|IDG_VS_PROJ_OPTIONS|
|設定|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>建置功能表群組

|群組|識別碼|
|-----------|--------|
|方案|IDG_VS_BUILD_SOLUTION|
|選取|IDG_VS_BUILD_SELECTION|
|特性指引最佳化|IDG_VS_PGO_SELECTION|
|其他|IDG_VS_BUILD_MISC|
|取消|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>工具功能表群組

|群組|識別碼|
|-----------|--------|
|命令列|IDG_VS_TOOLS_CMDLINE|
|程式碼片段|IDG_VS_TOOLS_SNIPPETS|
|物件的子集|IDG_VS_TOOLS_OBJSUBSET|
|選項|IDG_VS_TOOLS_OPTIONS|
|另外 2 個|IDG_VS_TOOLS_OTHER2|
|外部工具|IDG_VS_TOOLS_EXT_TOOLS|
|外部的自訂項目|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>視窗功能表群組

|群組|識別碼|
|-----------|--------|
|新增|IDG_VS_WINDOW_NEW|
|停駐] / [關閉|IDG_VS_DOCKCLOSE|
|停駐/隱藏|IDG_VS_DOCKHIDE|
|排列|IDG_VS_WINDOW_ARRANGE|
|巡覽|IDG_VS_WINDOW_NAVIGATION|
|清單|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>說明功能表群組

|群組|識別碼|
|-----------|--------|
|範例|IDG_VS_HELP_SAMPLES|
|支援|IDG_VS_HELP_SUPPORT|
|關於|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Visual Studio 功能表的子功能表
 下列階層會顯示在 Visual Studio 功能表列上的功能表與相關聯的子功能表。 只有一組可以有一個功能表做為其父系，因為每一個子功能表必須下降從群組在功能表上，而不是直接從功能表。 如需功能表、 群組和子功能表之間的關聯性的詳細資訊，請參閱[子功能表加入功能表](../../extensibility/adding-a-submenu-to-a-menu.md)。

> [!NOTE]
> Visual Studio 功能表列上的功能表名稱不會個別顯示此階層中上，因為他們可以從推斷在 IDE 中，群組的命名慣例，如下所示：IDG_VS_*功能表名稱*_*群組名稱*。

|父群組|子功能表|子群組|
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
|||IDG_VS_WNDO_OTRWNDWS1…6|
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
 [Visual Studio 工具列的 Guid 和 Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md) [Visual Studio 命令的 Guid 和 Id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md) [Visual Studio 命令資料表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
