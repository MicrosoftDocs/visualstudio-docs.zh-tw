---
title: Visual Studio 2017 擴充性的重大變更
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1a12470530589c8d19a088428bc265c530b55f0
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252323"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 擴充性的變更

Visual Studio 2017 提供[更快速、更輕量的 Visual Studio 安裝體驗](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer)，可降低使用者系統上 Visual Studio 的影響，同時讓使用者更能選擇所安裝的工作負載和功能。 為了支援這些改良功能，我們對擴充性模型進行了變更，包括一些重大變更。 本文說明這些變更的技術詳細資料，以及解決問題的方式。

> [!NOTE]
> 某些資訊是時間點執行的詳細資料，稍後可能會變更。

## <a name="changes-affecting-vsix-format-and-installation"></a>影響 VSIX 格式和安裝的變更

Visual Studio 2017 引進了 VSIX v3 （第3版）格式來支援輕量安裝體驗。

對 VSIX 格式所做的變更包括：

* 安裝程式必要條件的宣告。 為了提供輕量、快速安裝 Visual Studio 的承諾，安裝程式現在會為使用者提供更多的設定選項。 因此，為了確保已安裝延伸模組所需的功能和元件，延伸模組需要宣告其相依性。

  * Visual Studio 2017 安裝程式會自動提供，以在安裝擴充功能的過程中，為使用者取得並安裝必要的元件。
  * 當使用者嘗試安裝不是使用新的 VSIX v3 格式所建立的延伸模組時，即使這些擴充功能已在其資訊清單中標示為目標版本15.0，也會發出警告。

* VSIX 格式的增強功能。 為了在同時支援並存安裝的 Visual Studio 上提供[低影響安裝](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install)，我們不會再將大部分的設定資料儲存至系統登錄，並將 Visual Studio 特定的元件移出 GAC。 我們也增加了 VSIX 格式和 VSIX 安裝引擎的功能，讓您可以使用它，而不是 MSI 或 EXE 來安裝某些安裝類型的延伸模組。

新功能包括：

* 註冊到指定的 Visual Studio 實例。
* 在[extensions 資料夾](set-install-root.md)外部安裝。
* 偵測處理器架構。
* 依賴以語言分隔的語言套件。
* 具有[NGEN 支援](ngen-support.md)的安裝。

## <a name="build-an-extension-for-visual-studio-2017"></a>建立 Visual Studio 2017 的擴充功能

Visual Studio 2017 中提供用於撰寫新 VSIX v3 資訊清單格式的設計師工具。 請參閱隨附的[檔如何：將擴充性專案遷移至](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) Visual Studio 2017，以取得使用設計工具的詳細資料，或對專案和資訊清單進行手動更新以開發 VSIX v3 擴充功能。

## <a name="change-visual-studio-user-data-path"></a>更改Visual Studio 使用者資料路徑

之前，每一部電腦上只能有一個 Visual Studio 主要版本的安裝。 為了支援 Visual Studio 2017 的並存安裝，使用者的電腦上可能會有多個 Visual Studio 的使用者資料路徑。

在 Visual Studio 程式中執行的程式碼應該更新為使用 Visual Studio 設定管理員。 在 Visual Studio 進程外部執行的程式碼，可以[遵循這裡的指引](locating-visual-studio.md)，尋找特定 Visual Studio 安裝的使用者路徑。

## <a name="change-global-assembly-cache-gac"></a>更改全域組件快取（GAC）

大部分的 Visual Studio 核心元件不會再安裝到 GAC 中。 已進行下列變更，因此在 Visual Studio 進程中執行的程式碼仍可在執行時間找到必要的元件。

> [!NOTE]
> 下方的 [INSTALLDIR] 是指 Visual Studio 的安裝根目錄。 *VSIXInstaller*會自動填入此，但若要撰寫自訂部署程式碼，請參閱[尋找 Visual Studio](locating-visual-studio.md)。

* 僅安裝在 GAC 中的元件：

  這些元件現在會安裝在<em>[INSTALLDIR] \Common7\IDE\*、* [INSTALLDIR] \Common7\IDE\PublicAssemblies</em>或 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*之下。 這些資料夾是 Visual Studio 進程的探查路徑的一部分。

