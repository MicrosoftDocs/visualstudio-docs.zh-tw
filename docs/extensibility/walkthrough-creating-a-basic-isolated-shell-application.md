---
title: "逐步解說： 建立基本獨立 Shell 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e007e366847ac42d3916b16cbde190e8fd755821
ms.contentlocale: zh-tw
ms.lasthandoff: 08/17/2017

---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>逐步解說： 建立基本獨立的 Shell 應用程式
本逐步解說示範如何建立獨立的 shell 方案、 自訂 [說明] 工具視窗中，以及建立安裝程式安裝在 isolated 的 shell。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 若要部署獨立的 shell，您也必須使用 Visual Studio Shell （隔離式） 可轉散發套件。  
  
## <a name="creating-an-isolated-shell-solution"></a>建立 Isolated 的 Shell 方案  
 本節說明如何使用 Visual Studio Shell 外掛式主控專案範本來建立獨立的 shell 的方案。 解決方案包含下列專案：  
  
-   *SolutionName*。AboutBoxPackage 專案，可讓您自訂的說明 / 關於 方塊的外觀。  
  
-   ShellExtensionsVSIX 專案，其中包含定義 isolated 的 shell 應用程式的不同元件的 source.extension.vsixmanifest 檔案。  
  
-   *SolutionName*會產生獨立的 shell 應用程式會叫用的可執行檔的專案。 此專案包含可讓您 customiz 外觀和行為的 isolated 的 shell 應用程式的 Shell Customization 資料夾。  
  
-   *SolutionName* UI 專案，會產生附屬組件會定義使用中的功能表命令以及可當地語系化的字串。  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>若要建立基本獨立的 shell 方案  
  
1.  開啟 Visual Studio 並建立新專案。  
  
2.  在**新專案**視窗中，展開 **其他專案類型**然後**擴充性**。 選取**Visual Studio Shell 外掛式主控**專案範本。  
  
3.  將專案命名`MyVSShellStub`和指定的位置。 請確定**為方案建立目錄**勾選，，然後按一下 **確定**。  
  
     新的方案會出現在**方案總管 中**。  
  
4.  建置方案，並開始偵錯 isolated 的 shell 應用程式。  
  
     Visual Studio isolated shell 隨即出現。 標題列讀取**MyVSShellStub**。 標題列圖示是從 \MyVSShellStub\Resource Files\ApplicationIcon.ico 產生。  
  
## <a name="customizing-the-application-name-and-icon"></a>自訂的應用程式名稱和圖示  
 若要設定您的應用程式的標題列中使用的公司和其標誌名稱的品牌。 下列步驟顯示如何變更名稱和變更封裝定義檔，MyVSShellStub.Application.pkgdef 自訂應用程式標題列中顯示的圖示。  
  
#### <a name="to-customize-the-application-name-and-icon"></a>若要自訂的應用程式名稱和圖示  
  
1.  在 MyVSShellStub 專案中，開啟 \Shell Customization\MyVSShellStub.Application.pkgdef。  
  
2.  變更`AppName`項目值要**:"AppName"="Fabrikam 音樂 Editor"**  
  
3.  若要變更應用程式圖示，將複製到 \MyVSShellStub\MyVSShellStub\MyVSShellStub\ 目錄的不同的圖示。 將現有的 ApplicationIcon.ico 檔案重新命名為 ApplicationIcon1.ico。 新的檔案重新命名 ApplicationIcon.ico。  
  
4.  建置方案並開始偵錯。 在 isolated 的 shell IDE 就會出現。 標題列有您新的圖示，字組旁邊**Fabrikam 音樂編輯器**。  
  
## <a name="customizing-the-default-web-browser-home-page"></a>自訂預設網頁瀏覽器首頁  
 本節說明如何變更預設的首頁的**網頁瀏覽器**視窗中的變更封裝定義檔。  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>若要自訂預設網頁瀏覽器首頁  
  
1.  在 MyVSShellStub.Application.pkgdef 檔案中，變更`DefaultHomePage`"http://www.microsoft.com"的項目值。  
  
2.  重建 MyVSShellStub 專案。  
  
3.  建置方案並開始偵錯。  
  
4.  在**檢視 / 其他視窗**，按一下 **網頁瀏覽器**。 **網頁瀏覽器**視窗會顯示 Microsoft Corporation 的 [首頁] 頁面。  
  
