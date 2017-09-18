---
title: "安裝獨立的 Shell 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell [Visual Studio]，將命令介面為基礎的應用程式部署"
  - "Visual Studio shell，部署命令介面為基礎的應用程式"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 40
---
# 安裝獨立的 Shell 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要安裝的殼層應用程式中，您必須執行下列步驟。  
  
-   準備您的方案。  
  
-   建立您的應用程式的 Windows Installer \(MSI\) 封裝。  
  
-   建立安裝程式啟動載入器。  
  
 本文件中的範例程式碼的所有來自 [Shell 部署範例](http://go.microsoft.com/fwlink/?LinkId=262245), ，您可以從 MSDN 網站上的程式碼庫。 此範例會顯示執行這些步驟的結果。  
  
## 必要條件  
 若要執行本主題所描述的程序，必須在電腦上安裝下列工具。  
  
-   Visual SDK Studio  
  
-   [Windows Installer XML 工具組](http://go.microsoft.com/fwlink/?LinkId=82720) 3.6 版  
  
 此範例也會要求 Microsoft Visualization and Modeling SDK，並非所有的 shell 需要。  
  
## 準備您的方案  
 根據預設，殼層範本建置 VSIX 套件，但是這個問題主要供偵錯之用。 當您部署殼層應用程式時，您必須使用 MSI 封裝安裝期間允許登錄存取以及重新啟動。 若要準備您的應用程式的 MSI 部署，請執行下列步驟。  
  
#### 若要準備 MSI 部署的殼層應用程式  
  
1.  編輯您的方案中每個.vsixmanifest 檔案。  
  
     在 `Identifier` 項目，加入 `InstalledByMSI` 項目和 `SystemComponent` 項目，然後將其值設定為 `true`。  
  
     這些項目避免 VSIX 安裝程式嘗試從它們使用 \[解除安裝安裝程式元件和使用者 **擴充功能和更新** 對話方塊。  
  
2.  編輯檔案包含 VSIX 資訊清單的每個專案，建置工作的輸出的位置從中安裝 MSI 的內容。 VSIX 資訊清單中包含組建輸出，但是不建立.vsix 檔案。  
  
## 為您的 Shell 建立 MSI  
 若要建置 MSI 套件，我們建議您使用 [Windows Installer XML 工具組](http://go.microsoft.com/fwlink/?LinkId=82720) 因為它提供更大的彈性比標準的安裝專案。  
  
 在 Product.wxs 檔案中，設定偵測區塊和殼層元件的版面配置。  
  
 在您方案的.reg 檔案和 ApplicationRegistry.wxs 中，然後建立登錄項目。  
  
### 偵測區塊  
 偵測區塊組成 `Property` 項目，指定偵測到的必要條件和 `Condition` 項目，指定要傳回之必要條件並不存在於電腦上的訊息。 例如，殼層應用程式所需 Microsoft Visual Studio Shell 可轉散發套件，並偵測區塊會類似下列的標記。  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### 殼層元件的版面配置  
 您必須加入項目來識別目標目錄結構與要安裝的元件。  
  
##### 若要設定殼層元件的版面配置  
  
1.  建立的階層 `Directory` 項目來代表所有要在系統上建立檔案的目標電腦上，如下列範例所示的目錄。  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     這些目錄由參考 `Id` 時指定的檔案，必須先安裝。  
  
2.  識別命令介面與殼層應用程式需要，如下列範例所示的元件。  
  
    > [!NOTE]
    >  某些項目可以參考其他.wxs 檔案中定義。  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  `ComponentRef` 項目是指識別目前的元件所需之檔案的另一個.wxs 檔案。 例如，GeneralProfile 具有下列定義 HelpAbout.wxs 中。  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         `DirectoryRef` 項目會指定在使用者電腦上這些檔案在哪裡。`Directory` 項目會指定它將會安裝到子目錄，而每一個 `File` 項目代表內建或，方案的一部分，並識別該檔案可以找到時建立 MSI 檔案的檔案。  
  
    2.  `ComponentGroupRef` 項目是指一群其他元件 \(元件或元件群組\)。 比方說， `ComponentGroupRef` ApplicationGroup 下定義，如下所示 Application.wxs 中。  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  必要 Shell \(獨立模式\) 應用程式相依性: DebuggerProxy，MasterPkgDef，資源 \(尤其是.winprf 檔案\)，應用程式和 PkgDefs。  
  
### 登錄項目  
 Shell \(獨立模式\) 專案範本包括 *ProjectName*合併安裝上的登錄機碼的.reg 檔案。 這些登錄項目必須是安裝和清除用途的 MSI 的一部分。 您也必須在 ApplicationRegistry.wxs 建立比對登錄區塊。  
  
##### 若要整合到 MSI 的登錄項目  
  
1.  在 **Shell 自訂** 資料夾中，開啟 *ProjectName*。.reg  
  
2.  目標安裝目錄的路徑取代 $RootFolder$ 語彙基元的所有執行個體。  
  
3.  新增應用程式所需的任何其他登錄項目。  
  
4.  開啟 ApplicationRegistry.wxs。  
  
5.  在每個登錄項目的 *ProjectName*.reg，加入對應的登錄區塊，如下列範例所示。  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= 「 PhotoStudio DTE 物件 」|\< 登錄機碼識別碼 \= 'DteClsidRegKey' Root \= 'HKCR' Key \=' $\(var。DteClsidRegKey\)' 動作 \= 'createAndRemoveOnUninstall' \><br /><br /> \< RegistryValue 類型 \= 'string' Name \=' @' 值 \=' $\(var。ShortProductName\) DTE 物件 ' \/ \><br /><br /> \< \/ 登錄機碼 \>|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6} \\LocalServer32\]<br /><br /> @\="$RootFolder$\\PhotoStudio.exe"|\< 登錄機碼識別碼 \= 'DteLocSrv32RegKey' Root \= 'HKCR' Key \=' $\(var。DteClsidRegKey\) \\LocalServer32' 動作 \= 'createAndRemoveOnUninstall' \><br /><br /> \< RegistryValue 類型 \= 'string' Name \=' @' 值 \='\[INSTALLDIR\] $\(var。ShortProductName\).exe ' \/ \><br /><br /> \< \/ 登錄機碼 \>|  
  
     在此範例中，Var.DteClsidRegKey 會解析為頂端列中的登錄機碼。 Var.ShortProductName 會解析為 `PhotoStudio`。  
  
## 建立安裝程式的啟動載入器  
 只有當第一次安裝所有必要條件，將會安裝您已完成的 MSI。 若要簡化使用者經驗，建立安裝程式會收集您的應用程式安裝之前先安裝所有必要條件。 若要確保安裝成功之後，執行下列動作:  
  
-   強制執行安裝的系統管理員。  
  
-   偵測是否已安裝 Visual Studio Shell \(獨立模式\)。  
  
-   順序執行一或兩個介面安裝程式。  
  
-   處理重新啟動要求。  
  
-   執行 MSI。  
  
### 強制執行系統管理員安裝  
 此程序，才能讓安裝程式來存取所需的目錄，例如 files\\。  
  
##### 若要強制執行系統管理員安裝  
  
1.  開啟安裝專案的捷徑功能表，然後選擇 **屬性**。  
  
2.  在 **組態資訊清單屬性\/連結器檔案**, ，請將 **UAC 執行層級** 至 **requireAdministrator**。  
  
     這個屬性會將要求至內嵌資訊清單檔案，系統管理員身分執行程式的屬性。  
  
### 偵測殼層安裝  
 若要判斷是否必須安裝 Visual Studio Shell \(獨立模式\)，請先判斷是否已安裝方式是檢查登錄值的 HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Install。  
  
> [!NOTE]
>  Product.wxs 的殼層偵測區塊也會讀取這些值。  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder 指定已安裝 Visual Studio Shell，及您可以檢查檔案的位置。  
  
 如何偵測殼層安裝的範例，請參閱 `GetProductDirFromReg` Utilities.cpp Shell 部署範例中的函式。  
  
 如果其中一個或多個封裝所需的 Visual Studio Shell 未安裝在電腦上，您必須將它們加入您要安裝元件的清單。 如需範例，請參閱 `ComponentsPage::OnInitDialog` ComponentsPage.cpp Shell 部署範例中的函式。  
  
### 執行的命令介面安裝程式  
 若要執行的命令介面安裝程式，請使用正確的命令列引數呼叫 Visual Studio Shell 可轉散發套件。 至少，您必須使用命令列引數 **\/norestart \/q** ，並觀察傳回的程式碼，以判斷應該要如何處理下一步。 下列範例會執行 Shell \(獨立模式\) 可轉散發套件。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### 執行 Shell 語言套件安裝程式  
 如果您改為尋找已安裝的殼層，只需要語言套件，您可以安裝語言套件，如下列範例所示。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### 解密傳回值  
 在某些作業系統上安裝 Visual Studio Shell \(獨立模式\) 將會需要重新啟動。 這種情況可藉由呼叫的傳回碼 `ExecCmd`。  
  
|傳回值|描述|  
|---------|--------|  
|ERROR\_SUCCESS|安裝已完成。 您現在可以安裝您的應用程式。|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|安裝已完成。 重新啟動電腦之後，您可以安裝您的應用程式。|  
|3015|安裝正在進行中。 重新啟動電腦才能繼續安裝。|  
  
### 處理重新啟動  
 當您執行介面安裝程式使用 **\/norestart** 引數，您指定它不會重新啟動電腦，或要求重新啟動電腦。 不過，可能需要重新啟動，而且您必須確定在重新啟動電腦之後，繼續執行安裝程式。  
  
 若要正確處理重新啟動，請確定該只有一個安裝程式會設為繼續執行而繼續處理序會正確處理。  
  
 如果傳回 ERROR\_SUCCESS\_REBOOT\_REQUIRED 或 3015 時，您的程式碼應該重新啟動電腦才能繼續安裝。  
  
 若要處理重新啟動時，執行下列動作:  
  
-   設定登錄以 Windows 啟動時，繼續安裝。  
  
-   執行雙重新啟動的啟動載入器。  
  
-   刪除介面安裝程式 ResumeData 機碼。  
  
-   重新啟動 Windows。  
  
-   重設啟動路徑的 MSI。  
  
### 設定登錄，以繼續設定 Windows 啟動時  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ 登錄機碼在系統啟動時，使用系統管理權限執行，則會清除。HKEY\_CURRENT\_USER 包含類似的索引鍵，但它以一般使用者身分執行，並不適合用於安裝。 將字串值放在您的安裝程式會呼叫 runonce 機碼中，您可以繼續安裝。 不過，我們建議您藉由呼叫安裝程式 **\/restart** 或類似的參數，以通知它正在繼續而不啟動應用程式。 您也可以包含參數，表示要在安裝過程中，特別適用於安裝可能需要多次重新啟動。  
  
 下列範例顯示用於繼續安裝的 RunOnce 登錄機碼值。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### 安裝雙重新啟動的啟動載入器  
 如果安裝程式使用直接從 RunOnce，桌面無法完全載入。 若要使用完整使用者介面，您必須建立另一個執行安裝程式，並結束 RunOnce 的執行個體。  
  
 您必須重新執行安裝程式，使它會取得正確的權限，您必須提供足夠資訊知道您的停止處之前重新啟動，如下列範例所示。  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### 刪除介面安裝程式 ResumeData 機碼  
 殼層安裝程式將 HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData 登錄機碼重新啟動後繼續執行安裝程式的資料。 因為您的應用程式不是介面安裝程式，繼續時，刪除該登錄機碼，如下列範例所示。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### 重新啟動 Windows  
 設定所需的登錄機碼之後，您可以重新啟動 Windows。 下列範例會叫用不同的 Windows 作業系統的重新啟動命令。  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### 重設 MSI 的啟動的路徑  
 之前重新啟動時，目前的目錄是您的安裝程式的位置，但重新啟動之後，位置會成為 system32 目錄。 安裝程式應該重設每個 MSI 呼叫之前，目前的目錄，如下列範例所示。  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### 執行 MSI 的應用程式  
 Visual Studio Shell 安裝程式會傳回 ERROR\_SUCCESS 之後，您可以執行 MSI 應用程式。 因為您的安裝程式會提供使用者介面，以無訊息模式中啟動 MSI \(**\/q**\) 和記錄 \(**\/L**\)，如下列範例所示。  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## 請參閱  
 [逐步解說: 建立基本的獨立的 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)