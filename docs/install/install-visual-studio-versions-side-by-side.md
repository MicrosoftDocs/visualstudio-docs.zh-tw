---
title: 並存安裝 Visual Studio 版本
description: 瞭解如何在已安裝舊版或更新版本 Visual Studio 的電腦上安裝 Visual Studio。
ms.custom: SEO-VS-2020
ms.date: 03/29/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: j-martens
ms.author: jmartens
manager: jmartens
ms.openlocfilehash: c8d1da5f8cb5c237fe02a41197825d5086fc6471
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307017"
---
# <a name="install-visual-studio-versions-side-by-side"></a>並存安裝 Visual Studio 版本

您可在已安裝舊版或新版 Visual Studio 的電腦上安裝 Visual Studio。

::: moniker range="vs-2017"

並存安裝多個版本之前，請先檢閱下列狀況：

* 如果您使用 Visual Studio 2017 開啟於 Visual Studio 2015 所建立的解決方案，只要未實作 Visual Studio 2017 特定的任何功能，稍後就可以在舊版中開啟和修改該方案。

* 如果您嘗試使用 Visual Studio 2017 開啟使用 Visual Studio 2015 或以前版本所建立的方案，可能需要修改專案和檔案，才能與 Visual Studio 2017 相容。 如需詳細資訊，請參閱[移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)頁面。

::: moniker-end

::: moniker range="vs-2019"

並存安裝多個版本之前，請先檢閱下列狀況：

* 如果您使用 Visual Studio 2019 開啟於 Visual Studio 2017 所建立的解決方案，只要未實作 Visual Studio 2019 特定的任何功能，稍後就可以在舊版中開啟和修改該方案。

* 如果您嘗試使用 Visual Studio 2019 開啟使用 Visual Studio 2017 或以前版本所建立的方案，可能需要修改專案和檔案，才能與 Visual Studio 2019 相容。 如需詳細資訊，請參閱[移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)頁面。

::: moniker-end

::: moniker range=">=vs-2022"

並存安裝多個版本之前，請先檢閱下列狀況：

* 如果您使用 Visual Studio 2022 來開啟以 Visual Studio 2017 或 Visual Studio 2019 建立的方案，您可以稍後在先前的版本中開啟和修改解決方案，只要您尚未執行 Visual Studio 2022 的特定功能。

* 如果您嘗試使用 Visual Studio 2022 來開啟以 Visual Studio 2019 或更早版本建立的方案，可能需要修改專案和檔案，才能與 Visual Studio 2022 相容。 如需詳細資訊，請參閱[移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)頁面。

::: moniker-end

* 如果在已經安裝多個 Visual Studio 版本的電腦上將其中一個版本解除安裝，則會移除所有版本的 Visual Studio 檔案關聯。

* Visual Studio 不會自動升級擴充功能，因為並非所有擴充功能都相容。 您必須從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 或軟體發行者重新安裝延伸模組。

## <a name="install-minor-visual-studio-versions-side-by-side"></a>並存安裝次要 Visual Studio 版本

從 Visual Studio 的次要版本升級到下一個版本時，Visual Studio 安裝程式預設會將您目前的安裝更新為該通道中的最新版本。 例如，假設16.9.4 剛發行。 安裝程式會嘗試使用16.9.4 取代您目前的 16.9.3 (或較低的) 安裝，因為這兩個版本都是 [Visual Studio 2019 發行通道](/visualstudio/productinfo/release-rhythm)的一部分。 在更新期間以較新的版本取代較舊的版本，有助於確保舊版 Visual Studio 不佔用您電腦上的空間。 不過，在某些特定情況下，將不同的次要發行版本 Visual Studio 並存安裝可能會很有説明。 例如，您可能想要在同一部電腦上同時有16.9.3 和16.9.4。

::: moniker range="vs-2017"

