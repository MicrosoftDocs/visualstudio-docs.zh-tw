---
title: Visual Studio 2017 擴充性的重大變更
description: 瞭解 Visual Studio 2017 中的擴充性模型之重大變更的技術詳細資料，以及您可以如何解決這些問題。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c07d48eb63c727701c3b6fcde9d405f9c96abec1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068189"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 擴充性的變更

Visual Studio 2017 提供 [更快、更輕量的 Visual Studio 安裝體驗](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) ，可降低 Visual Studio 對使用者系統的影響，同時讓使用者更能選擇所安裝的工作負載和功能。 為了支援這些改良功能，我們已對擴充性模型進行變更，包括一些重大變更。 本文描述這些變更的技術詳細資料，以及可解決這些變更的方式。

> [!NOTE]
> 某些資訊是時間點執行的詳細資料，稍後可能會變更。

## <a name="changes-affecting-vsix-format-and-installation"></a>變更會影響 VSIX 格式和安裝

Visual Studio 2017 引進了 VSIX v3 (第3版) 格式，以支援輕量安裝體驗。

VSIX 格式的變更包括：

* 安裝必要條件的宣告。 為了提供輕量、快速安裝 Visual Studio 的承諾，安裝程式現在會為使用者提供更多的設定選項。 因此，為了確保已安裝擴充功能所需的功能和元件，擴充功能需要宣告其相依性。

  * Visual Studio 2017 安裝程式會在安裝延伸模組時，自動提供取得並安裝使用者必要元件的功能。
  * 當使用者嘗試安裝不是使用新 VSIX v3 格式建立的延伸模組時，即使它們已在其資訊清單中標示為目標版本15.0，也會收到警告。

* VSIX 格式的增強功能。 為了提供對也支援並存安裝之 Visual Studio 的 [低影響力安裝](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) ，我們不再將大部分的設定資料儲存到系統登錄，並且將 Visual Studio 特定的元件移出 GAC。 此外，我們也增強了 VSIX 格式和 VSIX 安裝引擎的功能，讓您可以使用它，而非 MSI 或 EXE 來安裝某些安裝類型的擴充功能。

這些新功能包括：

* 註冊至指定的 Visual Studio 實例。
* 在延伸模組 [資料夾](set-install-root.md)之外安裝。
* 偵測處理器架構。
* 依賴語言分隔的語言套件。
* 具有 [NGEN 支援](ngen-support.md)的安裝。

## <a name="build-an-extension-for-visual-studio-2017"></a>建立 Visual Studio 2017 的延伸模組