* 已安裝到非探查路徑和 GAC 中的元件：

  * GAC 中的複本已從安裝程式中移除。
  * 已加入 *.pkgdef*檔案，以指定元件的程式碼基底專案。

    例如：

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    在執行時間，Visual Studio .pkgdef 子系統會將這些專案合併到 Visual Studio 進程的執行時間設定檔案（在 *[VSAPPDATA] \devenv.exe.config*）做為[`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element)元素。 這是建議的方法，讓 Visual Studio 進程尋找您的元件，因為它可避免搜尋路徑的搜尋。

### <a name="reacting-to-this-breaking-change"></a>對這種重大變更的反應

* 如果您的擴充功能是在 Visual Studio 進程內執行：

  * 您的程式碼可以找到 Visual Studio 核心元件。
  * 如有需要，請考慮使用 *.pkgdef*檔案來指定元件的路徑。

* 如果您的擴充功能是在 Visual Studio 進程外部執行：

  請考慮使用設定檔或元件<em>，尋找 [INSTALLDIR\*] \Common7\IDE、* [INSTALLDIR] \Common7\IDE\PublicAssemblies</em>或 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*下的 Visual Studio 核心元件到達.

## <a name="change-reduce-registry-impact"></a>更改降低登錄影響

### <a name="global-com-registration"></a>全域 COM 註冊

* 先前，Visual Studio 在 HKEY_CLASSES_ROOT 和 HKEY_LOCAL_MACHINE hive 中安裝了許多登錄機碼，以支援原生 COM 註冊。 為了消除這種影響，Visual Studio 現在會使用[COM 元件的免註冊啟用](https://msdn.microsoft.com/library/ms973913.aspx)。
* 因此，Visual Studio 預設不會再安裝% ProgramFiles （x86）% \ Common Files\Microsoft Shared\MSEnv 下大部分的 TLB/.OLB/DLL 檔案。 這些檔案現在會安裝在 [INSTALLDIR] 底下，並提供 Visual Studio 主機進程所使用的對應免註冊 COM 資訊清單。
* 因此，依賴全域 COM 註冊 Visual Studio COM 介面的外部程式碼將不再找到這些註冊。 在 Visual Studio 程式中執行的程式碼不會看到差異。

### <a name="visual-studio-registry"></a>Visual Studio 登錄

* 先前，Visual Studio 在 Visual Studio 特定的機碼下，將許多登錄機碼安裝到系統的**HKEY_LOCAL_MACHINE**和**HKEY_CURRENT_USER** hive 中：

  * **HKLM\Software\Microsoft\VisualStudio\{版本}** ：MSI 安裝程式和個別電腦擴充功能所建立的登錄機碼。
  * **HKCU\Software\Microsoft\VisualStudio\{版本}** ：Visual Studio 所建立的登錄機碼，用來儲存使用者特定的設定。
  * **HKCU\Software\Microsoft\VisualStudio\{版本} _Config**：上述 Visual Studio HKLM 金鑰的複本，加上由擴充功能與 *.pkgdef*檔案合併的登錄機碼。

* 為了降低對登錄的影響，Visual Studio 現在會使用[RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya)函數，將登錄機碼儲存在 *[VSAPPDATA] \privateregistry.bin*下的私用二進位檔案中。 系統登錄中只會保留非常少量的 Visual Studio 特定索引鍵。
* 在 Visual Studio 進程內執行的現有程式碼不會受到影響。 Visual Studio 會將 HKCU Visual Studio 特有金鑰下的所有登錄作業重新導向至私人登錄。 讀取和寫入其他登錄位置將會繼續使用系統登錄。
* 外部程式碼將需要從這個檔案載入和讀取，以進行 Visual Studio 登錄專案。

### <a name="react-to-this-breaking-change"></a>回應這種重大變更

* 外部程式碼也應該轉換為使用 COM 元件的免註冊啟用。
* 外部元件可以[遵循這裡的指引](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)來尋找 Visual Studio 位置。
* 我們建議外部元件使用[外部設定管理員](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager)，而不是直接讀取/寫入 Visual Studio 登錄機碼。
* 檢查您的擴充功能所使用的元件是否可能已實作為註冊的另一個技術。 例如，偵錯工具延伸模組可能能夠利用新的[MSVSMON JSON 檔案 COM 註冊](migrate-debugger-COM-registration.md)。
