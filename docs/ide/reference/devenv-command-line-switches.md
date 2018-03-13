---
title: "Visual Studio Devenv 命令列參數 | Microsoft Docs"
ms.date: 02/28/2018
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b507ff8710e3257f2da61a32baa81a18441c3aff
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="devenv-command-line-switches"></a>Devenv 命令列參數

Devenv 可讓您設定整合式開發環境 (IDE) 的各種選項，也可讓您從命令列建置、偵錯和部署專案。 使用這些參數透過指令碼或 .bat 檔案 (例如，夜間組建指令碼) 執行 IDE，或在特定組態中啟動 IDE。

> [!NOTE]
> 針對組建相關工作，建議您使用 MSBuild，而不是 devenv。 如需詳細資訊，請參閱 [MSBuild 命令列參考](../../msbuild/msbuild-command-line-reference.md)。

## <a name="devenv-switch-syntax"></a>Devenv 參數語法

根據預設，devenv 命令會將參數傳遞至 devenv.com 公用程式。 Devenv.com 公用程式會透過標準系統資料流來傳遞輸出，像是 `stdout` 和 `stderr`。 當公用程式擷取到輸出時，會決定適當的 I/O 重新導向，例如導向 .txt 檔案。

另一方面，以 `devenv.exe` 開頭的命令可以使用相同參數，但會略過 devenv.com 公用程式。

`devenv` 參數的語法規則與其他 DOS 命令列公用程式的語法規則類似。 下列語法規則套用至所有 `devenv` 參數和其引數︰

- 命令開始於 `devenv`。

- 參數不區分大小寫。

- 指定方案或專案時，第一個引數是方案檔或專案檔的名稱 (包括檔案路徑)。

- 如果第一個引數不是解決方案檔或專案檔，則會使用適當的編輯器在 IDE 的新執行個體開啟該檔案。

- 如果您提供專案檔名稱，而不是解決方案檔名稱，`devenv` 命令會在專案檔的父資料夾中搜尋同名的解決方案檔。 例如，`devenv /build myproject1.vbproj` 命令會在父資料夾中搜尋名為 "myproject1.sln" 的解決方案檔。

    > [!NOTE]
    > 只能有一個參考此專案的方案檔應該位於其上層資料夾。 如果父資料夾未包含參考此專案的解決方案檔，或父資料夾包含二或多個參考此專案的解決方案檔，則會建立暫存解決方案檔。

- 當路徑和檔案名稱包括空格時，必須在前後加上引號 ("")。 例如，"c:\project a\\"。

- 在同一行的參數與引數之間插入一個空白字元。 例如，**devenv /log output.txt** 命令會開啟 IDE，並將該工作階段的所有記錄資訊輸出至 output.txt。

- 您不能在 `devenv` 命令中使用模式比對語法命令。

## <a name="devenv-switches"></a>Devenv 參數

下列命令列參數顯示 IDE，並執行所述的工作。

|命令列參數|描述|
|-------------------------|-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|啟動 IDE，並執行指定的命令。|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|在偵錯工具的控制下載入 C++ 可執行檔。 此參數不適用於 Visual Basic 或 C# 可執行檔。 如需詳細資訊，請參閱[在偵錯工具中自動啟動處理序](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)。|
|[/LCID 或 /l](../../ide/reference/lcid-devenv-exe.md)|設定 IDE 的預設語言。 如果 Visual Studio 安裝中未包含指定的語言，則會忽略此設定。|
|[/Log](../../ide/reference/log-devenv-exe.md)|啟動 Visual Studio，並將所有活動記錄至記錄檔。|
|[/Run 或 /r](../../ide/reference/run-devenv-exe.md)|編譯並執行指定的方案。|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|編譯並執行指定的方案、執行方案時最小化 IDE，以及在方案完成執行之後關閉 IDE。|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|讓 IDE 使用 PATH、INCLUDE 和 LIB 環境變數進行 C++ 編譯，而不是在 [選項] 對話方塊中 [專案] 選項的 [VC++ 目錄] 區段中指定的設定。 此參數的安裝包含 **使用 C++ 的桌面開發**工作負載。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds)。|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|在這個應用程式的作用中執行個體中開啟指定的檔案。 如果沒有執行中的執行個體，則會以簡易視窗配置啟動新的執行個體。|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|以安全模式啟動 Visual Studio，並且只載入預設環境和服務，以及隨附的協力廠商套件版本。|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|清除想要避免 VSPackage 載入問題的使用者已新增至 VSPackage 的所有 SkipLoading 標記。|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|強制 Visual Studio 合併來自所有可用 Vspackage 的資源中繼資料 (其描述功能表、工具列和命令群組)。 您必須以系統管理員身分執行此命令。|

下列命令列參數不會顯示 IDE。

|命令列參數|描述|
|-------------------------|-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|在 [命令提示字元] 視窗中顯示 devenv 參數的說明。<br /><br /> **Devenv /?**|
|[/Build](../../ide/reference/build-devenv-exe.md)|根據所指定方案的組態，建置指定的方案或專案。<br /><br /> **Devenv myproj.csproj /build**|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|刪除 build 命令所建立的任何檔案，而不會影響原始程式檔。<br /><br /> **Devenv myproj.csproj /clean**|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|根據方案組態，建置方案，以及部署所需的檔案。<br /><br /> **Devenv myproj.csproj /deploy**|
|[/Diff](../../ide/reference/diff.md)|比較兩個檔案。 接受四個參數：SourceFile、TargetFile、SourceDisplayName (選擇性)、TargetDisplayName (選擇性)。|
|[/Out](../../ide/reference/out-devenv-exe.md)|可讓您指定要在建置時接收錯誤的檔案。<br /><br /> **Devenv myproj.csproj /build /out log.txt**|
|[/Project](../../ide/reference/project-devenv-exe.md)|要建置、清除或部署的專案。 只有在同時提供 /build、/rebuild、/clean 或 /deploy 參數時，才能使用此參數。|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|指定要建置或部署的專案組態。 只有在同時提供 /project 參數時，才能使用此參數。|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|根據所指定方案的組態，清除後建置指定的方案或專案。|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|還原 Visual Studio 預設設定。 選擇性地將設定重設為指定的 .vssettings 檔案。|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|將指定的解決方案檔及其所有專案檔，或指定的專案檔，升級為這些檔案目前的 Visual Studio 格式。|

## <a name="see-also"></a>另請參閱

* [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)