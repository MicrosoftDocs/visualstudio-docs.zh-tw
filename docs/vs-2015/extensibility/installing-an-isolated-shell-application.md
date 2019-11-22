---
title: 安裝獨立模式 Shell 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a077173a0d095ee10cc1fa16da3db1f3744dafa8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301160"
---
# <a name="installing-an-isolated-shell-application"></a>安裝獨立模式 Shell 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要安裝 Shell 應用程式，您必須執行下列步驟。  
  
- 準備您的解決方案。  
  
- 為您的應用程式建立 Windows Installer （MSI）套件。  
  
- 建立安裝程式啟動載入器。  
  
  本檔中的所有範例程式碼都來自于 [ [Shell 部署範例](https://go.microsoft.com/fwlink/?LinkId=262245)]，您可以從 MSDN 網站上的程式碼庫下載。 此範例會顯示執行上述每個步驟的結果。  
  
## <a name="prerequisites"></a>先決條件  
 若要執行本主題所述的程式，您的電腦上必須安裝下列工具。  
  
- Visual Studio SDK  
  
- [WINDOWS INSTALLER XML 工具](https://go.microsoft.com/fwlink/?LinkId=82720)組版本3。6  
  
  此範例也需要 Microsoft 視覺效果和模型化 SDK，而不是所有的 shell 都需要。  
  
## <a name="preparing-your-solution"></a>準備您的解決方案  
 根據預設，Shell 範本會建立到 VSIX 封裝，但此行為主要是用於偵錯工具。 當您部署 Shell 應用程式時，您必須使用 MSI 套件來允許登錄存取，並在安裝期間重新開機。 若要準備您的應用程式以進行 MSI 部署，請執行下列步驟。  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>準備 Shell 應用程式以進行 MSI 部署  
  
1. 編輯方案中的每個 extension.vsixmanifest 檔案。  
  
     在 `Identifier` 專案中，加入 `InstalledByMSI` 元素和 `SystemComponent` 元素，然後將其值設定為 `true`。  
  
     這些元素會防止 VSIX 安裝程式嘗試安裝您的元件，而使用者無法使用 [**擴充功能和更新**] 對話方塊將它們卸載。  
  
2. 針對每個包含 VSIX 資訊清單的專案，編輯組建工作，將內容輸出至 MSI 將安裝的位置。 在組建輸出中包含 VSIX 資訊清單，但不要建立 .vsix 檔案。  
  
## <a name="creating-an-msi-for-your-shell"></a>建立命令介面的 MSI  
 若要建立 MSI 套件，建議您使用[WINDOWS INSTALLER XML 工具](https://go.microsoft.com/fwlink/?LinkId=82720)組，因為它比標準安裝專案提供更大的彈性。  
  
 在 wsmanconfig.wxs 專案檔案中，設定偵測區塊和 Shell 元件的版面配置。  
  
 然後在您方案的 .reg 檔案和 ApplicationRegistry. wsmanconfig.wxs 專案中建立登錄專案。  
  
### <a name="detection-blocks"></a>偵測區塊  
 偵測區塊包含指定要偵測之必要條件的 `Property` 專案，以及指定在電腦上不存在必要條件時要傳回之訊息的 `Condition` 元素。 例如，您的 Shell 應用程式將需要 Microsoft Visual Studio Shell 可轉散發套件，而偵測區塊會類似下列標記。  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Shell 元件的版面配置  
 您必須加入元素，以識別要安裝的目標目錄結構和元件。  
  
##### <a name="to-set-the-layout-of-shell-components"></a>設定 Shell 元件的版面配置  
  
1. 建立 `Directory` 元素的階層，以代表要在目的電腦上的檔案系統上建立的所有目錄，如下列範例所示。  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     當指定必須安裝的檔案時，`Id` 會參考這些目錄。  
  
2. 識別 Shell 和您的 Shell 應用程式所需的元件，如下列範例所示。  
  
    > [!NOTE]
    > 有些元素可能會參考其他 wsmanconfig.wxs 專案檔中的定義。  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. `ComponentRef` 元素會參考另一個 wsmanconfig.wxs 專案檔，以識別目前元件所需的檔案。 例如，GeneralProfile 在 HelpAbout 中具有下列定義： wsmanconfig.wxs 專案。  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef` 元素會指定這些檔案在使用者電腦上的位置。 `Directory` 專案會指定要將它安裝到子目錄中，而每個 `File` 元素代表一個已建立的檔案或存在於方案中的檔案，並識別在建立 MSI 檔案時，可以在何處找到該檔案。  
  
    2. `ComponentGroupRef` 元素會參考其他元件（或元件和元件群組）的群組。 例如，ApplicationGroup 下的 `ComponentGroupRef` 在 wsmanconfig.wxs 專案中定義如下。  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > Shell （獨立模式）應用程式所需的相依性為： DebuggerProxy、MasterPkgDef、Resources （尤其是 winprf 檔案）、Application 和 PkgDefs。  
  
### <a name="registry-entries"></a>登錄項目  
 Shell （獨立模式）專案範本包含用於在安裝時合併之登錄機碼的*專案名稱*.reg 檔案。 這些登錄專案必須是 MSI 的一部分，以供安裝和清除之用。 您也必須在 ApplicationRegistry 中建立相符的登錄區塊。 wsmanconfig.wxs 專案。  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>將登錄專案整合至 MSI  
  
1. 在 [ **Shell 自訂**] 資料夾中，開啟 [*專案名稱*.reg]。  
  
2. 將 $RootFolder $ token 的所有實例取代為目標安裝目錄的路徑。  
  
3. 新增您的應用程式所需的任何其他登錄專案。  
  
4. 開啟 ApplicationRegistry. wsmanconfig.wxs 專案。  
  
5. 針對*專案名稱*.reg 中的每個登錄專案，新增對應的登錄區塊，如下列範例所示。  
  
    |*專案名稱*.reg|ApplicationRegisty. wsmanconfig.wxs 專案|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT \CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "PhotoStudio DTE Object"|\<RegistryKey Id = ' DteClsidRegKey ' 根 = ' HKCR ' 索引鍵 = ' $ （var。DteClsidRegKey） ' Action = ' createAndRemoveOnUninstall ' ><br /><br /> \<的 RegistryValue 類型 = ' 字串 ' 名稱 = ' @ ' 值 = ' $ （var。ShortProductName） DTE 物件 '/><br /><br /> \</RegistryKey >|  
    |[HKEY_CLASSES_ROOT \CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @ = "$RootFolder $ \PhotoStudio.exe"|\<RegistryKey Id = ' DteLocSrv32RegKey ' 根 = ' HKCR ' 索引鍵 = ' $ （var。DteClsidRegKey） \LocalServer32 ' Action = ' createAndRemoveOnUninstall ' ><br /><br /> \<的 RegistryValue 類型 = ' 字串 ' 名稱 = ' @ ' 值 = ' [INSTALLDIR] $ （var。ShortProductName） .exe '/><br /><br /> \</RegistryKey >|  
  
     在此範例中，DteClsidRegKey 會解析為頂端資料列中的登錄機碼。 ShortProductName 會解析為 `PhotoStudio`。  
  
## <a name="creating-a-setup-bootstrapper"></a>建立安裝程式啟動載入器  
 只有在先安裝所有必要條件之後，才會安裝已完成的 MSI。 若要簡化使用者體驗，請建立安裝程式，以收集並安裝所有必要條件，然後再安裝您的應用程式。 若要確保安裝成功，請執行下列動作：  
  
- 強制安裝系統管理員。  
  
- 偵測是否已安裝 Visual Studio Shell （獨立模式）。  
  
- 依序執行一或兩個 Shell 安裝程式。  
  
- 處理重新開機要求。  
  
- 執行您的 MSI。  
  
### <a name="enforcing-installation-by-administrator"></a>強制安裝系統管理員  
 這是啟用安裝程式以存取所需目錄（例如 \Program 檔\\）所需的程式。  
  
##### <a name="to-enforce-installation-by-administrator"></a>若要強制安裝系統管理員  
  
1. 開啟安裝專案的快捷方式功能表，然後選擇 [**屬性**]。  
  
2. 在 [設定**屬性/連結器/資訊清單**檔案] 下，將 [ **UAC 執行層級**] 設為**requireAdministrator**。  
  
     這個屬性會將要求以系統管理員身分執行程式的屬性放入內嵌的資訊清單檔中。  
  
### <a name="detecting-shell-installations"></a>偵測 Shell 安裝  
 若要判斷是否必須安裝 Visual Studio Shell （獨立模式），請先檢查 HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install. 的登錄值，判斷是否已經安裝它。  
  
> [!NOTE]
> Wsmanconfig.wxs 專案中的 Shell 偵測區塊也會讀取這些值。  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder 指定安裝 Visual Studio Shell 的位置，您可以在該處檢查檔案。  
  
 如需如何偵測 Shell 安裝的範例，請參閱 Shell 部署範例中的 `GetProductDirFromReg` 的公用程式函式。  
  
 如果電腦上未安裝套件所需的其中一個或兩個 Visual Studio Shell，您必須將它們新增至要安裝的元件清單。 如需範例，請參閱 Shell 部署範例中 ComponentsPage 的 `ComponentsPage::OnInitDialog` 功能。  
  
### <a name="running-the-shell-installers"></a>執行 Shell 安裝程式  
 若要執行 Shell 安裝程式，請使用正確的命令列引數呼叫 Visual Studio Shell 可轉散發套件。 您至少必須使用命令列引數 **/norestart/q** ，並監看傳回碼以判斷接下來應執行的動作。 下列範例會執行 Shell （獨立模式）可轉散發套件。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>執行 Shell 語言套件安裝程式  
 如果您改為發現已安裝 shell 或 shell，而且只需要語言套件，您可以安裝語言套件，如下列範例所示。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>解密傳回值  
 在某些作業系統上，Visual Studio Shell （獨立模式）安裝將需要重新開機。 這個條件可以由呼叫的傳回碼來決定 `ExecCmd`。  
  
|傳回值|描述|  
|------------------|-----------------|  
|ERROR_SUCCESS|安裝已完成。 您現在可以安裝您的應用程式。|  
|ERROR_SUCCESS_REBOOT_REQUIRED|安裝已完成。 重新開機電腦之後，您就可以安裝應用程式。|  
|3015|安裝正在進行中。 需要重新開機電腦，才能繼續安裝。|  
  
### <a name="handling-restarts"></a>處理重新開機  
 當您使用 **/norestart**引數執行 Shell 安裝程式時，指定它不會重新開機電腦或要求重新開機電腦。 不過，可能需要重新開機，而且您必須在重新開機電腦之後，確保安裝程式繼續進行。  
  
 若要正確地處理重新開機，請確定只有一個安裝程式已設定為 [繼續]，而且會正確處理繼續處理。  
  
 如果傳回 ERROR_SUCCESS_REBOOT_REQUIRED 或3015，您的程式碼應該先重新開機電腦，安裝才會繼續進行。  
  
 若要處理重新開機，請執行下列動作：  
  
- 設定登錄以在 Windows 啟動時繼續安裝。  
  
- 執行啟動載入器的雙重開機。  
  
- 刪除 Shell 安裝程式 ResumeData 鍵。  
  
- 重新開機 Windows。  
  
- 重設 MSI 的開始路徑。  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>設定登錄以在 Windows 啟動時繼續安裝程式  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ 登錄機碼會在系統啟動時，以系統管理許可權執行，然後再清除。 HKEY_CURRENT_USER 包含類似的索引鍵，但它是以一般使用者的身分執行，並不適用于安裝。 您可以將字串值放在呼叫安裝程式的 RunOnce 索引鍵中，以繼續安裝。 不過，我們建議您使用 **/restart**或類似的參數來呼叫安裝程式，以通知應用程式正在繼續而不是啟動。 您也可以包含參數來指出您在安裝程式中的位置，這在可能需要多次重新開機的安裝中特別有用。  
  
 下列範例顯示繼續安裝的 RunOnce 登錄機碼值。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>安裝啟動載入器的雙重開機  
 如果直接從 RunOnce 使用安裝程式，桌面將無法完全載入。 若要讓完整的使用者介面可供使用，您必須建立另一個執行的安裝程式，並結束 RunOnce 實例。  
  
 您必須重新執行安裝程式，使其取得正確的許可權，而且您必須提供足夠的資訊來知道您在重新開機之前停止的位置，如下列範例所示。  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>刪除 Shell 安裝程式 ResumeData 機碼  
 Shell 安裝程式會使用資料設定 HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData 登錄機碼，以在重新開機後繼續安裝程式。 因為您的應用程式（而非 Shell 安裝程式）正在繼續，所以請刪除該登錄機碼，如下列範例所示。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>重新開機 Windows  
 設定必要的登錄機碼之後，您可以重新開機 Windows。 下列範例會叫用不同 Windows 作業系統的重新開機命令。  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>重設 MSI 的起始路徑  
 在重新開機之前，目前的目錄是安裝程式的位置，但在重新開機之後，位置會變成 system32 目錄。 在每個 MSI 呼叫之前，您的安裝程式應該重設目前的目錄，如下列範例所示。  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>正在執行應用程式 MSI  
 Visual Studio Shell 安裝程式傳回 ERROR_SUCCESS 之後，您就可以執行應用程式的 MSI。 因為您的安裝程式會提供使用者介面，請以無訊息模式（ **/q**）和記錄（ **/l**）啟動您的 MSI，如下列範例所示。  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰建立基本的 Isolated Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
