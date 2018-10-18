---
title: 自訂 Isolated 的 Shell |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3804ded3106c68c1298063b38fb3d384685a18a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175548"
---
# <a name="customizing-the-isolated-shell"></a>自訂 Isolated 的 Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

藉由變更 Visual Studio 使用者介面的不同層面，以及限制的命令和特製化的應用程式包含的功能，您可以自訂您的 Visual Studio isolated shell 應用程式。  
  
## <a name="using-the-applicationpkgdef-file"></a>使用 Application.pkgdef 檔案  
 獨立模式的 shell 範本方案包括*SolutionName*。Application.pkgdef 檔案，可讓您修改下列功能：  
  
##### <a name="the-application-title"></a>應用程式標題  
 您可以自訂應用程式標題，即會顯示在應用程式的標題列，藉由變更:"AppName"中資料列的值的名稱*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
 如果您不想要顯示目前已載入專案的應用程式標題，變更"ShowHierarchyRootInTitle 」 資料列中的值*SolutionName*。Application.pkgdef 檔從 dword: 00000001 dword:00000000。  
  
##### <a name="the-application-icon"></a>應用程式圖示  
 您可以自訂應用程式圖示，它是由應用程式名稱的應用程式標題列中顯示的圖示。 將不同的圖示複製到圖示目錄中。 在 [**方案總管] 中**，將圖示新增至資源檔的資料夾。 然後開啟 VSShellStub.rc 檔案，並使用 [新增] 圖示的名稱取代 IDI_STUBPROGRAM 值。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-command-line-logo"></a>命令列的標誌  
 您可以自訂的命令列的標誌，也就是從命令列中，啟動應用程式中的"CommandLineLogo 」 資料列的值變更時，會出現的文字*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>使用者名稱的檔案子資料夾  
 您可以變更您的應用程式會維護使用者檔案中的"UserFilesSubFolderName 」 資料列的值變更的資料夾名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>在 [新增專案] 對話方塊中的方案樹狀目錄節點的標題  
 您可以自訂在 [新增專案] 對話方塊的 [方案] 節點的標題中的"NewProjDlgSlnTreeNodeTitle 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>已安裝的範本中的標頭新增專案 對話方塊  
 您可以變更已安裝的範本中的標頭新增專案 對話方塊中的"NewProjDlgInstalledTemplatesHdr 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>指出是否要依預設隱藏其他檔案  
 您可以指定是否要依預設隱藏其他檔案中的"HideMiscellaneousFilesByDefault 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要隱藏其他檔案，將值設定`dword:00000001`，並顯示的檔案，將值設定`dword:00000000`。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>指出是否要停用 [輸出] 視窗  
 您可以指定是否要停用應用程式中的 [輸出] 視窗中的"DisableOutputWindow 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要停用 [輸出] 視窗，請將值`dword:00000001`，以顯示 [輸出] 視窗，將值設定`dword:00000000`。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>指出是否要允許在主視窗的已卸除的檔案  
 您可以指定是否要允許您的應用程式中的主視窗上已置放的檔案中的"AllowsDroppedFilesOnMainWindow 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要允許卸除的檔案，將值設定`dword:00000001`，並不允許卸除的檔案，將值設定`dword:00000000`。  
  
##### <a name="the-default-search-page"></a>預設的 [搜尋] 頁面  
 您可以自訂網頁瀏覽器上，也就是開啟網頁瀏覽器視窗時，「 DefaultSearchPage 」 資料列中的值變更時，會顯示的頁面*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-home-page"></a>預設的首頁  
 您可以自訂 [首頁] 頁面中的"DefaultHomePage 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>指出是否要隱藏解決方案概念  
 您可以指定是否要隱藏您的應用程式中的方案中的"HideSolutionConcept 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要隱藏解決方案，將值設定`dword:00000001`，並顯示方案，請將值設定`dword:00000000`。  
  
