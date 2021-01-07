---
title: C + + debug config 的專案設定
description: 在屬性頁中設定 C 和 c + + 調試。 本文描述這些設定，並告訴您其類別。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/26/2018
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6130b49beecb3411c275fc5d2005b7aabee262fd
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975286"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ 偵錯組態的專案設定
您可以在 [ **屬性頁** ] 對話方塊中變更 C 或 c + + 偵錯工具設定的專案設定，如 [如何：設定 Debug 和 release 設定](../debugger/how-to-set-debug-and-release-configurations.md)中所述。 下表顯示 [屬性頁] 對話方塊中與偵錯工具相關的設定位置。

> [!NOTE]
> UWP 應用程式和以 c + + 撰寫之元件的設定 **屬性/調試** 程式類別目錄中的 debug 專案設定不同。 請參閱 [開始 (VB、c #、c + + 和 XAML) 的 debug 會話 ](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。

 每個偵錯 屬性設定會自動寫入並儲存在 「 每位使用者 」 檔案 (.vcxproj.user) 為您的方案，當您儲存您的解決方案。

 在 [ **要啟動的調試** 程式] 清單方塊中，指定要使用哪個偵錯工具，如下表所述。 您的選擇將影響屬性的可見性。

## <a name="configuration-properties-folder-debugging-category"></a>組態屬性資料夾 (偵錯分類)

| **設定** | **說明** |
| - | - |
| **要啟動的偵錯工具** | 指定要執行的偵錯工具，並提供下列選項：<br /><br /> -   **本機 Windows 偵錯工具**<br />-   **遠端 Windows 偵錯工具**<br />-   **網頁瀏覽器偵錯工具**<br />-   **Web 服務偵錯工具** |
| **命令** (本機 Windows 偵錯工具) | 指定用來啟動將於本機電腦上進行偵錯之程式的命令。 |
| **遠端命令** (遠端 Windows 偵錯工具) | 遠端電腦上 .exe 的路徑。 依照在遠端電腦上輸入路徑的方式輸入路徑。 |
|  (本機 Windows 偵錯工具的 **命令引數**) <br /><br /> 遠端 **命令引數** (遠端 Windows 偵錯工具)  | - 指定先前指定之命令的引數。<br /><br /> 您可以在這個方塊中使用下列重新導向運算子：<br /><br /> < `file`<br /> 從檔案讀取 stdin。<br /><br /> > `file`<br /> 將 stdout 寫入檔案。<br /><br /> >> `file`<br /> 將 stdout 附加至檔案。<br /><br /> 2> `file`<br /> 將 stderr 寫入檔案。<br /><br /> 2>> `file`<br /> 將 stderr 附加至檔案。<br /><br /> 2> &1<br /> 將 stderr (2) 輸出傳送到與 stdout (1) 相同的位置。<br /><br /> 1> &2<br /> 將 stdout (1) 輸出傳送到與 stderr (2) 相同的位置。<br /><br /> 在大多數情況下，這些運算子只適用於主控台應用程式。 |
| **工作目錄** | 指定要進行偵錯之程式的工作目錄 (相對於您的 EXE 所在的專案目錄)。 如果您將這個項目保持空白，工作目錄就會是專案目錄。 遠端偵錯程式的專案目錄是在遠端伺服器上。 |
| **附加** (本機 Windows 偵錯工具和遠端 Windows 偵錯工具) | 指定是否要啟動或附加至應用程式。 預設設定為 [否]。 |
| **遠端伺服器名稱** (遠端 Windows 偵錯工具) | 指定要用於應用程式偵錯的電腦名稱 (並非您的電腦)。<br /><br /> RemoteMachine 建置巨集會設定為這個屬性的值；如需詳細資訊，請參閱[建置命令和屬性的巨集](/cpp/build/reference/common-macros-for-build-commands-and-properties)。 |
| **連線** (遠端 Windows 偵錯工具) | 可讓您在標準和無驗證連線類型之間切換，以進行遠端偵錯。 在 [遠端伺服器名稱] 方塊中指定遠端電腦名稱。 連線類型如下：<br /><br /> -   **遠端使用 Windows 驗證**<br />-   **遠端未使用驗證**<br /><br /> **注意**：[遠端未使用驗證] 可能容易使遠端電腦因為安全性違規而受到損害。 Windows 驗證模式較為安全。<br /><br /> 如需詳細資訊，請參閱[遠端偵錯設定](../debugger/remote-debugging.md)。 |
| **HTTP URL** (Web 服務偵錯工具和網頁瀏覽器偵錯工具) | 指定要偵錯之專案所在的 URL。 |
| **偵錯工具類型** | 指定要使用的偵錯工具類型：**僅限原生**、**僅限受控**、**僅限 GPU**、**混合**、**自動** (預設值) 或 **指令碼**。<br /><br /> -   **僅限原生** 適用於非受控 C++ 程式碼。<br />-   **僅限受控** 適用於通用語言執行平台 (受控碼) 下執行的程式碼。<br />-   **混合** 會針對受控和非受控程式碼叫用偵錯工具。<br />-   **自動** 會根據編譯器和 EXE 資訊判斷偵錯工具類型。<br />-   **指令碼** 會針對指令碼叫用偵錯工具。<br />-   **僅限 GPU** 適用於 GPU 裝置或 DirectX 參考轉譯器上執行的 C++ AMP 程式碼。 請參閱將 [GPU 程式碼進行調試](../debugger/debugging-gpu-code.md)程式。 |
| **環境** (本機 Windows 偵錯工具和遠端 Windows 偵錯工具)  | 為您要進行偵錯的程式指定環境變數。 使用標準環境變數語法 (例如 `PATH="%SystemRoot%\..."`)。 依據 **合併環境** 設定而定，這些變數會覆寫系統環境或與系統環境合併。 當您以滑鼠左鍵按一下 [設定] 資料行時，就會出現 [編輯 ...]。 選取該連結以編輯環境變數。 |
| **合併環境** (本機 Windows 偵錯工具) | 判斷 [環境] 方塊中指定的變數，是否要與作業系統所定義的環境合併。 預設設定為 [是]。 |
| **SQL 偵錯** (適用所有偵錯工具，但 MPI 叢集偵錯工具除外) | 從您的 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 應用程式啟用 SQL 程序的偵錯功能。 預設設定為 [否]。 |
| **針對加速器類型進行偵錯** (僅適用於 GPU 偵錯) | 指定要用來進行偵錯的 GPU 裝置。 安裝相容 GPU 裝置的裝置驅動程式將會加入額外的選項。 預設設定為 **GPU - 軟體模擬器**。 |
| **GPU 預設中斷點行為** (僅適用於 GPU 偵錯) | 指定是否應針對 SIMD 變形的每個執行緒引發中斷點事件。 預設設定為僅針對每次變形引發中斷點事件一次。 |
| **AMP 的預設加速器** | 指定對 GPU 程式碼進行偵錯時的預設 AMP 加速器。 如果問題是由硬體或驅動程式所造成，而不是您的程式碼所造成，請選擇 [WARP 軟體加速器] 進行調查。 |
| **部署目錄** (遠端 Windows 偵錯工具) | 指定遠端電腦上的路徑，在啟動之前專案輸出會複製到這個路徑中。 路徑可以是遠端電腦上的網路共用，或是遠端電腦上資料夾的路徑。 預設設定為空白，表示專案輸出不會複製到網路共用。 若要啟用檔案部署，您也必須選取 [組態管理員] 對話方塊中的 [部署] 核取方塊。 如需詳細資訊，請參閱 [如何：建立和編輯](../ide/how-to-create-and-edit-configurations.md)設定。 |
| **其他要部署的檔案** (遠端 Windows 偵錯工具) | 如果已設定 [部署目錄] 屬性，這會是要複製到部署目錄的其他檔案清單（以分號分隔）。 預設設定為空白，表示不會將其他檔案複製到部署目錄。 若要啟用檔案部署，您也必須選取 [組態管理員] 對話方塊中的 [部署] 核取方塊。 如需詳細資訊，請參閱 [如何：建立和編輯](../ide/how-to-create-and-edit-configurations.md)設定。 |
| **部署 Visual C++ 偵錯執行階段程式庫** (遠端 Windows 偵錯工具) | 如果 [部署目錄] 屬性已設定，這會指定是否應將目前平台的 Visual C++ 偵錯執行階段程式庫複製到網路共用。 預設設定為 [是]。 |

## <a name="cc-folder-general-category"></a>C/C++ 資料夾 (一般分類)

|設定|描述|
|-------------|-----------------|
|**偵錯資訊格式** ([/Z7、/Zd、Zi、/ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|指定要為專案建立的偵錯資訊類型。<br /><br /> 預設選項 (/ZI) 會以 [編輯後繼續] 相容格式建立程式資料庫 (PDB)。 如需詳細資訊，請參閱 [/Z7、/Zd、/Zi、/ZI (偵錯資訊格式)](/cpp/build/reference/z7-zi-zi-debug-information-format)。|

## <a name="cc-folder-optimization-category"></a>C/C++ 資料夾 (最佳化分類)

|設定|描述|
|-------------|-----------------|
|**最佳化**|指定編譯器是否應該將它所產生的程式碼最佳化。 最佳化會變更執行的程式碼。 優化的程式碼不再符合原始程式碼，讓偵錯工具更困難。<br /><br /> 預設選項 ([停用 (/0d]) 會隱藏最佳化。 您可以在隱藏最佳化的情況下進行開發，然後在建立程式碼的生產環境版本時再將此功能開啟。|

## <a name="linker-folder-debugging-category"></a>連結器資料夾 (偵錯分類)

|設定|描述|
|-------------|-----------------|
|**產生偵錯資訊** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|通知連結器要包含偵錯資訊，資訊的格式是由 [/Z7、/Zd、Zi 或 /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format) 所指定。|
|**產生程式資料庫檔案** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|在此方塊中指定程式資料庫 (PDB) 檔案的名稱。 您必須選取 ZI 或 /Zi 以指定 [偵錯資訊格式]。|
|**移除專用符號** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|如果您不想要在 PDB 檔中包含專用符號，請在這個方塊中指定 PDB 檔的名稱。 當您使用任何產生 PDB 檔案的編譯器或連結器選項（例如/DEBUG、/Z7、/Zd.）建立程式映射時，此選項會建立第二個 PDB 檔案。 或 /Zi)。 第二個 PDB 檔會省略您不想要出貨給客戶的符號。 如需詳細資訊，請參閱 [/PDBSTRIPPED (去除私用符號) ](/cpp/build/reference/pdbstripped-strip-private-symbols)。|
|**產生對應檔案** ([/MAP](/cpp/build/reference/map-generate-mapfile))|通知連結器在連結期間產生對應檔。 預設設定為 [否]。 如需詳細資訊，請參閱 [/MAP (產生對應檔)](/cpp/build/reference/map-generate-mapfile)。|
|**對應檔名稱** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*name*)|如果您選擇 [產生對應檔]，就可以在這個方塊中指定對應檔。 如需詳細資訊，請參閱 [/MAP (產生對應檔)](/cpp/build/reference/map-generate-mapfile)。|
|**對應匯出** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|在對應檔中包含匯出函式。 預設設定為 [否]。 如需詳細資訊，請參閱 [/MAPINFO (將資訊包括在對應檔中)](/cpp/build/reference/mapinfo-include-information-in-mapfile) \(機器翻譯\)。|
|**可偵錯組件** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|指定連結器 /ASSEMBLYDEBUG 選項的設定。 可能的值包括：<br /><br /> -   **未發出可偵錯屬性**。<br />-   **正在進行執行階段追蹤並停用最佳化 (/ASSEMBLYDEBUG)**。 這是預設設定。<br />-   **沒有執行階段追蹤並啟用最佳化 (/ASSEMBLYDEBUG:DISABLE)**。<br />-   **\<inherit from parent or project defaults>**.<br />- 如需詳細資訊，請參閱 [/ASSEMBLYDEBUG (新增 DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)。|

 您可以使用 Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings 介面，以程式設計的方式在 [組態屬性] 資料夾 ([偵錯] 分類) 中變更這些設定。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>。

## <a name="other-project-settings"></a>其他專案設定

若要將靜態程式庫和 Dll 之類的專案類型進行偵錯工具，您的 Visual Studio 專案必須能夠找到正確的檔案。 當原始程式碼可供使用時，您可以將靜態程式庫和 Dll 做為個別的專案加入至相同的方案，讓偵錯工具更容易進行。 如需建立這些專案類型的詳細資訊，請參閱 [建立和使用動態連結程式庫 (DLL) ](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) 和 [使用靜態程式庫建立](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp)。 使用原始程式碼時，您也 **可以選擇 [**  >    >  **從現有程式碼新增專案**]，以建立新的 Visual Studio 專案。

若要對專案外部的 Dll 進行 debug 錯，請參閱 [偵錯工具 dll 專案](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal)。 如果您需要對自己的 DLL 專案進行偵錯工具，但無法存取呼叫應用程式的專案，請參閱 [如何從 DLL 專案進行調試](../debugger/how-to-debug-from-a-dll-project.md)程式。

## <a name="see-also"></a>請參閱
- [程式碼的偵錯工具](../debugger/debugging-native-code.md)
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)
- [建立和管理 c + + 專案](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (加入 DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [建置命令和屬性的一般巨集](/cpp/ide/common-macros-for-build-commands-and-properties)