1. 針對您想要與現有 Visual Studio 版本並存安裝的版本，從 [Visual Studio [舊版](https://visualstudio.microsoft.com/vs/older-downloads/) ] 頁面下載最新的 Visual Studio 2017 15.9 版的啟動載入器。

1. 以系統管理員模式開啟命令提示字元。 若要這樣做，請開啟 Windows [開始] 功能表，輸入 "cmd"，以滑鼠右鍵按一下命令提示字元搜尋結果，然後選取 [以 **系統管理員身分執行**]。 在命令提示字元中，將目錄變更為您 Visual Studio 啟動載入器檔案所在的資料夾。

1. 執行下列命令，指定安裝位置的新資料夾路徑，並以您要安裝的 Visual Studio 版本的適當啟動載入器名稱取代 .exe 的檔案名。 .exe 的檔案名應符合或類似于下列其中一個檔案：

   * vs_enterprise.exe (適用於 Visual Studio Enterprise)
   * vs_professional.exe (適用於 Visual Studio Professional)

1. 遵循安裝程式對話方塊來選取安裝所需的元件。 如需詳細資訊，請參閱 [安裝 Visual Studio](install-visual-studio.md#step-4---choose-workloads)。

::: moniker-end

::: moniker range="vs-2019"

1. 從 [ [下載] 頁面](https://visualstudio.microsoft.com/downloads) 下載 Visual Studio 2019 啟動載入器檔案，或 Visual Studio 從您要與現有 Visual Studio 版本並存安裝的次要版本的 [ [Visual Studio 2019 版本](/visualstudio/releases/2019/history#installing-an-earlier-release) ] 頁面下載。

1. 以系統管理員模式開啟命令提示字元。 若要這樣做，請開啟 Windows [開始] 功能表，輸入 "cmd"，以滑鼠右鍵按一下命令提示字元搜尋結果，然後選取 [以 **系統管理員身分執行**]。 在命令提示字元中，將目錄變更為您 Visual Studio 啟動載入器檔案所在的資料夾。

1. 執行下列命令，指定安裝位置的新資料夾路徑，並以您要安裝的 Visual Studio 版本的適當啟動載入器名稱取代 .exe 的檔案名。 .exe 的檔案名應符合或類似于下列其中一個檔案：

   * vs_enterprise.exe (適用於 Visual Studio Enterprise)
   * vs_professional.exe (適用於 Visual Studio Professional)
   * vs_community.exe (適用於 Visual Studiofor Community)

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

1. 遵循安裝程式對話方塊來選取安裝所需的元件。 如需詳細資訊，請參閱 [安裝 Visual Studio](install-visual-studio.md#step-4---choose-workloads)。

::: moniker-end

::: moniker range=">=vs-2022"

1. 從 [ [下載] 頁面](https://visualstudio.microsoft.com/downloads) 下載 Visual Studio 2022 啟動載入器檔案，或 Visual Studio 從您要與現有 Visual Studio 版本並存安裝的次要版本的 [ [Visual Studio 2022 版本](/visualstudio/releases/2022/history) ] 頁面下載。

1. 以系統管理員模式開啟命令提示字元。 若要這樣做，請開啟 Windows [開始] 功能表，輸入 "cmd"，以滑鼠右鍵按一下命令提示字元搜尋結果，然後選取 [以 **系統管理員身分執行**]。 在命令提示字元中，將目錄變更為您 Visual Studio 啟動載入器檔案所在的資料夾。

1. 執行下列命令，指定安裝位置的新資料夾路徑，並以您要安裝的 Visual Studio 版本的適當啟動載入器名稱取代 .exe 的檔案名。 .exe 的檔案名應符合或類似于下列其中一個檔案：

   * vs_enterprise.exe (適用於 Visual Studio Enterprise)
   * vs_professional.exe (適用於 Visual Studio Professional)
   * vs_community.exe (適用於 Visual Studiofor Community)

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files\Microsoft Visual Studio\<AddNewPath>"
   ```

1. 遵循安裝程式對話方塊來選取安裝所需的元件。 如需詳細資訊，請參閱 [安裝 Visual Studio](install-visual-studio.md#step-4---choose-workloads)。
   
::: moniker-end

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework 的版本和並存安裝

Visual Basic、Visual C# 或 Visual F# 專案中 [專案設計工具]  使用 [目標 Framework]  選項，指定專案的目標 .NET Framework 版本。 對於 C++ 專案，您可以手動修改 .vcxproj 檔案來變更目標 Framework。 如需詳細資訊，請參閱 [.NET Framework 的版本相容性](/dotnet/framework/migration-guide/version-compatibility)頁面。

當您建立專案時，您可以在 [新增專案]  對話方塊的 [.NET Framework]  清單中指定專案的目標 .NET Framework 版本。

如需語言特定的資訊，請參閱下表中適當的主題。

::: moniker range="vs-2017"

| 語言     | 主題                                                                                                                                                   |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C#    | [專案設計工具，應用程式頁 (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true)                 |
| Visual F#    | [在 Visual Studio 中使用 Visual F# 進行開發](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true)                                               |
| C++          | [作法：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/)                         |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [移植、遷移及升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [建置 C/C++ 隔離應用程式和並存組件](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| 語言     | 主題                                                                                                                           |
|--------------|---------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)         |
| Visual C#    | [專案設計工具，應用程式頁 (C#)](../ide/reference/application-page-project-designer-csharp.md)                         |
| Visual F#    | [在 Visual Studio 中使用 Visual F# 進行開發](../ide/fsharp-visual-studio.md)                                                       |
| C++          | [作法：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [移植、遷移及升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [建置 C/C++ 隔離應用程式和並存組件](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
