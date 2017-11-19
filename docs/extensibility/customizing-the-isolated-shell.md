---
redirect_url: shell/customizing-the-isolated-shell
title: "自訂 Isolated 的 Shell |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35aab40dbacd814dcec281ff1f3dd529b29d4424
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-isolated-shell"></a>自訂 Isolated 的 Shell
藉由變更 Visual Studio 使用者介面的不同層面，以及限制的命令和特殊應用程式中包含的功能，您可以自訂 Visual Studio isolated shell 應用程式。  
  
## <a name="using-the-applicationpkgdef-file"></a>使用 Application.pkgdef 檔案  
 獨立的 shell 範本解決方案包含*SolutionName*。Application.pkgdef 檔案可讓您修改下列功能：  
  
##### <a name="the-application-title"></a>應用程式標題  
 您可以自訂應用程式標題，這是藉由變更的值:"AppName"中的資料列會顯示應用程式的標題列中的名稱*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
 如果您不想要顯示目前已載入專案的應用程式標題，變更 「 showhierarchyrootintitle 設 」 資料列中的值*SolutionName*。將檔案從 dword: 00000001 Application.pkgdef 為 dword: 00000000。  
  
##### <a name="the-application-icon"></a>應用程式圖示  
 您可以自訂應用程式圖示，也就是由應用程式名稱的應用程式標題列中顯示的圖示。 複製的圖示目錄不同的圖示。 在**方案總管 中**，將圖示加入至 資源檔案 資料夾。 然後開啟 VSShellStub.rc 檔案，並以新圖示的名稱取代 IDI_STUBPROGRAM 的值。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-command-line-logo"></a>命令列標誌  
 您可以自訂的命令列的標誌，亦即當從命令列啟動應用程式中的"CommandLineLogo 「 資料列的值變更時所顯示的文字*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>使用者檔案子資料夾名稱  
 您可以變更您的應用程式中的"UserFilesSubFolderName 「 資料列的值變更維護使用者檔案的資料夾名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>在 [新增專案] 對話方塊方案樹狀節點的標題  
 您可以自訂的新專案 對話方塊中的方案節點標題中的"NewProjDlgSlnTreeNodeTitle 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>已安裝的範本中的標頭新增專案 對話方塊  
 您可以變更已安裝的範本中的標頭新增專案 對話方塊中的"NewProjDlgInstalledTemplatesHdr 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>是否要依預設會隱藏其他檔案  
 您可以指定是否要依預設會隱藏其他檔案中的"HideMiscellaneousFilesByDefault 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要隱藏其他檔案，將值設定`dword:00000001`，若要顯示的檔案，將值設定`dword:00000000`。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>是否要停用 [輸出] 視窗  
 您可以指定是否要停用應用程式中的 [輸出] 視窗中的"DisableOutputWindow 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要停用 [輸出] 視窗，請將值`dword:00000001`，若要顯示 [輸出] 視窗，將值設定`dword:00000000`。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>決定是否允許主視窗上的已卸除的檔案  
 您可以指定是否要允許應用程式中的主視窗上的已卸除的檔案中的"AllowsDroppedFilesOnMainWindow 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要允許卸除的檔案，將值`dword:00000001`，不允許卸除的檔案，將值設定`dword:00000000`。  
  
##### <a name="the-default-search-page"></a>預設的 [搜尋] 頁面  
 您可以自訂網頁瀏覽器上，這是開啟網頁瀏覽器視窗時，「 DefaultSearchPage 」 資料列中的值變更時所顯示的頁面*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-home-page"></a>預設的首頁  
 您可以自訂 [首頁] 頁面中的"DefaultHomePage 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>是否要隱藏解決方案概念  
 您可以指定是否要隱藏您的應用程式中的方案中的"HideSolutionConcept 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要隱藏解決方案，將值設定`dword:00000001`，若要顯示方案，將值設定`dword:00000000`。  
  
