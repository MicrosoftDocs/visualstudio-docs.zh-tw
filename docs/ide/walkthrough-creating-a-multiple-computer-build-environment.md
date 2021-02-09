---
title: 建立多電腦建置環境
description: 在主機電腦上安裝 Visual Studio，然後將各種檔案和設定複製到另一部電腦，以在組織內建立組建環境。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ae0e5f2516dd1f78aea880289f549ca3a44f3bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881954"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>逐步解說：建立多電腦建置環境

您可以在組織內建立建置環境，方法是在主機電腦上安裝 Visual Studio，然後將各種檔案和設定複製到另一部電腦，以便該電腦可參與建置。 您不需要在另一部電腦上安裝 Visual Studio。

本文件並不會授權在外部轉散發軟體，或將建置環境提供給第三方。

> 免責聲明<br /><br /> 本文件係依「原樣」提供。 雖然我們已測試過所述的步驟，但無法徹底測試每一種組態。 我們將試圖以學到的任何其他資訊，確保文件處於最新狀態。 本文件中說明的資訊與畫面 (包括 URL 及其他網際網路網站參考資料) 如有變更，恕不另行通知。 Microsoft 對此處提供的資訊，不做任何明確或隱含的瑕疵擔保。 貴用戶須自行承擔使用風險。<br /><br /> 本文件不為您提供對任何 Microsoft 產品中的任何智慧財產的法定權利。 您可以複製本文件供內部參照之用。<br /><br /> 貴用戶沒有義務提供與本文件相關的任何建議、意見或其他意見反應 (「意見反應」) 給 Microsoft。 不過，貴用戶自願提供的任何意見反應可能會用於 Microsoft 產品以及相關規格或其他文件 (統稱為「Microsoft 供應項目」)，之後可能會由其他第三方用來開發自己的產品。 因此，如果　貴用戶針對本文件的任何版本提供 Microsoft 意見反應或套用意見反應的 Microsoft 供應項目，即表示　貴用戶同意：(a) Microsoft 可以在任何 Microsoft 供應項目中，自由地使用、重製、授權、散發或商業化意見反應；(b) 貴用戶也免費授權給第三方，這些權利僅限於讓其他產品使用或連接到納入意見反應的 Microsoft 產品之任何特定部分所需的專利權；以及 (c) 在下列情況下，貴用戶不會提供 Microsoft 任何意見反應，以授權或分享給任何第三方：(i) 貴用戶合理相信這些意見反應受限於任何第三方的任何專利、著作權或其他智慧財產權宣告或權利；或是 (ii) 受限於試圖要求納入或衍生自這類意見反應之任何 Microsoft 供應項目的授權條款，或其他 Microsoft 智慧財產權。

本逐步解說已對下列作業系統驗證過：

- Windows 8 (x86 和 x64)
- Windows 7 旗艦版
- Windows Server 2008 R2 Standard

完成本逐步解說中的步驟之後，您可以使用多電腦環境來建置下列應用程式類型：

- 使用 Windows 8 SDK 的 C++ 傳統型應用程式
- 以 .NET Framework 4.5 為目標的 Visual Basic 或 C# 傳統型應用程式

您無法使用多電腦環境來建置下列應用程式類型：

- UWP 應用程式。 若要建置 UWP 應用程式，您必須在建置電腦上安裝 Visual Studio。
- 以 .NET Framework 4 (含) 以前版本為目標的傳統型應用程式。 若要建置這些應用程式類型，您必須在組建電腦上安裝 Visual Studio 或 .NET 參考組件和工具 (從 Windows 7.1 SDK)。

## <a name="prerequisites"></a>必要條件

已安裝 [.NET 桌面開發] 工作負載的 Visual Studio。

## <a name="install-software-on-the-computers"></a>在電腦上安裝軟體

首先設定主機電腦，然後設定建置電腦。

