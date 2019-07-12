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
ms.openlocfilehash: 0cc62384f2a413362f53ed0626031501e163d6a4
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823812"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>在 Visual Studio 2017 擴充性的變更

Visual Studio 2017 提供[更快速、 輕量的 Visual Studio 安裝經驗](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer)縮減 Visual Studio 的影響，在使用者系統上同時工作負載，以及功能讓使用者更佳的選擇安裝。 若要支援這些改進，我們已變更的擴充性模型，包括一些突破性的變革。 這篇文章描述這些變更，可以做什麼來解決這些技術的詳細的資料。

> [!NOTE]
> 某些資訊的時間點實作詳細資料，並稍後可能會變更。

## <a name="changes-affecting-vsix-format-and-installation"></a>變更會影響的 VSIX 格式和安裝

Visual Studio 2017 導入 VSIX v3 （第 3 版） 格式，以支援輕量級安裝體驗。

VSIX 格式所做變更包括：

* 安裝程式必要條件的宣告。 若要履行承諾的輕量型、 快速安裝 Visual Studio，安裝程式現在會對使用者提供更多組態選項。 如此一來，若要確保安裝的功能和擴充功能所需的元件，延伸模組需要宣告其相依性。

  * Visual Studio 2017 安裝程式會自動提供要取得並安裝必要元件，以使用者做為安裝延伸模組的一部分。
  * 嘗試安裝不是使用新的 VSIX v3 格式，即使它們已經標示為目標版本 15.0 其資訊清單中的延伸模組時，也會警告使用者。

* VSIX 格式的增強的功能。 履行[低影響安裝](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install)也支援並排顯示安裝的 Visual studio，我們不會再將大部分的設定資料儲存至系統登錄中，移出 GAC 的 Visual Studio 特定組件。 我們也會增加的功能的 VSIX 格式和 VSIX 安裝引擎，可讓您使用它而 MSI 或 EXE 安裝您的擴充功能，某些安裝類型。

新功能包括：

* 註冊到指定的 Visual Studio 執行個體。
* 安裝外的[延伸模組資料夾](set-install-root.md)。
* 偵測的處理器架構。
* 語言分隔的語言套件相依性。
* 與安裝[NGEN 支援](ngen-support.md)。

## <a name="build-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 建置的擴充功能

VSIX v3 中的資訊清單格式工具來撰寫新的設計工具位於 Visual Studio 2017。 請參閱隨附的文件[How to:將擴充性專案移轉至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)如需有關使用設計工具，或對專案進行手動更新及開發 VSIX v3 擴充功能的資訊清單。

## <a name="change-visual-studio-user-data-path"></a>變更：Visual Studio 使用者資料路徑

先前，只有一個安裝的每個主要版本的 Visual Studio 可能存在的每部機器上。 若要支援的 Visual Studio 2017 的並存安裝，使用者電腦上可能存在的 Visual Studio 的多個使用者資料路徑。

在 Visual Studio 處理序內執行的程式碼應該更新為使用 Visual Studio 設定管理員中。 在 Visual Studio 處理序外執行的程式碼可以找到特定的 Visual Studio 安裝的使用者路徑[只要遵循這裡的指引](locating-visual-studio.md)。

## <a name="change-global-assembly-cache-gac"></a>變更：全域組件快取 (GAC)

大部分的 Visual Studio 核心組件不會再安裝到 GAC。 已進行下列變更，以便在 Visual Studio 處理序中執行的程式碼仍在執行階段尋找必要的組件。

> [!NOTE]
> [INSTALLDIR] 下面是指 Visual Studio 安裝根目錄。 *VSIXInstaller.exe*將會自動填入此項目，但若要撰寫自訂部署程式碼，請閱讀[找出 Visual Studio](locating-visual-studio.md)。

* 只安裝至 GAC 的組件：

  這些組件現在會安裝下<em>[INSTALLDIR] \Common7\IDE\*，* [INSTALLDIR] \Common7\IDE\PublicAssemblies</em>或是 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*。 這些資料夾是 Visual Studio 處理序的探查路徑的一部分。

