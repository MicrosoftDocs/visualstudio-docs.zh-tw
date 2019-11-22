---
title: 逐步解說：建立基本獨立 Shell 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6dc84dd8d9f19012c4d09ba9bfd974ec181b9f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291267"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>逐步解說：建立基本獨立 Shell 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何建立獨立的 shell 解決方案、自訂 [說明] 工具視窗，以及建立安裝程式來安裝獨立的 shell。  
  
## <a name="prerequisites"></a>先決條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。 若要部署獨立的 shell，您也必須使用 Visual Studio Shell （獨立模式）可轉散發套件。  
  
## <a name="creating-an-isolated-shell-solution"></a>建立獨立的 Shell 解決方案  
 本節說明如何使用 Visual Studio Shell 隔離專案範本來建立獨立的 Shell 解決方案。 解決方案包含下列專案：  
  
- *解決方案名稱*。AboutBoxPackage 專案，可讓您自訂 [說明]/[關於] 方塊的外觀。  
  
- ShellExtensionsVSIX 專案，其中包含定義獨立 shell 應用程式之不同元件的 extension.vsixmanifest 檔案。  
  
- 程式*名稱*專案，它會產生叫用獨立 shell 應用程式的可執行檔。 此專案包含 Shell 自訂資料夾，可讓您 customiz 獨立模式 Shell 應用程式的外觀和行為。  
  
- [程式*名稱*] UI 專案，它會產生定義作用中功能表命令和可當地語系化字串的附屬元件。  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>建立基本的獨立 shell 解決方案  
  
1. 開啟 Visual Studio 並建立新專案。  
  
2. 在 [**新增專案**] 視窗中，依序展開 [**其他專案類型**] 和 [擴充性 **]。** 選取 [ **Visual Studio Shell 隔離**專案] 範本。  
  
3. 將專案命名為 `MyVSShellStub` 並指定位置。 請確定已核取 [**為方案建立目錄**]，然後按一下 **[確定]** 。  
  
     新的解決方案會出現在**方案總管**中。  
  
4. 建立解決方案，並開始對獨立的 shell 應用程式進行偵測。  
  
     Visual Studio 的獨立模式 shell 隨即出現。 標題列會讀取**MyVSShellStub**。 標題列圖示是從 \MyVSShellStub\Resource Files\ApplicationIcon.ico. 產生的  
  
## <a name="customizing-the-application-name-and-icon"></a>自訂應用程式名稱和圖示  
 您可能想要使用您公司的名稱及其在標題列中的標誌來為應用程式加上品牌。 下列步驟顯示如何藉由變更封裝定義檔 MyVSShellStub，變更顯示在自訂應用程式標題列中的名稱和圖示。  
  
#### <a name="to-customize-the-application-name-and-icon"></a>自訂應用程式名稱和圖示  
  
1. 在 MyVSShellStub 專案中，開啟 \Shell Customization\MyVSShellStub.Application.pkgdef。  
  
2. 將 `AppName` 元素值變更為 **"AppName" = "Fabrikam 音樂編輯器"**  
  
3. 若要變更應用程式圖示，請將不同的圖示複製到 \MyVSShellStub\MyVSShellStub\MyVSShellStub\ 目錄。 將現有的 ApplicationIcon .ico 檔案重新命名為 ApplicationIcon1。 將新檔案重新命名為 ApplicationIcon。  
  
4. 建置方案並開始偵錯。 獨立模式 shell IDE 隨即出現。 標題列在 [ **Fabrikam 音樂編輯器**] 單字旁有新的圖示。  
  
## <a name="customizing-the-default-web-browser-home-page"></a>自訂預設網頁瀏覽器首頁  
 本節說明如何藉由變更封裝定義檔來變更**Web 瀏覽器**視窗的預設首頁。  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>自訂預設網頁瀏覽器首頁  
  
1. 在 .pkgdef 檔案中，將 `DefaultHomePage` 元素值變更為 "<https://www.microsoft.com>"。  
  
2. 重建 MyVSShellStub 專案。  
  
3. 建置方案並開始偵錯。  
  
4. 在 [**查看/其他視窗**] 中，按一下 [**網頁瀏覽器**]。 [**網頁瀏覽器**] 視窗會顯示 Microsoft Corporation 首頁。  
  
## <a name="removing-the-print-command"></a>移除列印命令  
 獨立模式 shell UI 專案中的 .vsct 檔案包含一*組 `<Define name=No_`專案*`>`的宣告，其中*element*是標準 Visual Studio 功能表和命令的其中一個。  
  
 如果宣告為取消批註，則會從獨立的 shell 中排除該功能表或命令。 相反地，如果宣告已加上批註，則功能表或命令會包含在獨立的 shell 中。  
  
 在下列步驟中，您會在 .vsct 檔案中取消批註 print 命令。  
  
#### <a name="to-remove-the-print-command"></a>若要移除列印命令  
  
1. 確認 [**列印**] 命令出現在獨立模式 shell 應用程式的 [檔案 **] 功能表上**。  
  