您會藉由在主機電腦上安裝 Visual Studio，建立稍後將複製到組建電腦的檔案和設定。 您可以在 x86 或 x64 電腦上安裝 Visual Studio，但組建電腦的架構必須符合主機電腦的架構。

1. 在主機電腦上，安裝 Visual Studio。

2. 在建置電腦上，安裝 .NET Framework 4.5 或更新版本。 若要確認已安裝，請檢查登錄子機碼 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 中 [Version] 項目的值是否為 [4.5] 或更高。

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>將檔案從主機電腦複製到組建電腦

本節說明如何將特定檔案、編譯器、建置工具、MSBuild 資產和登錄設定從主機電腦複製到組建電腦。 這些指示假設您已在主機電腦上的預設位置安裝 Visual Studio；如果您安裝在其他位置，請據以調整步驟。

- 在 x86 電腦上，預設位置為 *C:\Program Files\Microsoft Visual Studio*
- 在 x64 電腦上，預設位置為 *C:\Program Files (x86)\Microsoft Visual Studio*

請注意，*Program Files* 資料夾的名稱取決於所安裝的作業系統。 在 x86 電腦上，此名稱會是 *Program Files*；在 x64 電腦上，此名稱會是 *Program Files (x86)*。 不論系統架構為何，本逐步解說會將 *Program Files* 資料夾稱為 *%ProgramFiles%*。

> [!NOTE]
> 在組建電腦中，所有相關檔案都必須位於相同的磁碟機上。 不過，該磁碟機的磁碟機代號可能會與安裝在主機電腦之 Visual Studio 磁碟機的磁碟機代號不同。 在任何情況下，當您建立登錄項目時，您必須考慮檔案的位置，如本文件稍後所述。

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>將 Windows SDK 檔案複製到組建電腦

1. 如果您只安裝 Windows 8 的 Windows SDK，請將下列資料夾從主機電腦遞迴複製到組建電腦：

   - %ProgramFiles%\Windows Kits\8.0\bin\

   - %ProgramFiles%\Windows Kits\8.0\Catalogs\

   - %ProgramFiles%\Windows Kits\8.0\DesignTime\

   - %ProgramFiles%\Windows Kits\8.0\include\

   - %ProgramFiles%\Windows Kits\8.0\Lib\

   - %ProgramFiles%\Windows Kits\8.0\Redist\

   - %ProgramFiles%\Windows Kits\8.0\References\

   如果您還有下列其他 Windows 8 套件...

   - Microsoft Windows 評定及部署套件

   - Microsoft Windows 驅動程式套件

   - Microsoft Windows 硬體認證套件

   ...這些套件可能已將檔案安裝到上一個步驟所列的 *%ProgramFiles%\Windows Kits\8.0* 資料夾中，而且其授權條款可能不允許這些檔案的組建伺服器權限。 請檢查每個已安裝 Windows 套件的授權條款，以確認檔案是否可以複製到組建電腦。 如果授權條款不允許組建伺服器權限，則從組建電腦移除檔案。

2. 將下列資料夾從主機電腦遞迴複製到組建電腦：

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %ProgramFiles%\Common Files\Merge Modules\

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\

3. 將下列檔案從主機電腦複製到組建電腦：

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\vsvars32.bat

4. 下列 Visual C++ 執行階段程式庫只有在您於組建電腦上執行建置輸出時才需要，例如作為自動化測試的一部分。 這些檔案通常位於 *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\redist\x86* 或 *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\redist\x64* 資料夾下的子資料夾中，視系統架構而定。 在 x86 系統上，將 x86 二進位檔複製到 *Windows\System32* 資料夾。 在 x64 系統上，將 x86 二進位檔複製到 *Windows\SysWOW64* 資料夾，並將 x64 二進位檔複製到 *Windows\System32* 資料夾。

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. 只將下列檔案從 *Debug_NonRedist\x86* 或 *Debug_NonRedist\x64* 資料夾複製到組建電腦，如 [準備測試電腦以執行偵錯可執行檔](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)中所述。 不會複製其他任何檔案。

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>建立登錄設定

