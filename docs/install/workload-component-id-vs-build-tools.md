---
title: "Visual Studio Build Tools 2017 工作負載和元件識別碼 | Microsoft Docs"
description: "使用 Visual Studio 工作負載和元件識別碼來建置傳統 Windows 型應用程式"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/30/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 96018963278cd1d53b226473baade41da1e98111
ms.openlocfilehash: 86ac70e66b581a2e70dc8efa185b1e61d7d0204c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio Build Tools 2017 元件目錄

此頁面上的表格列出您可以用來透過命令列安裝 Visual Studio 的識別碼。 請注意，我們將會在發行 Visual Studio 更新時新增其他元件。

此外，也請注意此頁面的下列相關注意事項：

* 每個工作負載都有自己的小節 (後面接著工作負載識別碼)，以及一張工作負載可用元件的表格。
* 安裝工作負載時，預設會安裝「必要」元件。 您也可以選擇安裝「建議」元件和「選擇性」元件。
* 我們還新增了一個章節，當中列出不屬於任何工作負載的額外元件。

如需有關如何使用這些識別碼的詳細資訊，請參閱[使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 頁面。 而如需其他產品的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。

## <a name="msbuild-tools"></a>MSBuild 工具

**識別碼：**Microsoft.VisualStudio.Workload.MSBuildTools

**描述：**提供建置 MSBuild 型應用程式所需的工具。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | 15.0.26711.1 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# 編譯器 | 15.0.26606.0 | Optional

## <a name="net-core-build-tools"></a>.NET Core 建置工具

**識別碼：** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**描述：**建置 .NET Core 應用程式的工具。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | .NET Core 1.0 - 1.1 開發工具 | 15.0.26606.0 | 必要

## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**識別碼：**Microsoft.VisualStudio.Workload.VCTools

**描述：**使用 Visual C++ 工具組、ATL 以及 MFC 和 C++/CLI 這類選用功能的強大能力，來建置傳統 Windows 型應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools 核心功能 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 可轉散發更新 | 15.0.26606.0 | 必要
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 15.0.26621.2 | 必要
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.0.26711.1 | 建議
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.VC.CMake.Project | 適用於 CMake 的 Visual C++ 工具 | 15.0.26621.2 | 建議
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 工具組 (x86、x64) | 15.0.26621.2 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | 適用於 Desktop C++ x86 和 x64 的 Windows 10 SDK (10.0.15063.0) | 15.0.26621.2 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C#、VB、JS | 15.0.26621.2 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C++ | 15.0.26621.2 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 與網頁程式開發 | 15.0.26606.0 | 建議
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.140 | 適用於桌上型電腦 (x86、x64) 的 VC++ 2015.3 v140 工具組 | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL 支援 | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC 與 ATL 支援 (x86 及 x64) | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (實驗性) | 15.0.26724.1 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 支援 | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 標準程式庫的模組 (實驗性) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK 與 UCRT SDK | 15.0.26208.0 | Optional

## <a name="web-development-build-tools"></a>Web 程式開發建置工具

**識別碼：**Microsoft.VisualStudio.Workload.WebBuildTools

**描述：**用於建置 Web 應用程式的 MSBuild 工作和目標。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.0.26621.2 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.0.26606.0 | 必要
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Web 程式開發建置工具 | 15.0.26323.1 | 必要
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 15.0.26621.2 | 建議
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.0.26621.2 | 建議
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.0.26621.2 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.0.26621.2 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.0.26621.2 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 15.0.26606.0 | 建議
Microsoft.Net.Core.Component.SDK | .NET Core 1.0 - 1.1 開發工具 | 15.0.26606.0 | 建議
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開發工具 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 15.0.26606.0 | Optional

## <a name="unaffiliated-components"></a>非附屬元件

這些是未隨附於任何工作負載但可選取來作為個別元件的元件。

元件識別碼 | 名稱 | 版本
--- | --- | ---
N/A | N/A | N/A

## <a name="see-also"></a>請參閱

* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)

