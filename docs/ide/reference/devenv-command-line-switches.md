---
title: Devenv 命令列參數
description: 瞭解 devenv 命令列參數，以及如何使用它們來設定 IDE 選項，也可以從命令列建立、偵測和部署專案。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bef72e8889026f8202c7acdf3ea7c6b97c780b75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882169"
---
# <a name="devenv-command-line-switches"></a>Devenv 命令列參數

Devenv 可讓您從命令列針對 IDE 設定不同選項、建置專案、偵錯專案，以及部署專案。 使用這些參數，從指令碼或 .bat 檔案 (例如，夜間組建指令碼) 執行 IDE，或在特定組態中啟動 IDE。

> [!NOTE]
> 針對組建相關工作，建議您使用 MSBuild，而不是 devenv。 如需詳細資訊，請參閱 [MSBuild 命令列參考](../../msbuild/msbuild-command-line-reference.md)。

如需與 VSPackage 開發相關的參數資訊，請參閱[適用於 VSPackage 開發的 Devenv 命令列參數](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)。

## <a name="devenv-switch-syntax"></a>Devenv 參數語法

以 `devenv` 開頭的命令是由 `devenv.com` 公用程式處理，它會透過標準系統資料流提供輸出，例如 `stdout` 和 `stderr`。 當公用程式擷取到輸出時，會決定適當的 I/O 重新導向，例如導向 .txt 檔案。

或者，以 `devenv.exe` 為開頭的命令可以使用相同參數，但會略過 `devenv.com` 公用程式。 直接使用 `devenv.exe` 會導致輸出不顯示在主控台上。

`devenv` 參數的語法規則與其他 DOS 命令列公用程式的規則類似。 下列語法規則套用至所有 `devenv` 參數和其引數︰

- 命令開始於 `devenv`。

- 參數不會區分大小寫。

- 您可以使用連字號 ("-") 或斜線 ("/") 來指定參數。

- 指定方案或專案時，第一個引數是方案檔或專案檔的名稱 (包括檔案路徑)。

- 如果第一個引數不是方案檔或專案檔，則會使用適當的編輯器在 IDE 的新執行個體中開啟該檔案。

- 如果您提供專案檔名稱，而不是解決方案檔名稱，`devenv` 命令會在專案檔的父資料夾中搜尋同名的解決方案檔。 例如，`devenv myproject1.vbproj /build` 命令會在父資料夾中搜尋名為 `myproject1.sln` 的方案檔。

  > [!NOTE]
  > 只能有一個參考此專案的方案檔應該位於其上層資料夾。 如果父資料夾未包含參考此專案的解決方案檔，或父資料夾包含二或多個參考此專案的解決方案檔，則會建立暫存解決方案檔。

- 當路徑和檔案名稱包括空格時，必須在前後加上引號 ("")。 例如： `"c:\project a\"` 。

- 在同一行的參數與引數之間插入一個空白字元。 例如，`devenv /log output.txt` 命令會開啟 IDE，並將該工作階段的所有記錄資訊輸出至 output.txt。

- 您不能在 `devenv` 命令中使用模式比對語法。

## <a name="devenv-switches"></a>Devenv 參數

下列命令列參數會顯示 IDE，並執行所述的工作。

|命令列參數|Description|
| - |-----------------|
|[/Command](command-devenv-exe.md)|啟動 IDE，並執行指定的命令。<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|在偵錯工具的控制下載入 C++ 可執行檔。 此參數不適用於 Visual Basic 或 C# 可執行檔。 如需詳細資訊，請參閱[在偵錯工具中自動啟動處理序](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)。<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|比較兩個檔案。 採用四個參數： *SourceFile*、 *TargetFile*、 *SourceDisplayName* (選擇性的) ，以及 *TargetDisplayName* (選擇性的) 。<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|開啟指定的解決方案，而不載入任何專案。<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|在這個應用程式的作用中執行個體中開啟指定的檔案。 如果沒有執行中的執行個體，則會以簡易視窗配置啟動新的執行個體。<br /><br /> `devenv /edit File1 File2`|
|[/LCID 或 /L](lcid-devenv-exe.md)|設定 IDE 的預設語言。 如果 Visual Studio 安裝中未包含指定的語言，則會忽略此設定。<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|啟動 Visual Studio，並將所有活動記錄至記錄檔。<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|開啟 IDE，而不顯示啟動顯示畫面。<br /><br /> `devenv /nosplash File1 File2`|
|[/ResetSettings](resetsettings-devenv-exe.md)|還原 Visual Studio 預設設定。 選擇性地將設定重設為指定的 `.vssettings` 檔案。<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Run 或 /R](run-devenv-exe.md)|編譯並執行指定的方案。<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|編譯並執行指定的方案、執行方案時最小化 IDE，以及在方案完成執行之後關閉 IDE。<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|以安全模式啟動 Visual Studio。 此參數只會載入預設環境、預設服務，以及隨附的協力廠商封裝版本。<br /><br /> 此參數不需使用引數。|
|[/UseEnv](useenv-devenv-exe.md)|導致 IDE 使用 PATH、INCLUDE、LIBPATH 和 LIB 環境變數進行 C++ 編譯。 此參數的安裝包含 **使用 C++ 的桌面開發** 工作負載。 如需詳細資訊，請參閱 [Setting the Path and Environment Variables for Command-Line Builds](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds)。|

下列命令列參數不會顯示 IDE。

|命令列參數|描述|
| - |-----------------|
|[/?](q-devenv-exe.md)|在 [命令提示字元] 視窗中顯示 `devenv` 參數的說明。<br /><br /> 此參數不需使用引數。|
|[/Build](build-devenv-exe.md)|根據所指定方案的組態，建置指定的方案或專案。<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|刪除 build 命令所建立的任何檔案，而不會影響原始程式檔。<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|根據方案組態，建置方案以及部署所需的檔案。<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|可讓您指定要在建置時接收錯誤的檔案。<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|要建置、清除或部署的專案。 只有在同時提供 `/Build`、`/Rebuild`、`/Clean` 或 `/Deploy` 參數時，才能使用此參數。<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|指定要建置或部署的專案組態。 只有在同時提供 `/Project` 參數時，才能使用此參數。<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|根據所指定方案的組態，清除後建置指定的方案或專案。<br /><br /> `devenv mysln.sln /rebuild`|
|[/Upgrade](upgrade-devenv-exe.md)|將指定的解決方案檔及其所有專案檔，或指定的專案檔，升級為這些檔案目前的 Visual Studio 格式。<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](general-environment-options-dialog-box.md)
- [適用于 VSPackage 開發的 Devenv 命令列參數](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