* 已安裝到非探查的路徑及 GAC 的組件：

  * 在 GAC 中的複本已從安裝程式移除。
  * A *.pkgdef*檔案加入至指定組件的程式碼基底項目。

    例如：

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    在執行階段，Visual Studio pkgdef 子系統合併至 Visual Studio 處理序的執行階段組態檔的這些項目 (底下 *[VSAPPDATA]\devenv.exe.config*) 作為[ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element)項目。 這是讓 Visual Studio 程序尋找您的組件，因為它可避免探查路徑中搜尋的建議的方式。

### <a name="reacting-to-this-breaking-change"></a>回應這項重大變更

* 如果您的延伸模組在 Visual Studio 處理序內執行：

  * 您的程式碼都能夠找到 Visual Studio 核心組件。
  * 請考慮使用 *.pkgdef*來指定您的組件的路徑，如有必要的檔案。

* 如果您的延伸模組在 Visual Studio 處理序之外執行：

  尋找在 Visual Studio 核心組件，請考慮<em>[INSTALLDIR] \Common7\IDE\*，* [INSTALLDIR] \Common7\IDE\PublicAssemblies</em>或 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*使用組態檔案或組件解析程式。

## <a name="change-reduce-registry-impact"></a>變更：減少登錄的影響

### <a name="global-com-registration"></a>全域 COM 註冊

* 過去，Visual Studio 安裝 HKEY_CLASSES_ROOT 和 HKEY_LOCAL_MACHINE 登錄區，以支援原生 COM 註冊許多的登錄機碼。 若要消除這種影響，Visual Studio 現在會使用[COM 元件的免註冊啟用](https://msdn.microsoft.com/library/ms973913.aspx)。
* 如此一來，大部分的 TLB / OLB / 不再根據預設，Visual Studio 安裝在 %programfiles (x86) %\Common Files\Microsoft Shared\MSEnv 的 DLL 檔案。 與 Visual Studio 主機處理序所使用的對應免註冊 COM 資訊清單，這些檔案現在會安裝 [INSTALLDIR] 底下。
* 如此一來，依賴全域 Visual Studio COM 介面的 COM 註冊的外部程式碼將不再會尋找這些註冊。 在 Visual Studio 處理序內執行的程式碼看不到的差異。

### <a name="visual-studio-registry"></a>Visual Studio 登錄

* 之前，Visual Studio 安裝到系統的許多的登錄機碼**HKEY_LOCAL_MACHINE**並**HKEY_CURRENT_USER** hive Visual Studio 特定機碼下：

  * **HKLM\Software\Microsoft\VisualStudio\{版本}** :MSI 安裝程式和每個機器擴充功能所建立的登錄機碼。
  * **HKCU\Software\Microsoft\VisualStudio\{版本}** :Visual Studio 來儲存使用者專屬設定所建立的登錄機碼。
  * **HKCU\Software\Microsoft\VisualStudio\{版本} _Config**:從一份 Visual Studio HKLM 索引鍵，再加上的登錄機碼合併 *.pkgdef*延伸模組的檔案。

* 若要減少對登錄的影響，Visual Studio 現在會使用[RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya)將登錄機碼下的私用二進位檔案中的函式 *[VSAPPDATA]\privateregistry.bin*。 只有非常少數的 Visual Studio 特定索引鍵會保留在系統登錄中。
* 在 Visual Studio 處理序內執行的現有程式碼不會受到影響。 Visual Studio 會在 HKCU Visual Studio 特定機碼下的所有登錄作業重新都導向的私人登錄。 讀取和寫入登錄中的其他位置將會繼續使用系統登錄。
* 外部程式碼必須載入，並從這個檔案的 Visual Studio 登錄項目讀取。

### <a name="react-to-this-breaking-change"></a>因應這項重大變更

* 外部程式碼應該轉換成的 COM 元件，也使用免註冊啟用。
* 外部元件可以找到 Visual Studio 位置[只要遵循這裡的指引](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)。
* 我們建議使用的外部元件[外部 Settings Manager](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager)而不是直接向 Visual Studio 登錄機碼的讀取/寫入。
* 請檢查您的延伸模組所使用的元件是否已實作註冊的另一種技術。 比方說，可能可以利用新的偵錯工具擴充功能[msvsmon JSON 檔案 COM 註冊](migrate-debugger-COM-registration.md)。
