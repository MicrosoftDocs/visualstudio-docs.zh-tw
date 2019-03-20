---
title: 並存安裝 Visual Studio 版本
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1f2969fe93ab2623b1f8406f6eaa0ce35c454202
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160533"
---
# <a name="install-visual-studio-versions-side-by-side"></a>並存安裝 Visual Studio 版本

您可在已安裝舊版或新版 Visual Studio 的電腦上安裝 Visual Studio。

::: moniker range="vs-2017"

並存安裝多個版本之前，請先檢閱下列狀況：

* 如果您使用 Visual Studio 2017 開啟於 Visual Studio 2015 所建立的解決方案，只要未實作 Visual Studio 2017 特定的任何功能，稍後就可以在舊版中開啟和修改該方案。

* 如果您嘗試使用 Visual Studio 2017 開啟使用 Visual Studio 2015 或以前版本所建立的方案，可能需要修改專案和檔案，才能與 Visual Studio 2017 相容。 如需詳細資訊，請參閱[移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)頁面。

::: moniker-end

::: moniker range=">= vs-2019"

並存安裝多個版本之前，請先檢閱下列狀況：

* 如果您使用 Visual Studio 2019 開啟於 Visual Studio 2017 所建立的解決方案，只要未實作 Visual Studio 2019 特定的任何功能，稍後就可以在舊版中開啟和修改該方案。

* 如果您嘗試使用 Visual Studio 2019 開啟使用 Visual Studio 2017 或以前版本所建立的方案，可能需要修改專案和檔案，才能與 Visual Studio 2019 相容。 如需詳細資訊，請參閱[移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-upgrade-visual-studio-projects-2019.md)頁面。

::: moniker-end

* 如果在已經安裝多個 Visual Studio 版本的電腦上將其中一個版本解除安裝，則會移除所有版本的 Visual Studio 檔案關聯。

* Visual Studio 不會自動升級擴充功能，因為並非所有擴充功能都相容。 您必須從 [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) 或軟體發行者重新安裝延伸模組。

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework 的版本和並存安裝

Visual Basic、Visual C# 或 Visual F# 專案中 [專案設計工具]  使用 [目標 Framework]  選項，指定專案的目標 .NET Framework 版本。 對於 C++ 專案，您可以手動修改 .vcxproj 檔案來變更目標 Framework。 如需詳細資訊，請參閱 [.NET Framework 的版本相容性](/dotnet/framework/migration-guide/version-compatibility)頁面。

當您建立專案時，您可以在 [新增專案]  對話方塊的 [.NET Framework]  清單中指定專案的目標 .NET Framework 版本。

如需語言特定的資訊，請參閱下表中適當的主題。

::: moniker range="vs-2017"

| 語言 | 主題 |
|--------------|-----------|
| Visual Basic | [專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [在 Visual Studio 中使用 Visual F# 進行開發](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [如何：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md?view=vs-2017)
* [移植、移轉及升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [建置 C/C++ 隔離應用程式和並存組件](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| 語言 | 主題 |
|--------------|-----------|
| Visual Basic | [專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2019) |
| Visual C# | [專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2019) |
| Visual F# | [在 Visual Studio 中使用 Visual F# 進行開發](../ide/fsharp-visual-studio.md?view=vs-2019) |
| C++ | [如何：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md?view=vs-2019)
* [移植、移轉及升級 Visual Studio 專案](../porting/port-migrate-upgrade-visual-studio-projects-2019.md)
* [建置 C/C++ 隔離應用程式和並存組件](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end