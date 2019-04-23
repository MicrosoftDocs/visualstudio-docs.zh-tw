---
title: Devenv 命令列參數 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4eadb8c9553873f43ad9435ad43fae00f57affcb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050700"
---
# <a name="devenv-command-line-switches"></a>Devenv 命令列參數
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devenv 可讓您設定整合式開發環境 (IDE) 的各種選項，也可讓您從命令列建置、偵錯和部署專案。 使用這些參數透過指令碼或 .bat 檔案 (例如，夜間組建指令碼) 執行 IDE，或在特定組態中啟動 IDE。  
  
> [!NOTE]
>  針對組建相關工作，現在建議您使用 MSBuild，而不是 devenv。 如需詳細資訊，請參閱[命令列參考](../../msbuild/msbuild-command-line-reference.md)。  
  
> [!NOTE]
>  您必須以系統管理員身分執行 devenv，才能使用 [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) 和 [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) 參數。  
  
## <a name="devenv-switch-syntax"></a>Devenv 參數語法  
 根據預設，devenv 命令會將參數傳遞至 devenv.com 公用程式。  
  
 devenv.com 公用程式可透過標準系統資料流 (例如 `stdout` 和 `stderr`) 來傳遞輸出，並決定擷取輸出時的適當 I/O 重新導向 (例如，重新導向至 .txt 檔案)。 開頭為 `devenv.exe` 的命令可以使用相同的參數，但會將它們傳送至 devenv.exe 程式，並略過 devenv.com 公用程式。  
  
 `devenv` 參數的語法規則與其他 DOS 命令列公用程式的語法規則類似。 下列語法規則套用至所有 `devenv` 參數和其引數︰  
  
- 命令開始於 `devenv`。  
  
- 參數不區分大小寫。  
  
- 指定方案或專案時，第一個引數是方案檔或專案檔的名稱 (包括檔案路徑)。  
  
- 如果第一個引數不是方案檔或專案檔，則會使用適當的編輯器在 IDE 的新執行個體開啟該檔案。  
  
- 如果您提供專案檔名稱，而不是方案檔名稱，`devenv` 命令將會在專案檔的上層資料夾中搜尋同名的方案檔。 例如，`devenv /build myproject1.vbproj` 命令將會在上層資料夾中搜尋名為 "myproject1.sln" 的方案檔。  
  
    > [!NOTE]
    >  只能有一個參考此專案的方案檔應該位於其上層資料夾。 如果上層資料夾未包含參考此專案的方案檔，或上層資料夾包含兩個或多個參考此專案的方案檔，將會建立針對此專案命名並參考此專案的暫存方案檔。  
  
- 檔案路徑和檔名包括空格時，必須用雙引號 ("") 括住它們。 例如，"c:\project a\\"。  
  
- 在同一行的參數與引數之間插入一個空白字元。 例如，**devenv /log output.txt** 命令會開啟 IDE，並將該工作階段的所有記錄資訊輸出至 output.txt。  
  
- 您不能在 `devenv` 命令中使用模式比對語法命令。  
  
## <a name="devenv-switches"></a>Devenv 參數  
 使用下列命令列參數來顯示 IDE，並執行所述的工作。  
  
|命令列參數|說明|  
|-------------------------|-----------------|  
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|啟動 IDE，並執行指定的命令。|  
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|透過偵錯工具的控制，載入 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 可執行檔。 此參數不適用於 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 可執行檔。 如需詳細資訊，請參閱[在偵錯工具中自動啟動處理序](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)。|  
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) 或 `/l`|設定 IDE 的預設語言。 如果 Visual Studio 安裝中未包含指定的語言，則會忽略此設定。|  
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，並將所有活動記錄至記錄檔。|  
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) or `/r`|編譯並執行指定的方案。|  
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|編譯並執行指定的方案、執行方案時最小化 IDE，以及在方案完成執行之後關閉 IDE。|  
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|讓 IDE 使用 PATH、INCLUDE 和 LIB 環境變數進行 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 編譯，而不是 [選項] 對話方塊之 [專案] 選項的 [VC++ 目錄] 區段中所指定的設定。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](http://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4)。|  
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|在這個應用程式的作用中執行個體中開啟指定的檔案。 如果沒有作用中執行個體，則會以簡易視窗配置啟動新的執行個體。|  
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|啟動 Visual Studio IDE 的執行個體，而不需要載入指定的增益集。|  
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|以安全模式啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，並且只載入預設環境和服務，以及隨附的協力廠商套件版本。|  
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|清除想要避免 VSPackage 載入問題的使用者已新增至 VSPackage 的所有 SkipLoading 標記。|  
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|強制 Visual Studio 合併來自所有可用 Vspackage 的資源中繼資料 (其描述功能表、工具列和命令群組)。|  
  
 使用下列命令列參數來執行所述的工作。 這些命令列參數不會顯示 IDE。  
  
|命令列參數|說明|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|在 [命令提示字元] 視窗中顯示 devenv 參數的說明。<br /><br /> **Devenv /?**|  
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|根據所指定方案的組態，建置指定的方案或專案。<br /><br /> **Devenv myproj.csproj /build**|  
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|刪除 build 命令所建立的任何檔案，而不會影響原始程式檔。<br /><br /> **Devenv myproj.csproj /clean**|  
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|根據方案組態，建置方案，以及部署所需的檔案。<br /><br /> **Devenv myproj.csproj /deploy**|  
|[/Diff](../../ide/reference/diff.md)|比較兩個檔案。  接受四個參數：SourceFile、TargetFile、SourceDisplayName (選擇性)、TargetDisplayName (選擇性)。|  
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|註冊位於 *\<VisualStudioInstallDir>* \Common7\IDE\ProjectTemplates 或 *\<VisualStudioInstallDir>* \Common7\IDE\ItemTemplates 中的專案或項目範本，以透過 [新增專案] 和 [新增項目] 對話方塊存取它們。<br /><br /> **Devenv /InstallVSTemplates**|  
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|可讓您指定要在建置時接收錯誤的檔案。<br /><br /> **Devenv myproj.csproj /build /out log.txt**|  
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|要建置、清除或部署的專案。 只有在同時提供 /build、/rebuild、/clean 或 /deploy 參數時，才能使用此參數。|  
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|指定要建置或部署的專案組態。 只有在同時提供 /project 參數時，才能使用此參數。|  
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|根據所指定方案的組態，清除後建置指定的方案或專案。|  
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|還原 Visual Studio 預設設定。 選擇性地將設定重設為指定的 .vssettings 檔案。|  
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|通知 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 合併系統上的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 套件，並檢查 MEF 快取中的任何變更。|  
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|將指定的方案檔和其所有專案檔或指定的專案檔升級至這些檔案的目前 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 格式。|  
  
## <a name="see-also"></a>請參閱  
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
