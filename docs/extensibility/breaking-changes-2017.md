---
title: 視覺工作室 2017 擴展性的突發變化
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739979"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 擴充性的變化

Visual Studio 2017 提供了[更快、更輕巧的 Visual Studio 安裝體驗](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer),減少了 Visual Studio 對使用者系統的影響,同時為使用者提供了對已安裝工作負載和功能的更多選擇。 為了支援這些改進,我們對擴充性模型進行了更改,包括一些重大更改。 本文介紹了這些更改的技術細節,以及可以採取哪些措施來解決這些問題。

> [!NOTE]
> 某些資訊是時間點實現詳細資訊,以後可能會更改。

## <a name="changes-affecting-vsix-format-and-installation"></a>影響 VSIX 格式與安裝的變更

Visual Studio 2017 引入了 VSIX v3(版本 3)格式,以支援輕量級安裝體驗。

對 VSIX 格式的變更包括:

* 設置先決條件聲明。 為了兌現輕巧、快速安裝的 Visual Studio 的承諾,安裝程式現在為使用者提供了更多的配置選項。 因此,為了確保安裝擴展所需的功能和元件,擴展需要聲明其依賴項。

  * Visual Studio 2017 安裝程式自動提供為使用者獲取和安裝必要的元件,作為安裝擴展的一部分。
  * 嘗試安裝未使用新的 VSIX v3 格式建構的擴展時,即使使用者在其清單中標記為目標版本 15.0,也會收到警告。

* VSIX 格式的增強功能。 為了提供同樣支援並行安裝的 Visual Studio[的低影響安裝](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install),我們不再將大多數配置數據保存到系統註冊表,並且將特定於 Visual Studio 的程式集移出 GAC。 我們還增加了 VSIX 格式和 VSIX 安裝引擎的功能,允許您使用它,而不是 MSI 或 EXE 來安裝某些安裝類型的擴展。

新功能包括:

* 註冊到指定的可視化工作室實例。
* 延伸[資料夾外安裝](set-install-root.md)。
* 檢測處理器架構。
* 依賴於語言分離的語言包。
* 安裝與[NGEN 支援](ngen-support.md)。

## <a name="build-an-extension-for-visual-studio-2017"></a>為 2017 年可視化工作室構建擴展

