---
title: 自訂隔離式 Shell |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555964"
---
# <a name="customizing-the-isolated-shell"></a>自訂獨立模式 Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由變更 Visual Studio 使用者介面的不同層面，以及限制特殊應用程式中包含的命令和功能，來自訂 Visual Studio 獨立模式 shell 應用程式。  
  
## <a name="using-the-applicationpkgdef-file"></a>使用 .pkgdef 檔案  
 獨立模式 shell 範本方案包含瞭解決 *方法。* 應用程式 .pkgdef 檔，可讓您修改下列功能：  
  
##### <a name="the-application-title"></a>應用程式標題  
 您可以藉由變更 *程式名稱中*"AppName" 資料列的值，自訂應用程式標題，也就是在應用程式標題列中顯示的名稱。.Pkgdef 檔案。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
 如果您不想讓應用程式標題顯示目前載入的專案，請在 [方案 *名稱*] 中變更 "ShowHierarchyRootInTitle" 資料列的值。從 dword：00000001到 dword：00000000的 .pkgdef 檔案。  
  
##### <a name="the-application-icon"></a>應用程式圖示  
 您可以自訂應用程式圖示，也就是應用程式名稱在應用程式標題列中顯示的圖示。 將不同的圖示複製到圖示目錄。 在 **方案總管**中，將圖示新增至 [資源檔] 資料夾。 然後開啟 VSShellStub .rc 檔，並以新圖示的名稱取代 IDI_STUBPROGRAM 的值。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-command-line-logo"></a>命令列標誌  
 您可以自訂命令列標誌，這是從命令列啟動應用程式時所顯示的文字，方法是變更程式碼中的 "CommandLineLogo" 資料列的 *值。*.Pkgdef 檔案。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>[使用者檔案] 子資料夾的名稱  
 您可以變更 [程式名稱] 中 "UserFilesSubFolderName" 資料列的值 *，以變更*應用程式針對使用者檔案所維護的資料夾名稱。.Pkgdef 檔案。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>[新增專案] 對話方塊中方案樹狀結構節點的標題  
 您可以在 [新增專案] 對話方塊中，藉由變更方案 *名稱*中的 "NewProjDlgSlnTreeNodeTitle" 資料列的值，自訂方案節點的標題。.Pkgdef 檔案。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>[新增專案] 對話方塊中的 [已安裝的範本] 標頭  
 您可以變更方案中 "NewProjDlgInstalledTemplatesHdr" 資料列的值，藉以 *變更 [新增*專案] 對話方塊中的 [已安裝的範本] 標頭。.Pkgdef 檔案。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>是否依預設隱藏其他檔案  
 您可以指定是否要在程式 *名稱*中變更 "HideMiscellaneousFilesByDefault" 資料列的值，以依預設隱藏其他檔案。.Pkgdef 檔案。 若要隱藏其他檔案、設定值 `dword:00000001` ，以及顯示檔案，請設定此值 `dword:00000000` 。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>是否要停用輸出視窗  
 您可以在 [程式 *名稱*] 中變更 "DisableOutputWindow" 資料列的值，以指定是否要停用應用程式中的輸出視窗。.Pkgdef 檔案。 若要停用 [輸出] 視窗，請設定值 `dword:00000001` ，並顯示 [輸出] 視窗，並設定值 `dword:00000000` 。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>是否允許在主視窗上放置已卸載的檔案  
 您可以藉由變更 [程式 *名稱*] 中 "AllowsDroppedFilesOnMainWindow" 資料列的值，指定是否允許在應用程式的主視窗上放置檔案。.Pkgdef 檔案。 若要允許捨棄的檔案、設定值 `dword:00000001` ，以及不允許卸載的檔案，請設定此值 `dword:00000000` 。  
  
##### <a name="the-default-search-page"></a>預設搜尋頁面  
 您可以自訂網頁瀏覽器頁面，也就是在開啟網頁瀏覽器視窗時所顯示的頁面，方法是變更程式 *名稱*中 "DefaultSearchPage" 資料列的值。.Pkgdef 檔案。  
  
##### <a name="the-default-home-page"></a>預設首頁  
 您可以在 [程式 *名稱*] 中變更 "DefaultHomePage" 資料列的值，以自訂首頁。.Pkgdef 檔案。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>是否要隱藏解決方案概念  
 您可以藉由變更程式 *名稱*中 "HideSolutionConcept" 資料列的值，指定是否要在應用程式中隱藏方案。.Pkgdef 檔案。 若要隱藏方案，請設定值 `dword:00000001` ，並顯示方案，並設定值 `dword:00000000` 。  
  