2. 在 MyVSShellStubUI 專案中，開啟 \Resource Files\MyVSShellStubUI.vsct 以進行編輯。  
  
3. 取消批註這一行：  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. 這會移除 [列印] 命令。  
  
5. 開始對獨立模式 shell 應用程式進行偵錯工具。 確認**File/Print**命令已消失。  
  
## <a name="removing-features-from-the-isolated-shell"></a>從獨立模式 Shell 移除功能  
 如果您不想要在自訂獨立模式 shell 應用程式中使用這些功能，您可以藉由編輯 .pkgundef 檔案來移除載入 Visual Studio 的封裝。 您可以在 $RootKey $ \Packages 登錄機碼的其中一個子機碼中指定封裝。  
  
> [!NOTE]
> 若要尋找 Visual Studio 功能的 Guid，請參閱[Visual Studio 功能的封裝 guid](../extensibility/package-guids-of-visual-studio-features.md)。  
  
 下列程式顯示如何從獨立模式 shell 移除 XML 編輯器。  
  
#### <a name="to-remove-the-xml-editor"></a>若要移除 XML 編輯器  
  
1. 在 MyVSShellStub 專案的 [Shell 自訂] 資料夾中，開啟 MyVSShellStub .pkgundef 檔案。  
  
2. 取消批註下列程式程式碼：  
  
     [$RootKey $ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. 重建方案，並開始對獨立的 shell 進行偵錯工具。 開啟 XML 檔案，例如 \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct。 請確認檔案中的 XML 關鍵字不是以色彩標示，而且在一行上輸入 "<" 並不會顯示 XML 工具提示。  
  
## <a name="customizing-the-helpabout-box"></a>自訂 [說明]/[關於] 方塊  
 您可以自訂 [說明]/[關於] 方塊，此方塊會建立為獨立模式 shell 專案範本的一部分。  
  
#### <a name="to-customize-the-company-name"></a>自訂公司名稱  
  
1. 公司名稱、著作權資訊、產品版本和產品描述可在 \Properties\AssemblyInfo.cs 檔案中的 MyVSShellStub. AboutBoxPackage 專案中找到。 開啟此檔案。  
  
2. 將 `AssemblyCompany` 值變更為**fabrikam**、`AssemblyProduct` 和 `AssemblyTitle` 值設為**fabrikam 音樂編輯器**，並將 `AssemblyCopyright` 值設為**著作權© Fabrikam 2015**：  
  
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
  
3. 若要新增產品的描述，請將 `AssemblyDescription` 值變更為**Fabrikam 音樂編輯器的描述。** ：  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. 開始進行偵錯工具，然後在獨立模式 shell 應用程式中開啟 [說明] **/[關於**] 方塊。 您應該會看到已變更的字串。 [說明]/[關於] 方塊的標題與 [AssemblyInfo.cs] 中的 [`AssemblyTitle`] 值相同。  
  
5. [說明] **/[關於**] 方塊本身的屬性可在 MyVSShellStub. AboutBoxPackage\AboutBox.xaml 檔案中找到。 若要變更 [說明]/[關於] 方塊的寬度，請移至 [`AboutDialogStyle`] 區塊，並將 [`Width`] 屬性設為200：  
  
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
  
6. 重建方案，並開始對獨立的 shell 進行偵錯工具。 [說明]/[關於] 方塊應該大約是正方形。  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>部署獨立模式 Shell 應用程式之前  
 您的獨立 shell 應用程式可以安裝在任何具有 Visual Studio Shell （獨立模式）可轉散發套件的電腦上。 如需可轉散發套件的詳細資訊，請參閱 Visual Studio 擴充性[下載](https://go.microsoft.com/fwlink/?LinkID=119298)網站。  
  
## <a name="deploying-the-isolated-shell-application"></a>部署獨立模式 Shell 應用程式  
 您可以藉由建立安裝專案，將獨立的 shell 應用程式部署到目的電腦。 您必須指定下列專案：  
  
- 目的電腦上的資料夾和檔案版面配置。  
  
- 保證 .NET Framework 和 Visual Studio shell 執行時間已安裝在目的電腦上的啟動條件。  
  
  在下列程式中，您將需要在電腦上安裝 InstallShield 限量版。  
  
#### <a name="to-create-the-setup-project"></a>若要建立安裝專案  
  
1. 在**方案總管**中，以滑鼠右鍵按一下方案節點，然後按一下 [**加入新專案**]。  
  
2. 在 [**新增專案**] 對話方塊中，展開 [**其他專案類型**]，然後選取 [**安裝和部署**]。 選取 [InstallShield] 範本。 將新專案命名為 `MySetup`，然後按一下 **[確定]** 。  
  
3. 如果已安裝 InstallShield 限量版本，請繼續進行下一個步驟。  
  
    如果尚未安裝 InstallShield 限量版本，則會出現 InstallShield 下載頁面。 依照指示下載並安裝產品，並選擇與您的 Visual Studio 版本相容的 InstallShield 版本。 您必須決定是否要註冊您的 InstallShield 安裝，或使用它做為評估。 完成安裝之後，您必須重新開機 Visual Studio。  
  
   > [!IMPORTANT]
   > 在建立 InstallShield 專案之前，您必須以系統管理員身分啟動 Visual Studio。 如果您沒有這麼做，當您建立專案時，將會收到錯誤。  
  
   接下來的步驟示範如何設定安裝專案。  
  
> [!IMPORTANT]
> 設定安裝專案之前，請確定您已建立獨立 shell 專案的發行設定至少一次。  
  
#### <a name="to-configure-the-setup-project"></a>設定安裝專案  
  
1. 在 [**方案總管**] 的 [ **mysetup.ps1** ] 專案下，選擇 [**專案助理**]。 在 [**專案助理**] 視窗的底部列中，選擇 [**應用程式資訊**]。 輸入**fabrikam**作為您的 [公司名稱] 和 [ **fabrikam 音樂編輯器**] 做為您的應用程式名稱。 選擇 [**專案助理**] 右下方的 [向下] 箭號。  
  
2. 在 **[您的應用程式是否需要在電腦上安裝任何軟體？** ] 底下選取 **[是]** ，然後選取 [ **Microsoft .NET Framework 4.5 完整套件**]。  
  
3. 選擇視窗底部的 [**應用程式檔**] 按鈕，並確定已選取 [ **Fabrikam 音樂編輯器**] 資料夾。  
  
4. 選擇 [**加入**檔案] 按鈕。 在 [**新增**檔案] 對話方塊中，從 [ **MyVSShellStub\Release** ] 資料夾新增下列檔案：  
  
    1. MyVSShellStub .exe .config  
  
    2. DebuggerProxy .dll  
  
    3. DebuggerProxy 的資訊清單  
  
    4. MyVSShellStub. .pkgdef  
  
    5. MyVSShellStub. .pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. 啟動顯示 .bmp  
  
5. 按一下 [**加入專案輸出**] 按鈕，然後新增**MyVSShellStub/主要輸出**。 按一下 [**確定**]。  
  
6. 在左窗格的 [**目的地電腦**] 底下，以滑鼠右鍵按一下 [ **Fabrikam 音樂編輯器 [INSTALLDIR]]** 節點，然後新增名為 [**擴充**功能] 的**新資料夾**。  
  
7. 以滑鼠右鍵按一下左窗格中的 [**擴充**功能] 節點，然後新增名為 [**應用程式**] 的新資料夾。  
  
8. 選取**應用程式**資料夾，然後按一下 [**加入專案輸出**] 按鈕，然後從 [MyVSShellStub] AboutBoxPackage 專案選取主要輸出。  
  
9. 按一下 [**新增**檔案] 按鈕，然後從 [\MyVSShellStub\Release\Extensions\Application\] 資料夾新增下列檔案：  
  
    - MyVSShellStub. AboutBoxPackage. .pkgdef  
  
    - MyVSShellStub. Application. .pkgdef  
  
10. 以滑鼠右鍵按一下左窗格中的 **[Fabrikam 音樂編輯器 [INSTALLDIR]]** 節點，然後新增名為**1033**的新資料夾。  
  
11. 選取 [1033] 資料夾，然後按一下 [**加入專案輸出**] 按鈕，並選取 MyVSShellStubUI 專案的主要輸出。  
  
12. 移至 [**應用程式快捷方式**] 視窗。  
  
13. 按一下 [**新增**] 以建立快捷方式，然後選取 **[ProgramFilesFolder] \Fabrikam\Fabrikam 音樂 Editor\MyVSShellStub.Primary 輸出**。  
  
14. 移至 [**安裝訪談**] 窗格。  
  
15. 將所有專案設定為 [**否**]。  
  
16. 在**方案總管**的 mysetup.ps1 專案中，開啟 [**定義安裝需求和動作 \ 需求**]。 [**需求**] 視窗隨即開啟。  
  
17. 以滑鼠右鍵按一下 [**系統軟體需求**]，然後選取 [**建立新的啟動條件**]。 [**系統搜尋] Wizard**隨即出現。  
  
18. 在 [**您要尋找什麼？** ] 窗格中，選擇下拉式清單中的 [登錄**專案**]，然後按 **[下一步]** 。  
  
19. 在 [**您要如何尋找它？** ] 窗格中，選取 [ **HKEY_LOCAL_MACHINE** ] 做為登錄根目錄。 輸入**SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell**作為64位系統或32位系統的**SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** ，並輸入**Install**做為登錄值。 按 [下一步]。  
  
20. 在 [**您要對此值執行什麼動作？** ] 窗格中，輸入**此產品需要安裝 Visual Studio 2015 獨立模式 Shell 可**轉散發套件。 做為顯示文字，然後按一下 **[完成]** 。  
  
21. 重建獨立的 shell 方案，以建立安裝專案。  
  
     您可以在下列資料夾中找到 setup.exe 檔案：  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>測試安裝程式  
 若要測試安裝，請將 setup.exe 檔案複製到另一部電腦，然後執行安裝程式可執行檔。 您應該能夠執行獨立模式 shell 應用程式。