## <a name="removing-the-print-command"></a>移除列印命令  
 .Vsct 檔中的獨立的 shell UI 專案組成一組宣告的形式`<Define name=No_`*元素*`>`，其中*元素*是其中一個標準的 Visual Studio 功能表和命令。  
  
 如果宣告是取消註解，該功能表或命令會排除在 isolated shell 中。 相反地，如果宣告標記為註解，功能表或命令包含在 isolated shell 中。  
  
 在下列步驟中，您取消註解列印命令.vsct 檔案中。  
  
#### <a name="to-remove-the-print-command"></a>若要移除的列印命令  
  
1.  確認**列印**命令會出現在**檔案**獨立的 shell 應用程式功能表中。  
  
2.  在 MyVSShellStubUI 專案中，開啟 \Resource Files\MyVSShellStubUI.vsct 進行編輯。  
  
3.  取消註解此行：  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  這會移除列印命令。  
  
5.  開始偵錯 isolated 的 shell 應用程式。 確認**檔案 / 列印**命令就會消失。  
  
## <a name="removing-features-from-the-isolated-shell"></a>從 Isolated Shell 中移除功能  
 您可以移除某些藉由編輯.pkgundef 檔案，如果您不想自訂的獨立的 shell 應用程式中的功能與 Visual Studio 會載入的封裝。 您在其中 $RootKey$ \Packages 登錄機碼的子機碼中指定的封裝。  
  
> [!NOTE]
>  若要尋找 Visual Studio Guid 功能，請參閱[封裝 Guid 的 Visual Studio 功能](../extensibility/package-guids-of-visual-studio-features.md)。  
  
 下列程序會示範如何移除 XML 編輯器與在 isolated shell。  
  
#### <a name="to-remove-the-xml-editor"></a>若要移除 XML 編輯器  
  
1.  開啟 MyVSShellStub.pkgundef 檔案 MyVSShellStub 專案的 Shell Customization 資料夾中。  
  
2.  取消註解下列一行：  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  重建方案，並開始偵錯在 isolated 的 shell。 開啟 XML 檔案，比方說，\MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct。 請確認檔案中的 XML 關鍵字未標示有色彩和輸入"<"該行不會讓 XML 工具提示。  
  
## <a name="customizing-the-helpabout-box"></a>自訂 說明/關於方塊  
 您可以自訂 [說明/關於] 方塊中，這會建立為獨立的 shell 專案範本的一部分。  
  
#### <a name="to-customize-the-company-name"></a>若要自訂公司名稱  
  
1.  公司名稱、 版權資訊、 產品版本和產品說明中找到 MyVSShellStub.AboutBoxPackage 專案 \Properties\AssemblyInfo.cs 檔案中。 開啟此檔案。  
  
2.  變更`AssemblyCompany`值設定為**Fabrikam**、`AssemblyProduct`和`AssemblyTitle`值**Fabrikam 音樂編輯器**，而`AssemblyCopyright`值設定為**Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")]  
    ```  
  
3.  若要新增之產品的描述，請變更`AssemblyDescription`值設定為**Fabrikam 音樂編輯器的描述。**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.")]  
    ```  
  
4.  開始偵錯，並在獨立的 shell 應用程式中，開啟**說明 / 關於**方塊。 您應該會看到已變更的字串。 標題的 說明/關於方塊是與相同`AssemblyTitle`AssemblyInfo.cs 中的值。  
  
5.  內容**說明/關於**方塊本身 MyVSShellStub.AboutBoxPackage\AboutBox.xaml 檔案中找到。 若要變更 說明/關於方塊的寬度，請移至`AboutDialogStyle`區塊並將設定`Width`到 200 個屬性：  
  
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
  