Visual Studio 2017 提供撰寫新 VSIX v3 資訊清單格式的設計工具。 如需使用設計工具或手動更新專案和資訊清單以開發 VSIX v3 擴充功能的詳細資訊，請參閱隨附的檔如何：將擴充性 [專案遷移至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 。

## <a name="change-visual-studio-user-data-path"></a>變更： Visual Studio 使用者資料路徑

之前，每一部電腦上只能有一個 Visual Studio 主要版本的安裝。 若要支援 Visual Studio 2017 的並存安裝，使用者的電腦上可能會有多個 Visual Studio 的使用者資料路徑。

在 Visual Studio 進程內執行的程式碼應該更新為使用 Visual Studio Settings Manager。 在 Visual Studio 進程之外執行的程式碼，可以 [遵循此處的指引](locating-visual-studio.md)，找到特定 Visual Studio 安裝的使用者路徑。

## <a name="change-global-assembly-cache-gac"></a>變更：全域組件快取 (GAC) 

大部分 Visual Studio 核心元件不再安裝到 GAC 中。 已進行下列變更，使 Visual Studio 進程中執行的程式碼仍可在執行時間找到必要的元件。

> [!NOTE]
> [INSTALLDIR] 是指 Visual Studio 的安裝根目錄。 *VSIXInstaller.exe* 將會自動填入此程式碼，但若要撰寫自訂部署程式碼，請參閱 [尋找 Visual Studio](locating-visual-studio.md)。

* 只安裝到 GAC 中的元件：

  這些元件現在會安裝在 <em>[INSTALLDIR] \Common7\IDE \* 、* [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> 或 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* 下。 這些資料夾是 Visual Studio 進程的探查路徑的一部分。

* 安裝至非探查路徑和 GAC 中的元件：

  * GAC 中的複本已從安裝程式中移除。
  * 已加入 *.pkgdef* 檔案，以指定元件的程式碼基底專案。

    例如：

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    在執行時間，Visual Studio 的 .pkgdef 子系統會將這些專案合併到 *[VSAPPDATA] \devenv.exe.config*) 作為元素下的 Visual Studio 進程執行時間配置 (檔中 [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) 。 這是建議的方式，讓 Visual Studio 的進程尋找您的元件，因為它可避免透過探查路徑搜尋。

### <a name="reacting-to-this-breaking-change"></a>回應此重大變更

* 如果您的延伸模組正在 Visual Studio 進程內執行：

  * 您的程式碼將能找到 Visual Studio 核心元件。
  * 如有必要，請考慮使用 *.pkgdef* 檔案來指定元件的路徑。

* 如果您的延伸模組是在 Visual Studio 進程之外執行：

  請考慮使用設定檔或元件解析程式 <em>，尋找 [INSTALLDIR] \Common7\IDE \* 、* [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> 或 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* 下的 Visual Studio 核心元件。

## <a name="change-reduce-registry-impact"></a>變更：減少登錄影響

### <a name="global-com-registration"></a>全域 COM 註冊

* 先前 Visual Studio 在 HKEY_CLASSES_ROOT 中安裝許多登錄機碼，並 HKEY_LOCAL_MACHINE hive 來支援原生 COM 註冊。 為了消除這種影響，Visual Studio 現在會使用 [COM 元件的免註冊啟用](/previous-versions/dotnet/articles/ms973913(v=msdn.10))。
* 因此，Visual Studio 預設不會再安裝% ProgramFiles (x86) % \ Common Files\Microsoft Shared\MSEnv 下的大部分 TLB/.OLB/DLL 檔案。 這些檔案現在會安裝在 [INSTALLDIR] 下，以及 Visual Studio 主機進程所使用的對應 Registration-Free COM 資訊清單。
* 因此，依賴 Visual Studio COM 介面的全域 COM 註冊的外部程式碼將不再找到這些註冊。 在 Visual Studio 進程內執行的程式碼將不會有任何差異。

### <a name="visual-studio-registry"></a>Visual Studio 登錄

* 先前，Visual Studio 將許多登錄機碼安裝到系統的 **HKEY_LOCAL_MACHINE** ，並在 Visual Studio 特定的機碼下 **HKEY_CURRENT_USER** hive：

  * **HKLM\Software\Microsoft\VisualStudio \{Version}**： MSI 安裝程式和每部電腦延伸模組所建立的登錄機碼。
  * **HKCU\Software\Microsoft\VisualStudio \{Version}**： Visual Studio 所建立的登錄機碼來儲存使用者專屬的設定。
  * **HKCU\Software\Microsoft\VisualStudio \{版本} _Config**：上述 VISUAL STUDIO HKLM 金鑰的複本，加上從 *.pkgdef* 檔案依副檔名合併的登錄機碼。

* 為了降低對登錄的影響，Visual Studio 現在使用 [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) 函式，將登錄機碼儲存在 *[VSAPPDATA] \privateregistry.bin* 下的私用二進位檔案中。 系統登錄中只會保留非常少量的 Visual Studio 特定金鑰。
* 在 Visual Studio 進程內執行的現有程式碼不會受到影響。 Visual Studio 會將 HKCU Visual Studio 特定金鑰底下的所有登錄作業重新導向至私用登錄。 讀取和寫入其他登錄位置將繼續使用系統登錄。
* 外部程式碼將需要從這個檔案載入和讀取 Visual Studio 登錄專案。

### <a name="react-to-this-breaking-change"></a>回應此重大變更

* 您也應該將外部程式碼轉換為使用 Registration-Free COM 元件的啟用。
* 外部元件可以 [遵循此處的指引](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)，找到 Visual Studio 位置。
* 建議外部元件使用 [外部設定管理員](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) ，而不是直接讀取/寫入 Visual Studio 登錄機碼。
* 檢查您的延伸模組所使用的元件是否可能已實作為註冊的另一種技術。 例如，偵錯工具擴充功能可能會利用新的 [MSVSMON JSON 檔案 COM 註冊](migrate-debugger-COM-registration.md)。