##### <a name="the-default-debug-engine"></a>預設的 debug 引擎  
 您可以變更程式 *名稱*中 "DefaultDebugEngine" 資料列的值，以變更應用程式所使用的 debug engine。.Pkgdef 檔案加入至您的偵錯工具的 GUID。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>使用者選項檔案的副檔名  
 您可以變更 [程式名稱] 中 "UserOptsFileExt" 資料列的值 *，以變更*應用程式針對使用者檔案所維護的資料夾名稱。.Pkgdef 檔案。  
  
##### <a name="the-solution-file-extension"></a>方案副檔名  
 您可以變更方案中 "SolutionFileExt" 資料列的值，藉以變更方案檔所使用的擴充 *功能。*.Pkgdef 檔案。  
  
##### <a name="the-default-user-files-folder-root"></a>預設使用者檔案資料夾根目錄  
 您可以藉由變更 *程式名稱中*"UserFilesSubFolderName" 資料列的值，變更應用程式使用者檔案的根資料夾名稱。.Pkgdef 檔案。  
  
##### <a name="the-solution-file-creator-identifier"></a>方案檔建立者識別碼  
 您可以變更方案 *名稱*中 "SolutionFileCreatorIdentifier" 資料列的值，藉以變更方案檔所使用的識別碼。.Pkgdef 檔案。  
  
##### <a name="the-default-projects-location"></a>預設專案位置  
 您可以變更 *方案名稱中*"DefaultProjectsLocation" 資料列的值，藉以變更預設專案位置的名稱。.Pkgdef 檔案。  
  
##### <a name="the-application-localization-package"></a>應用程式當地語系化套件  
 您可以變更程式 *名稱*中 "AppLocalizationPackage" 資料列的值，以變更應用程式所使用的當地語系化套件。.Pkgdef 檔案。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>是否要在標題中顯示階層根目錄  
 您可以在 [程式 *名稱*] 中變更 "ShowHierarchyRootInTitle" 資料列的值，以指定是否要在應用程式的標題列中顯示階層根。.Pkgdef 檔案。 若要顯示階層根、設定值 `dword:00000001` ，以及隱藏階層根，請設定此值 `dword:00000000` 。  
  
##### <a name="specifying-a-start-page"></a>指定起始頁  
 在 [程式 *名稱*] 中指定自訂應用程式的起始頁。.Pkgdef 檔案中，將 "DisableStartPage" 值設定為 `dword:00000000` ，然後 `[$RootKey$\StartPage\Default]` 將 URI 設定為 .xaml 檔案的位置：  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 在「 *解決方案名稱*」 UI 專案的 system.windows.input.applicationcommands.paste .vsct 檔案中，將 "No_ShellPkg_startPageCommand" 專案標記為批註：  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 您必須將 .xaml 檔案以及所需的任何圖形檔案，加入至 [方案 *名稱* ] 專案。 這些檔案實際上必須複製到「 *解決方案名稱* 」專案目錄，而不是從其他目錄加入。  
  
 在所有檔案上，將 [ **專案類型** ] 屬性設定為 [ **隔離的 Shell** 檔案]，以便將檔案複製到 *$RootFolder $* 目錄。  (若要設定 [ **專案類型** ] 屬性，請以滑鼠右鍵按一下檔案，然後選取 [ **屬性**]。 在 [設定 **屬性**]、 **[一般**] 底下找到此屬性。 )   
  
 如需自訂起始頁的詳細資訊，請參閱 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>使用隔離式 shell 的其他元素  
 您可以使用獨立 shell 方案範本中包含的其他檔案和專案，進一步自訂您的應用程式。  
  
##### <a name="enabledisable-visual-studio-packages"></a>啟用/停用 Visual Studio 套件  
 .Pkgundef 檔案可讓您藉由排除特定套件來停用特定類型的 Visual Studio*功能。* 例如，下列程式程式碼：  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 從 [ **新增專案** ] 對話方塊中顯示的一組專案範本，移除 [其他檔案] 專案。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="enabledisable-menu-commands"></a>啟用/停用功能表命令  
 程式 *名稱*.vsct 檔案包含可用於隔離式 shell 的所有功能表命令的批註式清單。 若要停用指定的命令，請取消批註對應的資料列。 例如，若要停用視窗/分割批註，請將資料列取消批註 `<Define name="No_SplitCommand"/>` 。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>啟動顯示畫面上使用的點陣圖  
 您可以自訂啟動顯示畫面上使用的點陣圖，也就是在啟動應用程式時所顯示的視窗，方法是變更程式 *名稱*中 "SplashScreenBitmap" 資料列的值。.Pkgdef 檔案。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-helpabout-window"></a>[說明]/[關於] 視窗  
 在獨立的 shell 範本中，您可以使用個別的專案，為應用程式自訂 [說明]/[關於] 方塊。 如需詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。