用於創作新的 VSIX v3 清單格式的設計器工具可在 Visual Studio 2017 中使用。 有關使用設計器工具或對專案和清單進行手動更新以開發 VSIX v3 擴展的詳細資訊,請參閱隨附的文檔[:將擴充性專案遷移到 Visual Studio 2017。](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="change-visual-studio-user-data-path"></a>變更:視覺化工作室使用者資料路徑

以前,每台電腦上只能安裝一個 Visual Studio 的每個主要版本。 為了支援 Visual Studio 2017 的並行安裝,Visual Studio 的多個用戶數據路徑可能存在於使用者的電腦上。

應在可視化工作室進程內運行的代碼更新為使用可視化工作室設置管理器。 運行在 Visual Studio 進程之外的代碼可以[按照此處的指導](locating-visual-studio.md)找到特定 Visual Studio 安裝的用戶路徑。

## <a name="change-global-assembly-cache-gac"></a>變更:全域程式集快取 (GAC)

大多數 Visual Studio 核心元件不再安裝到 GAC 中。 進行了以下更改,以便在 Visual Studio 進程中運行的代碼在執行時仍可以找到所需的程式集。

> [!NOTE]
> [INSTALLDIR] 下面是指可視化工作室的安裝根目錄。 *VSIXInstaller.exe*將自動填充此內容,但要編寫自定義部署代碼,請閱讀[定位 Visual Studio](locating-visual-studio.md)。

* 只安裝到 GAC 中的程式集:

  這些程式集現在安裝在<em>[INSTALLDIR]_Common7_IDE、[INSTALLDIR]_\*公共程式集</em>或 *[INSTALLDIR]_通用7_IDE_私有程式集*下。 這些資料夾是可視化工作室進程探測路徑的一部分。

* 安裝在非偵測路徑與 GAC 中的程式集:

  * GAC 中的副本從設置中刪除。
  * 添加了 *.pkgdef*檔以指定程式集的代碼基條目。

    例如：

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    在執行時,Visual Studio pkgdef 子系統將這些條目合併到 Visual Studio 行程的執行時設定檔(*在 [VSAPPDATA]_devenv.exe.config*下)作為[`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element)元素。 這是讓 Visual Studio 進程找到程式集的推薦方法,因為它可以避免通過探測路徑進行搜索。

### <a name="reacting-to-this-breaking-change"></a>應對這一重大變革

* 如果您的延伸在視覺化工作室行程中執行:

  * 您的代碼將能夠找到 Visual Studio 核心程式集。
  * 如有必要,請考慮使用 *.pkgdef*檔指定程式集的路徑。

* 如果您的延伸在視覺化工作室行程外執行:

  請考慮在<em>\*[INSTALLDIR]_Common7_IDE 下查找 Visual Studio 核心程式集,[INSTALLDIR]_公共程式集\IDE_公共程式集</em>或 *[INSTALLDIR]\通用7_IDE_使用*配置檔或程式集解析器的私有程式集。

## <a name="change-reduce-registry-impact"></a>變更:減少註冊表影響

### <a name="global-com-registration"></a>全球註冊註冊

* 以前,Visual Studio 在HKEY_CLASSES_ROOT中安裝了許多註冊表項,HKEY_LOCAL_MACHINE配置單元以支援本機 COM 註冊。 為了消除這種影響,Visual Studio 現在使用[COM 元件的無註冊啟動](https://msdn.microsoft.com/library/ms973913.aspx)。
* 因此,在 %程式檔 (x86)%%下的大多數 TLB / OLB / DLL 檔都不再預設由 Visual Studio 安裝。 這些檔現在安裝在 [INSTALLDIR] 下,與 Visual Studio 主機進程使用的相應無註冊 COM 清單一起安裝。
* 因此,依賴於 Visual Studio COM 介面的全域 COM 註冊的外部代碼將不再找到這些註冊。 在 Visual Studio 進程內執行的代碼不會看到差異。

### <a name="visual-studio-registry"></a>視覺工作室註冊表

* 以前,Visual Studio 在系統的**HKEY_LOCAL_MACHINE**中安裝了許多註冊表項,並在特定於 Visual Studio 的金鑰下**HKEY_CURRENT_USER**配置單元:

  * **HKLM_軟體[微軟]VisualStudio\{版本*:** 由 MSI 安裝程式和每台計算機擴展創建的註冊表項。
  * **HKCU_軟體[微軟]VisualStudio\{版本*:Visual**Studio 創建的註冊表項,用於存儲特定於用戶的設置。
  * **HKCU_軟體[微軟]VisualStudio\{版本]_Config:** 上面的 Visual Studio HKLM 密鑰的副本,以及按擴展名從 *.pkgdef*文件合併的註冊表項。

* 為了減少對註冊表的影響,Visual Studio 現在使用[RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya)函數在 *[VSAPPDATA]\privateregistry.bin*下將註冊表項存儲在私有二進位檔案中。 系統註冊表中僅保留極少數特定於 Visual Studio 的密鑰。
* 在可視化工作室進程內運行的現有代碼不受影響。 Visual Studio 會將 HKCU 視覺工作室特定密鑰下的所有註冊表操作重定向到專用註冊表。 讀取和寫入其他註冊表位置將繼續使用系統註冊表。
* 外部代碼將需要載入和讀取此檔為 Visual Studio 註冊表條目。

### <a name="react-to-this-breaking-change"></a>應對這一重大變革

* 外部代碼也應轉換為對 COM 元件使用無註冊啟動。
* 外部元件可以[按照此處的指導](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)找到 Visual Studio 位置。
* 我們建議外部元件使用[外部設置管理員](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager),而不是直接讀取/寫入 Visual Studio 註冊表項。
* 檢查擴展正在使用的元件是否實現了另一種註冊技術。 例如,除錯器延伸可能能夠利用新的[msvsmon JSON 檔案 COM 註冊](migrate-debugger-COM-registration.md)。