##### <a name="the-default-debug-engine"></a>預設的偵錯引擎  
 您可以變更應用程式中的"DefaultDebugEngine 」 資料列的值變更所使用的偵錯引擎*SolutionName*。Application.pkgdef 檔偵錯引擎的 GUID。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>使用者選項檔的副檔名  
 您可以變更您的應用程式會維護使用者檔案中的"UserOptsFileExt 」 資料列的值變更的資料夾名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-solution-file-extension"></a>解決方案檔案的副檔名  
 您可以變更用於將方案檔中的"SolutionFileExt 」 資料列的值變更的延伸模組*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-user-files-folder-root"></a>預設使用者檔案的資料夾根目錄  
 您也可以變更 「 UserFilesSubFolderName 」 資料列中的值為您的應用程式變更的使用者檔案的根資料夾名稱*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-solution-file-creator-identifier"></a>解決方案檔案建立者識別碼  
 您可以變更您的方案檔中的"SolutionFileCreatorIdentifier 」 資料列的值變更所使用的識別碼*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-default-projects-location"></a>預設專案位置  
 您可以變更預設專案位置的名稱變更的值中的"DefaultProjectsLocation 」 資料列*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="the-application-localization-package"></a>應用程式當地語系化套件  
 您可以變更用於您的應用程式中的"AppLocalizationPackage 」 資料列的值變更的當地語系化套件*SolutionName*。Application.pkgdef 檔案。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>指出是否要顯示在階層根目錄的標題  
 您可以指定是否要顯示在階層根目錄中在您的應用程式的標題列中的"ShowHierarchyRootInTitle 」 資料列的值變更*SolutionName*。Application.pkgdef 檔案。 若要顯示在階層根目錄，將值設定`dword:00000001`，若要隱藏在階層根目錄，將值設定`dword:00000000`。  
  
##### <a name="specifying-a-start-page"></a>指定的起始頁  
 若要指定自訂的應用程式起始頁*SolutionName*。Application.pkgdef 檔案，將 「 DisableStartPage"值設為`dword:00000000`，然後在`[$RootKey$\StartPage\Default]`設.xaml 檔的位置的 URI:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct 檔案中*SolutionName*UI 專案，標記為註解"No_ShellPkg_startPageCommand 」 項目：  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 您必須新增的.xaml 檔案，以及您需要為任何圖形檔案*SolutionName*專案。 這些檔案必須實際複製到*SolutionName*專案目錄中，不會加入從其他的目錄。  
  
 在所有檔案，將**項目類型**屬性設**隔離 Shell 檔案**複製到檔案以便 *$RootFolder$* 目錄。 (若要設定**項目類型**屬性，以滑鼠右鍵按一下檔案，然後選取**屬性**。 這個屬性下找到**組態屬性**，**一般**。)  
  
 如需有關自訂起始頁的詳細資訊，請參閱 <<c0> [ 自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>使用 isolated shell 的其他項目  
 您可以使用其他檔案和包含在獨立模式的 shell 解決方案範本，以進一步自訂您的應用程式的專案。  
  
##### <a name="enabledisable-visual-studio-packages"></a>啟用/停用 Visual Studio 封裝  
 *SolutionName*.pkgundef 檔案可讓您排除特定的封裝來停用特定種類的 Visual Studio 功能。 例如，下列程式碼行：  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 從集合中顯示的專案範本中移除其他檔案專案**新的專案**對話方塊。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="enabledisable-menu-commands"></a>啟用/停用功能表命令  
 *SolutionName*UI.vsct 檔案包含所有的功能表命令的獨立模式 shell 可標記為註解清單。 若要停用指定的命令，請取消註解對應的資料列。 例如，若要停用分割視窗/註解，請取消註解`<Define name="No_SplitCommand"/>`資料列。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>使用在啟動顯示畫面的點陣圖  
 您可以自訂在啟動顯示畫面上，也就是啟動應用程式時，「 SplashScreenBitmap 」 資料列中的值變更時，會顯示視窗用點陣圖*SolutionName*。Application.pkgdef 檔案。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-helpabout-window"></a>「 說明/關於 視窗  
 在獨立模式的 shell 範本中沒有個別的專案，您可以使用自訂 [說明] / [關於] 對話方塊，您的應用程式。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。