您必須建立登錄項目，才能進行 MSBuild 的設定。

1. 識別登錄項目的父資料夾。 所有登錄項目都會在相同的父機碼下建立。 在 x86 電腦上，父機碼會是 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**。 在 x64 電腦上，父機碼是 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft** 的。 不論系統架構為何，本逐步解說會將父機碼稱為 %RegistryRoot%。

    > [!NOTE]
    > 如果主機電腦的架構與組建電腦的架構不同，請務必在每部電腦上使用適當的父機碼。 如果您想要自動化匯出程序，這會特別重要。
    >
    > 此外，如果您想要在組建電腦上使用與主機電腦上所用不同的磁碟機代號，請務必變更要比對之登錄項目的值。

2. 在組建電腦上建立下列登錄項目。 所有項目都是字串 (登錄中的 Type == "REG_SZ")。 將這些項目的值設定為主機電腦上可比較項目的相同值。

   - **%RegistryRoot%\\.NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Default)**

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **%RegistryRoot%\VisualStudio\11.0@Source Directories**

   - <strong>%RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **%RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\Installed Roots@KitsRoot</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   在 x64 組建電腦上，同時建立下列登錄項目，並參考主機電腦，以判斷如何設定此項目。

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   如果您的建置電腦是 x64，而且您想要使用 64 位元版本的 MSBuild，或者如果您是在 x64 電腦上使用 Team Foundation Server 組建服務，請在原生 64 位元登錄中建立下列登錄項目。 請參考主機電腦，以判斷如何設定這些項目。

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>設定組建電腦上的環境變數

若要在組建電腦上使用 MSBuild，您必須設定 PATH 環境變數。 您可以使用 *vcvarsall.bat* 來設定變數，或手動加以設定。

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>使用 vcvarsall.bat 設定環境變數

在組建電腦上開啟 [**命令提示** 字元] 視窗，並執行 *% Program Files%\Microsoft Visual Studio \\ \<version> \\ \<edition>\VC\vcvarsall.bat*。 您可以使用命令列引數，指定要使用的工具組：x86、x64 Native 或 x64 Cross 編譯器。 如果您未指定命令列引數，則會使用 x86 工具組。

下表描述 *vcvarsall.bat* 支援的引數：

|Vcvarsall.bat 引數|編譯器|組建電腦架構|組建輸出架構|
| - |--------------| - | - |
|x86 (預設)|32 位元 Native|x86、x64|x86|
|x86_amd64|x64 Cross|x86、x64|x64|
|amd64|x64 Native|x64|x64|

如果 *vcvarsall.bat* 順利執行 (也就是未顯示任何錯誤訊息)，您可以略過下一個步驟，並繼續進行本文件的 [將 MSBuild 組件安裝到組建電腦上的全域組件快取 (GAC)](#install-msbuild-to-gac) 一節。

### <a name="manually-set-environment-variables"></a>手動設定環境變數

1. 若要手動設定命令列環境，將此路徑新增至 PATH 環境變數：

    - % Program Files%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE

2. 或者，您也可以將下列路徑新增至 PATH 變數，以更輕鬆地使用 MSBuild 來建置方案。

   如果您想要使用原生 32 位元 MSBuild，請將下列路徑新增至 PATH 變數：

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   如果您想要使用原生 64 位元 MSBuild，請將下列路徑新增至 PATH 變數：

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" /> 將 MSBuild 組件安裝到組建電腦上的全域組件快取 (GAC)

MSBuild 必須將一些額外的組件安裝到組建電腦上的 GAC。

1. 將下列組件從主機電腦複製到組建電腦。 因為這些組件將會安裝到 GAC，所以放在組建電腦上的位置並不重要。

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. 若要將組件安裝到 GAC，請在組建電腦上尋找 *gacutil.exe* (通常位於 %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\ 中)。 如果找不到此資料夾，請重複本逐步解說之[將檔案從主機電腦複製到組建電腦](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer)一節中的步驟。

     開啟具有系統管理權限的 [命令提示字元] 視窗，然後針對每個檔案執行此命令：

     **gacutil-i \<file>**

    > [!NOTE]
    > 組件可能需要重新開機，才能完整安裝到 GAC。

## <a name="build-projects"></a>建置專案

您可以使用 Azure Pipelines 來建置 Visual Studio 專案和方案，或者您可也在命令列建置它們。 當您使用 Azure Pipelines 建置專案時，它會叫用對應至系統架構的 MSBuild 可執行檔。 在命令列上，您可以使用 32 位元 MSBuild 或 64 位元 MSBuild，而且可以藉由設定 PATH 環境變數，或直接叫用特定架構的 MSBuild 可執行檔，來選擇 MSBuild 的架構。

若要在命令提示字元中使用 *msbuild.exe*，請執行下列命令；其中 *solution.sln* 是方案名稱的預留位置。

**msbuild** *solution.sln*

如需如何在命令列上使用 MSBuild 的詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)。

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>建立組建環境以使它能被簽入原始檔控制

