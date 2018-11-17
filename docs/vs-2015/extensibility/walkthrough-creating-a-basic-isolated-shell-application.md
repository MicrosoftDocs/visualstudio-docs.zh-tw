---
title: 逐步解說： 建立基本獨立 Shell 應用程式 |Microsoft Docs
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
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 901bbf12c9c1d153b84b3ed74f6ae8e97ebb2c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777314"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>逐步解說： 建立基本的 Isolated 的 Shell 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何建立獨立模式的 shell 解決方案、 自訂 [關於說明] 工具視窗中，並建立安裝程式來安裝獨立模式的 shell。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 若要部署 isolated 的 shell，您也必須使用 Visual Studio Shell （獨立模式） 可轉散發套件。  
  
## <a name="creating-an-isolated-shell-solution"></a>建立獨立模式的 Shell 解決方案  
 本節說明如何使用 Visual Studio Shell 獨立模式的專案範本來建立獨立模式的 shell 解決方案。 解決方案包含下列專案：  
  
-   *SolutionName*。AboutBoxPackage 專案，可讓您自訂的說明/關於 對話方塊的外觀。  
  
-   ShellExtensionsVSIX 專案，其中包含可定義 isolated 的 shell 應用程式的不同元件的 source.extension.vsixmanifest 檔案。  
  
-   *SolutionName*產生 isolated 的 shell 應用程式會叫用的可執行檔的專案。 此專案包含可讓您 customiz 外觀和行為的 isolated 的 shell 應用程式的 Shell 自訂資料夾。  
  
-   *SolutionName* UI 專案，這會產生附屬組件會定義使用中的功能表命令和可當地語系化的字串。  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>若要建立基本的 isolated 的 shell 方案  
  
1.  開啟 Visual Studio 並建立新專案。  
  
2.  在 [**新的專案**] 視窗中，展開**其他專案類型**，然後**擴充性**。 選取  **Visual Studio Shell 獨立模式**專案範本。  
  
3.  將專案命名為`MyVSShellStub`和指定的位置。 請確定**為方案建立目錄**勾選，，然後按一下**確定**。  
  
     新的解決方案會出現在**方案總管 中**。  
  
4.  建置方案，並開始偵錯 isolated 的 shell 應用程式。  
  
     Visual Studio 隔離 shell 隨即出現。 標題列讀取**MyVSShellStub**。 標題列圖示是從 \MyVSShellStub\Resource Files\ApplicationIcon.ico 產生。  
  
## <a name="customizing-the-application-name-and-icon"></a>自訂應用程式名稱和圖示  
 若要設定您的應用程式的品牌標題列中使用您的公司和其標誌的名稱。 下列步驟示範如何變更的名稱及所變更的封裝定義檔，MyVSShellStub.Application.pkgdef 自訂應用程式標題列中顯示的圖示。  
  
#### <a name="to-customize-the-application-name-and-icon"></a>若要自訂的應用程式名稱和圖示  
  
1.  在 MyVSShellStub 專案中，開啟 [\Shell Customization\MyVSShellStub.Application.pkgdef]。  
  
2.  變更`AppName`項目值 **:"AppName"="Fabrikam 音樂編輯器**  
  
3.  若要變更應用程式圖示，將不同的圖示複製到 \MyVSShellStub\MyVSShellStub\MyVSShellStub\ 目錄。 將現有的 ApplicationIcon.ico 檔案的重新命名為 ApplicationIcon1.ico。 新的檔案重新命名為 ApplicationIcon.ico。  
  
4.  建置方案並開始偵錯。 Isolated 的 shell IDE 會出現。 標題列有您新的圖示，字組旁邊**Fabrikam 音樂編輯器**。  
  
## <a name="customizing-the-default-web-browser-home-page"></a>自訂預設網頁瀏覽器首頁  
 本節說明如何變更預設首頁**網頁瀏覽器**視窗中的變更封裝定義檔。  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>若要自訂預設網頁瀏覽器首頁  
  
1. 在 MyVSShellStub.Application.pkgdef 檔案中，變更`DefaultHomePage`項目值 」<http://www.microsoft.com>"。  
  
2. 重建 MyVSShellStub 專案。  
  
3. 建置方案並開始偵錯。  
  
4. 在 **檢視 / 其他 Windows**，按一下**網頁瀏覽器**。 **網頁瀏覽器**視窗會顯示 Microsoft Corporation 的 [首頁] 頁面。  
  
## <a name="removing-the-print-command"></a>移除列印命令  
 .Vsct 檔在獨立模式的 shell UI 專案中包含的一組宣告的形式`<Define name=No_`*項目*`>`，其中*項目*是其中一個標準的 Visual Studio 功能表和命令。  
  
 如果取消註解的宣告，該功能表或命令時會排除 isolated shell。 相反地，如果宣告標記為註解，則功能表或命令包含在獨立模式 shell。  
  
 在下列步驟中，您取消註解列印命令在.vsct 檔案中。  
  