##### <a name="the-default-debug-engine"></a>預設的偵錯引擎  
 您可以變更您的應用程式使用中的"DefaultDebugEngine 「 資料列的值變更的偵錯引擎*SolutionName*。Application.pkgdef 檔案之 guid 的偵錯引擎。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>使用者選項檔副檔名  
 您可以變更您的應用程式中的"UserOptsFileExt 「 資料列的值變更維護使用者檔案的資料夾名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-solution-file-extension"></a>方案檔案的副檔名  
 您可以變更用於您的方案檔案中的"SolutionFileExt 「 資料列的值變更的延伸模組*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-user-files-folder-root"></a>預設使用者檔案資料夾根目錄  
 您也可以變更值中的"UserFilesSubFolderName 「 資料列的應用程式變更使用者檔案的根資料夾的名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-solution-file-creator-identifier"></a>方案檔案建立者識別碼  
 您可以變更用於您的方案檔案中的"SolutionFileCreatorIdentifier 「 資料列的值變更的識別項*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-projects-location"></a>預設專案位置  
 您可以變更預設專案位置的名稱中的"DefaultProjectsLocation 「 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-application-localization-package"></a>應用程式當地語系化套件  
 您可以變更用於您的應用程式中的"AppLocalizationPackage 「 資料列的值變更當地語系化套件*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>是否要顯示在階層根目錄的標題  
 您可以指定是否要顯示應用程式中的標題列中的階層根目錄中的"showhierarchyrootintitle 設 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要顯示在階層根目錄，請將值`dword:00000001`，若要隱藏在階層根目錄，將值設定`dword:00000000`。  
  
##### <a name="specifying-a-start-page"></a>指定起始頁  
 若要指定自訂的應用程式起始頁中*SolutionName*。Application.pkgdef 檔案設定為"DisableStartPage"值`dword:00000000`，然後在`[$RootKey$\StartPage\Default]`設.xaml 檔案的位置的 URI:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct 檔案中*SolutionName*UI 專案，註解"No_ShellPkg_startPageCommand"項目：  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 您必須新增的.xaml 檔案，以及您需要為的圖形檔案*SolutionName*專案。 這些檔案實際上必須複製到*SolutionName*專案目錄中，不會加入從其他的目錄。  
  
 上的所有檔案，設定**項目類型**屬性**隔離 Shell 檔案**順序檔案的檔案複製到*$RootFolder$*目錄。 (若要設定**項目類型**屬性，以滑鼠右鍵按一下檔案，然後選取**屬性**。 這個屬性可以在底下找到**組態屬性**，**一般**。)  
  
 如需有關自訂起始頁的詳細資訊，請參閱[自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>使用在 isolated shell 的其他項目  
 您可以使用其他檔案和獨立的 shell 解決方案範本，若要進一步自訂您的應用程式中包含的專案。  
  
##### <a name="enabledisable-visual-studio-packages"></a>啟用/停用 Visual Studio 套件  
 *SolutionName*.pkgundef 檔可讓您排除特定的封裝，以停用特定類型的 Visual Studio 功能。 例如，下列程式碼行：  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 從集合中顯示的專案範本中移除其他檔案專案**新專案**對話方塊。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="enabledisable-menu-commands"></a>啟用/停用功能表命令  
 *SolutionName*UI.vsct 檔案包含的所有功能表可用的命令在 isolated shell 標記為註解清單。 若要停用指定的命令，請取消註解的對應資料列。 例如，若要停用視窗/分隔註解，請取消註解`<Define name="No_SplitCommand"/>`資料列。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>用在啟動顯示畫面點陣圖  
 您可以自訂在啟動顯示畫面上，即會顯示應用程式啟動時，值"SplashScreenBitmap 「 資料列中的變更視窗用點陣圖*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-helpabout-window"></a>[說明] / [關於]  
 獨立的 shell 範本中沒有個別的專案，您可以使用以自訂 說明/關於您的應用程式的方塊。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。