您可以建立可部署到各種電腦的建置環境，而不需要對檔案進行 GAC 或修改登錄設定。 下列步驟只是完成此作業的一種方式。 請根據您的建置環境獨特的特性，來調整這些步驟。

> [!NOTE]
> 您必須停用累加建置，以免 *tracker.exe* 在建置期間擲回錯誤。 若要停用累加建置，請設定下列組建參數：
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. 在主機電腦上建立 *Depot* 目錄。

     這些步驟會將此目錄稱為 %Depot%。

2. 如本逐步解說的 [將檔案從主機電腦複製到組建電腦](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer)一節中所述，複製目錄和檔案，但改為貼到您剛才建立的 *%Depot%* 目錄下。 例如，從 *%ProgramFiles%\Windows Kits\8.0\bin* 複製到 *%Depot%\Windows Kits\8.0\bin*。

3. 將檔案貼到 *%Depot%* 之後，請進行下列變更：

    - 在 %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets、\Microsoft.Cpp.InvalidPlatforms.targets\\、\Microsoft.cppbuild.targets\\ 和 \Microsoft.CppCommon.targets\\ 中，將

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" 的每個執行個體變更

         to

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll"。

         先前的命名會依賴已進行 GAC 的組件。

    - 在 %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets 中，將

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" 的每個執行個體變更

         to

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll"。

4. 建立 *.props* 檔案 (例如 *Partner.AutoImports.props*)，並將該檔案放在含有專案之資料夾的根目錄中。 此檔案可用來設定變數，MSBuild 會使用這些變數來尋找各種資源。 如果變數不是由此檔案設定，則會由依賴登錄值的其他 *.props* 檔案和 *.targets* 檔案設定。 因為我們未設定任何登錄值，所以這些變數會是空白的，而且建置會失敗。 相反地，請將下列程式碼新增至 *Partner.AutoImports.props*：

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio\2017\Enterprise\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. 在每個專案檔中，於頂端的 `<Project Default Targets...>` 行之後新增下一行。

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. 變更命令列環境，如下所示：

    - 設定 Depot=「您在步驟 1 中建立的 Depot 目錄位置」

    - 設定 path=%path%;電腦上的 MSBuild 位置;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 15.0\Common7\IDE\

       如需原生 64 位元建置，請指向 64 位元版本的 MSBuild。

::: moniker-end

::: moniker range=">=vs-2019"

6. 變更命令列環境，如下所示：

    - 設定 Depot=「您在步驟 1 中建立的 Depot 目錄位置」

    - 設定 path=%path%;*電腦上的 MSBuild 位置*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 16.0\Common7\IDE\

       如需原生 64 位元建置，請指向 64 位元版本的 MSBuild。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [準備測試電腦以執行偵錯可執行檔](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [命令列參考](../msbuild/msbuild-command-line-reference.md)