#### <a name="to-remove-the-print-command"></a>若要移除的列印命令  
  
1.  確認**列印**才會出現指令**檔案**isolated 的 shell 應用程式中的功能表。  
  
2.  在 MyVSShellStubUI 專案中，開啟 \Resource Files\MyVSShellStubUI.vsct 進行編輯。  
  
3.  這行取消註解：  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  這會移除列印命令。  
  
5.  開始偵錯 isolated 的 shell 應用程式。 確認**檔案 / 列印**命令已不存在。  
  
## <a name="removing-features-from-the-isolated-shell"></a>從獨立的 Shell 中移除功能  
 您可以移除某些編輯.pkgundef 檔案，如果您不要在您自訂的 isolated 的 shell 應用程式的功能與 Visual Studio 會載入的封裝。 您在其中 $RootKey$ \Packages 的登錄機碼的子機碼中指定的套件。  
  
> [!NOTE]
>  若要尋找 Visual Studio 的 Guid 功能，請參閱[封裝的 Guid 的 Visual Studio 功能](../extensibility/package-guids-of-visual-studio-features.md)。  
  
 下列程序顯示如何移除 XML 編輯器與獨立模式 shell。  
  
#### <a name="to-remove-the-xml-editor"></a>若要移除 XML 編輯器  
  
1.  開啟 MyVSShellStub.pkgundef 檔案 MyVSShellStub 專案的 Shell 自訂資料夾中。  
  
2.  下面這行取消註解：  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  重建方案，並開始偵錯 isolated 的 shell。 開啟 XML 檔案，比方說，\MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct。 請確認檔案中的 XML 關鍵字會不以色彩標示和輸入"<"該行不會使 XML 工具提示。  
  
## <a name="customizing-the-helpabout-box"></a>自訂 [說明] / [關於] 對話方塊  
 您可以自訂 [說明/關於] 方塊中，這會建立為獨立的 shell 專案範本的一部分。  
  
#### <a name="to-customize-the-company-name"></a>若要自訂公司名稱  
  
1.  公司名稱、 著作權資訊、 產品版本和產品說明中找到 MyVSShellStub.AboutBoxPackage 專案，\Properties\AssemblyInfo.cs 檔案中。 開啟此檔案。  
  
2.  變更`AssemblyCompany`值**Fabrikam**，則`AssemblyProduct`和`AssemblyTitle`值**Fabrikam 音樂編輯器**，而`AssemblyCopyright`值**Copyright ©Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  若要新增的產品的描述，請變更`AssemblyDescription`值加入**Fabrikam 音樂編輯器的描述。**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  開始偵錯，並在獨立模式的 shell 應用程式中，開啟**協助 / 關於** 方塊中。 您應該會看到已變更的字串。 「 說明/關於 對話方塊的標題是相同`AssemblyTitle`AssemblyInfo.cs 中的值。  
  