6.  重建方案，並開始偵錯在 isolated 的 shell。 說明/關於方塊應該是大約正方形。  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>在部署獨立的 Shell 應用程式之前  
 獨立的 shell 應用程式可以安裝在任何具有 Visual Studio Shell （隔離式） 可轉散發套件的電腦上。 如需可轉散發套件的詳細資訊，請參閱[Visual Studio 擴充性下載](http://go.microsoft.com/fwlink/?LinkID=119298)網站。  
  
## <a name="deploying-the-isolated-shell-application"></a>部署獨立的 Shell 應用程式  
 您藉由建立安裝專案部署獨立的 shell 應用程式的目標電腦。 您必須指定下列項目：  
  
-   在目標電腦上的檔案和資料夾的版面配置。  
  
-   啟動條件，以保證在.NET Framework 和 Visual Studio shell 執行階段會在目標電腦上安裝。  
  
 在下列程序中，您必須在電腦上安裝 InstallShield Limited Edition。  
  
#### <a name="to-create-the-setup-project"></a>若要建立安裝專案  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下方案節點，然後按一下**加入新的專案**。  
  
2.  在**新專案**對話方塊方塊中，展開 **其他專案類型**，然後選取 **安裝和部署**。 選取的 InstallShield 範本。 將新專案`MySetup`，然後按一下 **確定**。  
  
3.  如果已安裝 InstallShield 限量版，繼續下一個步驟。  
  
     如果尚未安裝 InstallShield Limited Edition，則會出現 InstallShield 下載頁面。 依照指示下載並安裝的產品，選擇 InstallShield 與您的 Visual Studio 版本相容的版本。 您必須決定是否要註冊的 InstallShield 安裝或使用它來評估。 完成安裝之後，您必須重新啟動 Visual Studio。  
  
    > [!IMPORTANT]
    >  建立 InstallShield 專案之前，您必須以系統管理員身分啟動 Visual Studio。 如果不這麼做，您會收到錯誤，當您建置專案。  
  
 接下來的步驟示範如何設定安裝專案。  
  
> [!IMPORTANT]
>  請確認您已設定安裝專案之前建置獨立的 shell 專案的發行組態至少一次。  
  
#### <a name="to-configure-the-setup-project"></a>若要設定安裝專案  
  
1.  在**方案總管 中**下**MySetup**專案，選擇**Project Assistant**。 上的底端列**Project Assistant**視窗中，選擇**應用程式資訊**。 輸入**Fabrikam**為您的公司名稱和**Fabrikam 音樂編輯器**做為您的應用程式名稱。 選擇的右下方的正向箭號**Project Assistant**。  
  
2.  選取**是**下**應用程式是否需要在電腦上安裝任何軟體？** ，然後選取  **Microsoft.NET Framework 4.5 的完整套件**。  
  
3.  選擇**應用程式檔案**在視窗底部的按鈕，並確定**Fabrikam 音樂編輯器**選取資料夾。  
  
4.  選擇**加入檔案** 按鈕。 在**加入檔案**對話方塊方塊中，加入下列檔案從此**MyVSShellStub\Release**資料夾：  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  按一下**加入專案輸出**按鈕，然後加入**MyVSShellStub/主要輸出**。 按一下 [確定]。  
  
6.  在左窗格中下,**目的地電腦**，以滑鼠右鍵按一下**Fabrikam 音樂編輯器 [INSTALLDIR]**節點並加入**新資料夾**名為**延伸**。  
  
7.  以滑鼠右鍵按一下**延伸**的左窗格中的節點並加入新的資料夾，名為**應用程式**。  
  
8.  選取**應用程式**資料夾，然後按一下**加入專案輸出**按鈕，然後選取從 MyVSShellStub.AboutBoxPackage 專案主要輸出。  
  
9. 按一下**加入檔案**按鈕，然後從 \MyVSShellStub\Release\Extensions\Application\ 資料夾中，加入下列檔案：  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. 以滑鼠右鍵按一下**Fabrikam 音樂編輯器 [INSTALLDIR]**的左窗格中的節點並加入新的資料夾，名為**1033年**。  
  
11. 選取 [1033年] 資料夾，然後按一下**加入專案輸出**按鈕，然後選取從 MyVSShellStubUI 專案主要輸出。  
  
12. 移至**應用程式捷徑**視窗。  
  
13. 按一下**新增**建立捷徑，並選取**[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**。  
  
14. 移至**安裝會談**窗格。  
  
15. 若要設定的所有項目**否**。  
  
16. 在**方案總管 中**，MySetup 專案中，開啟**Define Setup Requirements and 動作 \ 需求**。 **需求**視窗隨即開啟。  
  
17. 以滑鼠右鍵按一下**系統軟體需求**選取**建立新的啟動條件**。 **系統搜尋精靈**隨即出現。  
  
18. 在**您想要尋找？**  窗格中，選擇**登錄項目**下拉式清單中按一下**下一步**。  
  
19. 在**您想要尋找其？**窗格中，選取**HKEY_LOCAL_MACHINE**做為登錄根目錄。 輸入**SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 64 位元系統或**SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 32 位元系統，並輸入**安裝**做為登錄值。 按 [ **下一步**]。  
  
20. 在**您想要的值做什麼？**  窗格中，輸入**需要 Visual Studio 2015 隔離 Shell 可轉散發安裝本產品。** 按一下顯示的文字以及**完成**。  
  
21. 重建獨立的 shell 方案以建立安裝專案。  
  
     您可以在下列資料夾中找到的 setup.exe 檔案：  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>測試安裝程式  
 若要測試安裝程式，將 setup.exe 檔案複製到另一部電腦，並執行安裝程式可執行檔。 您應該能夠執行獨立的 shell 應用程式。
