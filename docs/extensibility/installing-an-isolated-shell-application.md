---
redirect_url: shell/installing-an-isolated-shell-application
title: "安裝獨立的 Shell 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fffbe31d9d5919c1e8b94482556c851fc07a1750
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="installing-an-isolated-shell-application"></a>安裝獨立的 Shell 應用程式
若要安裝的殼層應用程式中，您必須執行下列步驟。  
  
-   準備您的方案。  
  
-   建立您的應用程式的 Windows Installer (MSI) 封裝。  
  
-   建立安裝程式啟動載入器。  
  
 所有的這份文件的範例程式碼來自[殼層部署範例](http://go.microsoft.com/fwlink/?LinkId=262245)，您可以從 MSDN 網站上的程式碼庫下載。 此範例會示範執行每個步驟的結果。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題描述的程序，必須在電腦上安裝下列工具。  
  
-   Visual Studio SDK  
  
-   [Windows Installer XML 工具組](http://go.microsoft.com/fwlink/?LinkId=82720)3.6 版  
  
 此範例也會要求 Microsoft Visualization and Modeling SDK，並非所有的殼層需要。  
  
## <a name="preparing-your-solution"></a>準備您的方案  
 根據預設，殼層範本建置至 VSIX 封裝，但是這種行為主要供偵錯之用。 當您部署 Shell 應用程式時，您必須登錄存取和重新啟動允許在安裝期間使用的 MSI 封裝。 若要準備您的應用程式的 MSI 部署，執行下列步驟。  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>若要準備 MSI 部署的殼層應用程式  
  
1.  編輯您的方案中每個的.vsixmanifest 檔案。  
  
     在`Identifier`項目，加入`InstalledByMSI`項目和`SystemComponent`項目，然後將其值設定為`true`。  
  
     這些項目可防止 VSIX 安裝程式嘗試從解除安裝的狀況使用安裝程式元件和使用者**擴充功能和更新** 對話方塊。  
  
2.  編輯包含 VSIX 資訊清單的每個專案，建置工作輸出的位置，將從中安裝程式 MSI 的內容。 VSIX 資訊清單包含在組建輸出中，但不建置.vsix 檔案。  
  
## <a name="creating-an-msi-for-your-shell"></a>建立您的 Shell MSI  
 若要建置 MSI 套件，我們建議您使用[Windows Installer XML 工具組](http://go.microsoft.com/fwlink/?LinkId=82720)因為它提供更大的彈性比標準的安裝專案。  
  
 在 Product.wxs 檔案中，設定偵測區塊和 Shell 元件的配置。  
  
 在您方案的.reg 檔案和 ApplicationRegistry.wxs 中，然後建立登錄項目。  
  
### <a name="detection-blocks"></a>偵測區塊  
 偵測區塊組成`Property`項目，指定偵測到的必要條件和`Condition`項目，指定要傳回如果必要條件不存在電腦上的訊息。 例如，殼層應用程式就需要 Microsoft Visual Studio Shell 可轉散發套件，並偵測區塊會類似下列的標記。  
  
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
  
### <a name="layout-of-shell-components"></a>殼層元件的配置  
 您必須加入元素，以識別的目標目錄結構和要安裝的元件。  
  
##### <a name="to-set-the-layout-of-shell-components"></a>若要設定殼層元件的配置  
  
1.  建立階層`Directory`項目來代表所有要在系統上建立檔案的目標電腦上，如下列範例所示的目錄。  
  
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
  
     這些目錄由參考`Id`時指定的檔案，必須先安裝。  
  
2.  識別殼層和 Shell 應用程式需要，如下列範例所示的元件。  
  
    > [!NOTE]
    >  某些項目可能會參考其他.wxs 檔案中定義。  
  
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
  
    1.  `ComponentRef`元素會識別目前的元件所需之檔案的另一個.wxs 檔案參考。 例如，GeneralProfile 具有下列定義 HelpAbout.wxs 中。  
  
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
  
         `DirectoryRef`項目會指定這些檔案在使用者電腦上的位置。 `Directory`項目會指定，將會安裝到子目錄中，而每一個`File`元素代表內建或之方案的一部分並找出該檔案可以找到時建立 MSI 檔案的檔案。  
  
    2.  `ComponentGroupRef`元素參考的其他元件 （或元件與元件群組） 的群組。 比方說， `ComponentGroupRef` ApplicationGroup 下定義，如下所示 Application.wxs 中。  
  
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
    >  所需的 Shell （獨立模式） 的應用程式相依性： DebuggerProxy，MasterPkgDef，資源 （特別是.winprf 檔案），應用程式，以及 PkgDefs。  
  
### <a name="registry-entries"></a>登錄項目  
 Shell （獨立模式） 的專案範本包含*ProjectName*.reg 檔案合併安裝上的登錄機碼。 這些登錄項目必須是安裝和清除用途的 MSI 的一部分。 您也必須建立比對登錄區塊 ApplicationRegistry.wxs 中。  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>若要整合到 MSI 的登錄項目  
  
1.  在**Shell Customization**資料夾中，開啟*ProjectName*。 註冊  
  
2.  所有執行個體 $RootFolder$ 語彙基元取代目標安裝目錄的路徑。  
  
3.  新增應用程式所需的任何其他登錄項目。  
  
4.  開啟 ApplicationRegistry.wxs。  
  
5.  每個登錄項目中*ProjectName*.reg，加入對應的登錄區塊，如下列範例所示。  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @="PhotoStudio DTE 物件 」|\<RegistryKey Id = 'DteClsidRegKey' 根 = 'HKCR' Key =' $(varDteClsidRegKey)' 動作 = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue 類型 = 'string' Name =' @' 值 =' $(varShortProductName) DTE 物件 ' / ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id = 'DteLocSrv32RegKey' 根 = 'HKCR' Key =' $(varDteClsidRegKey) \LocalServer32' 動作 = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue 類型 = 'string' Name =' @' 值 ='[INSTALLDIR] $(varShortProductName).exe ' / ><br /><br /> \</ RegistryKey >|  
  
     在此範例中，Var.DteClsidRegKey 會解析為頂端列中的登錄機碼。 Var.ShortProductName 解析成`PhotoStudio`。  
  
## <a name="creating-a-setup-bootstrapper"></a>建立安裝程式啟動載入器  
 只有當第一次安裝所有必要元件，將會安裝您已完成的 MSI。 若要簡化使用者經驗，建立安裝程式會收集並安裝您的應用程式之前先安裝所有必要條件。 若要確保安裝成功，執行下列動作：  
  
-   強制執行由系統管理員的安裝。  
  
-   偵測是否已安裝 Visual Studio Shell （隔離式）。  
  
-   順序執行一或兩個介面安裝程式。  
  
-   處理重新啟動要求。  
  
-   執行 MSI。  
  
### <a name="enforcing-installation-by-administrator"></a>強制執行由系統管理員的安裝  
 此程序，才能讓安裝程式，以存取所需的目錄，例如 \Program Files\\。  
  
##### <a name="to-enforce-installation-by-administrator"></a>若要強制執行由系統管理員的安裝  
  
1.  開啟安裝專案的捷徑功能表，然後選擇**屬性**。  
  
2.  在下**組態屬性/連結器/資訊清單檔**，將**UAC 執行層級**至**requireAdministrator**。  
  
     這個屬性會將要求至內嵌資訊清單檔案，系統管理員身分執行程式的屬性。  
  
### <a name="detecting-shell-installations"></a>偵測殼層安裝  
 若要判斷是否必須安裝 Visual Studio Shell （隔離式），請先判斷是否已安裝檢查的 HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install 的登錄值。  
  
> [!NOTE]
>  Product.wxs 的殼層偵測區塊也會讀取這些值。  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder 指定已安裝 Visual Studio Shell，和您可以檢查檔案的位置。  
  
 如需如何偵測殼層安裝的範例，請參閱`GetProductDirFromReg`Utilities.cpp 殼層部署範例中的函式。  
  
 如果一或兩個封裝所需的 Visual Studio Shell 未安裝在電腦上，您必須將他們加入您要安裝元件的清單。 如需範例，請參閱`ComponentsPage::OnInitDialog`ComponentsPage.cpp 殼層部署範例中的函式。  
  
### <a name="running-the-shell-installers"></a>執行殼層安裝程式  
 若要執行的 Shell 安裝程式，請使用正確的命令列引數呼叫 Visual Studio Shell 可轉散發套件。 最少，您必須使用命令列引數**/norestart /q**查看傳回的程式碼，以判斷應該要如何處理下一步。 下列範例會執行 Shell （獨立模式） 可轉散發套件。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>執行 Shell 語言套件安裝程式  
 如果您改為尋找已安裝殼層，只需要語言套件，您可以安裝語言套件，如下列範例所示。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>解密傳回值  
 在某些作業系統上的 Visual Studio Shell （獨立模式） 安裝將需要重新啟動。 您可以呼叫的傳回碼來判斷此條件`ExecCmd`。  
  
|傳回值|描述|  
|------------------|-----------------|  
|ERROR_SUCCESS|安裝已完成。 您現在可以安裝您的應用程式。|  
|ERROR_SUCCESS_REBOOT_REQUIRED|安裝已完成。 重新啟動電腦之後，您可以安裝您的應用程式。|  
|3015|安裝正在進行中。 重新啟動電腦才能繼續安裝。|  
  
### <a name="handling-restarts"></a>處理重新啟動  
 當您執行介面安裝程式使用**/norestart**引數，您指定它不會重新啟動電腦，或要求重新啟動電腦。 不過，可能需要重新啟動，而且您必須確定在重新啟動電腦之後，繼續執行您的安裝程式。  
  
 若要正確處理重新啟動，請確定只有一個安裝程式會設為繼續執行而繼續處理序會正確處理。  
  
 如果傳回 ERROR_SUCCESS_REBOOT_REQUIRED 或 3015 時，您的程式碼應該重新啟動電腦才能繼續安裝。  
  
 若要處理重新啟動時，執行下列動作：  
  
-   設定登錄以 Windows 啟動時，繼續安裝。  
  
-   執行兩個重新啟動的啟動載入器。  
  
-   刪除殼層 installer ResumeData 機碼。  
  
-   重新啟動 Windows。  
  
-   重設啟動路徑的 MSI。  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>設定登錄以 Windows 啟動時，繼續安裝程式  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ 登錄機碼在系統啟動時，使用系統管理權限執行，並接著會被清除。 HKEY_CURRENT_USER 包含類似的金鑰，但是一般使用者身分執行，並不適用於安裝。 將字串值放在您的安裝程式會呼叫 RunOnce 索引鍵，即可繼續安裝。 不過，我們建議您藉由呼叫安裝程式**/重新啟動**或類似的參數，以通知它正在繼續執行而不啟動應用程式。 您也可以包含參數，表示要在安裝過程中，可能需要多個重新啟動的安裝中特別有用。  
  
 下列範例會示範 RunOnce 登錄機碼值繼續安裝。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>安裝雙重新啟動的啟動載入器  
 如果安裝程式會用於直接從 RunOnce，桌面將無法完全載入。 若要使用完整使用者介面，您必須建立另一部執行安裝程式，並結束 RunOnce 執行個體。  
  
 您必須重新執行安裝程式，而它會取得正確的權限，您必須提供足夠資訊知道您的停止處之前重新啟動，如下列範例所示。  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>正在刪除殼層 Installer ResumeData 金鑰  
 介面安裝程式會設定 HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData 登錄機碼，以重新啟動後繼續執行安裝程式的資料。 因為您的應用程式不是殼層安裝程式，正在繼續執行，請刪除該登錄機碼，如下列範例所示。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>重新啟動 Windows  
 設定所需的登錄機碼之後，您可以重新啟動 Windows。 下列範例會叫用不同的 Windows 作業系統的重新啟動命令。  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>重設 MSI 的啟動路徑  
 之前重新啟動時，目前的目錄是您的安裝程式的位置，但是重新啟動之後，位置會變成 system32 目錄。 安裝程式應如下列範例所示，重設每個 MSI 呼叫之前，目前的目錄。  
  
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
  
### <a name="running-the-application-msi"></a>執行 MSI 的應用程式  
 Visual Studio Shell 安裝程式傳回 ERROR_SUCCESS 之後，您可以執行您的應用程式的 MSI。 因為您的安裝程式提供使用者介面時，啟動程式 MSI 以無訊息模式 (**/q**) 與記錄 (**/L**)，如下列範例所示。  
  
```cpp  
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
  
## <a name="see-also"></a>請參閱  
 [逐步解說︰建立基本的 Isolated Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)