5.  屬性**說明/關於**方塊本身位於 MyVSShellStub.AboutBoxPackage\AboutBox.xaml 檔案。 若要變更的說明/關於 方塊的寬度，請前往`AboutDialogStyle`區塊並將設定`Width`到 200 個的屬性：  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  重建方案，並開始偵錯 isolated 的 shell。 「 說明/關於 方塊應為大約正方形。  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>然後再部署 Isolated 的 Shell 應用程式  
 您的獨立的 shell 應用程式可以安裝有 Visual Studio Shell （獨立模式） 可轉散發套件的任何電腦上。 如需有關可轉散發套件的詳細資訊，請參閱[Visual Studio 擴充性下載](http://go.microsoft.com/fwlink/?LinkID=119298)網站。  
  
## <a name="deploying-the-isolated-shell-application"></a>部署獨立的 Shell 應用程式  
 您可以建立安裝專案部署到目標電腦您 isolated 的 shell 應用程式。 您必須指定這些項目：  
  
- 在目標電腦上的檔案和資料夾的版面配置。  
  
- 保證在.NET Framework 和 Visual Studio shell 執行階段的啟動條件會安裝在目標電腦上。  
  
  在下列程序中，您必須在電腦上安裝 InstallShield Limited Edition。  
  
#### <a name="to-create-the-setup-project"></a>若要建立安裝專案  
  
1. 在 **方案總管**，以滑鼠右鍵按一下方案節點，然後按一下**加入新的專案**。  
  
2. 在 **新的專案**對話方塊方塊中，展開**其他專案類型**，然後選取**安裝和部署**。 選取 InstallShield 範本。 將新專案命名`MySetup`，然後按一下  **確定**。  
  
3. 如果已經安裝 InstallShield 限量版，則繼續下一個步驟。  
  
    如果尚未安裝 InstallShield 限量版，則會出現 InstallShield 下載頁面。 請遵循指示下載並安裝此產品中，選擇適用於您的 Visual Studio 版本的 InstallShield 的版本。 您必須決定是否要註冊的 InstallShield 安裝，或使用它作為一份評估。 完成安裝之後，您必須重新啟動 Visual Studio。  
  
   > [!IMPORTANT]
   >  建立 InstallShield 專案之前，您必須以系統管理員身分啟動 Visual Studio。 如果不這麼做，您會收到錯誤，當您建置專案。  
  
   接下來的步驟示範如何設定安裝專案。  
  
> [!IMPORTANT]
>  請確定您已設定安裝專案之前可能建立獨立的 shell 專案的發行組態至少一次。  
  
#### <a name="to-configure-the-setup-project"></a>若要設定的安裝專案  
  
1.  中**方案總管**下方**MySetup**專案，選擇**Project Assistant**。 在底部的資料列**Project Assistant**  視窗中，選擇**應用程式資訊**。 輸入**Fabrikam**為您的公司名稱並**Fabrikam 音樂編輯器**做為您的應用程式名稱。 選擇 下的一步箭頭在右下方**Project Assistant**。  
  
2.  選取 **[是]** 下方**您的應用程式是否需要在電腦上安裝任何軟體？** ，然後選取**Microsoft.NET Framework 4.5 的完整套件**。  
  
3.  選擇**應用程式檔案**底部的視窗 按鈕，並確定**Fabrikam 音樂編輯器**選取資料夾。  
  
4.  選擇**將檔案新增** 按鈕。 在 **加入檔案**對話方塊方塊中，加入下列檔案從**MyVSShellStub\Release**資料夾：  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  按一下 **加入專案輸出**按鈕，然後新增**MyVSShellStub/主要輸出**。 按一下 [確定 **Deploying Office Solutions**]。  
  
6.  在左窗格中，在**目的地電腦**，以滑鼠右鍵按一下**Fabrikam 音樂編輯器 [INSTALLDIR]** 節點，並新增**新資料夾**名為**延伸模組**.  
  
7.  以滑鼠右鍵按一下**延伸模組**的左窗格中的節點，並新增名為的新資料夾**應用程式**。  
  
8.  選取 **應用程式**資料夾，然後按一下**加入專案輸出**按鈕，然後從 MyVSShellStub.AboutBoxPackage 專案中選取的主要輸出。  
  
9. 按一下 **將檔案新增**按鈕，然後從 \MyVSShellStub\Release\Extensions\Application\ 資料夾中，加入下列檔案：  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. 以滑鼠右鍵按一下**Fabrikam 音樂編輯器 [INSTALLDIR]** 的左窗格中的節點，並新增名為的新資料夾**1033年**。  
  
11. 選取 [1033年] 資料夾，然後按一下**加入專案輸出**按鈕，然後選取從 MyVSShellStubUI 專案的主要輸出。  
  
12. 移至**應用程式捷徑**視窗。  
  
13. 按一下 **的新**若要建立捷徑，然後選取 **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**。  
  
14. 移至**安裝會談**窗格。  
  
15. 若要設定所有項目**No**。  
  
16. 在 [**方案總管] 中**，在 MySetup 專案中，開啟**Define Setup Requirements and 動作 \ 需求**。 **需求**視窗隨即開啟。  
  
17. 以滑鼠右鍵按一下**軟體的系統需求**，然後選取**建立新的啟動條件**。 **系統搜尋精靈**隨即出現。  
  
18. 在 [**您想要尋找？** 窗格中，選擇**登錄項目**中的下拉式清單，然後按一下**下一步]**。  
  
19. 在 **您要如何尋找它？** 窗格中，選取**HKEY_LOCAL_MACHINE**以登錄 root 的身分。 輸入**SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell**適用於 64 位元系統或**SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell**適用於 32 位元系統，然後輸入**安裝**做為登錄值。 按 [ **下一步**]。  
  
20. 在 **您想要的值？** 窗格中，輸入**此產品需要 Visual Studio 2015 獨立 Shell 可轉散發套件安裝。** 作為顯示文字，然後按一下**完成**。  
  
21. 重建獨立模式的 shell 方案建立安裝專案。  
  
     您可以在下列資料夾中找到 setup.exe 檔案：  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>測試安裝程式  
 若要測試安裝，請將 setup.exe 檔案複製到另一部電腦並執行安裝程式可執行檔。 您應該能夠執行 isolated 的 shell 應用程式。

