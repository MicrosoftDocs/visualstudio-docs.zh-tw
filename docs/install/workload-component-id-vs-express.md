---
title: Visual Studio Desktop Express 工作負載和元件識別碼
titleSuffix: ''
description: 使用工作負載和元件識別碼透過命令列安裝 Visual Studio，或是在 VSIX 資訊清單中指定為相依性
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 21735c82a318623758f1980a1865a543adde121e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881798"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Visual Studio Desktop Express 元件目錄

此頁面上的表格列出您可以用來透過命令列安裝 Visual Studio 的識別碼，或是您可以在 VSIX 資訊清單中指定為相依性的識別碼。 請注意，我們將會在發行 Visual Studio 更新時新增其他元件。

此外，也請注意此頁面的下列相關注意事項：

* 每個工作負載都有自己的小節 (後面接著工作負載識別碼)，以及一張工作負載可用元件的表格。
* 安裝工作負載時，預設會安裝「必要」元件。
* 如果您選擇，也可以安裝 **建議** 的和 **選用** 的元件。
* 我們還新增了一個章節，當中列出不屬於任何工作負載的額外元件。

當您在 VSIX 資訊清單中設定相依性時，必須僅指定「元件識別碼」。 請使用此頁面上的表格來決定我們的最基本元件相依性。 在某些情況下，這可能意謂著您僅指定一個來自工作負載的元件。 在其他情況下，則可能意謂著您指定來自單一工作負載的多個元件，或來自多個工作負載的多個元件。 如需詳細資訊，請參閱[如何︰將擴充性專案移轉至 Visual Studio 2017 (英文)](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 頁面。

如需有關如何使用這些識別碼的詳細資訊，請參閱[使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 頁面。 而如需其他產品的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。

## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**ID：** Microsoft.VisualStudio.Workload.WDExpress

**說明：** 透過語法感知程式碼編輯、原始程式碼控制以及工作項目管理，建置原生和 Managed 應用程式，例如 WPF、WinForms 和 Win32。 包含 C#、Visual Basic 和 Visual C++ 的支援。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.HelpViewer | 說明檢視器 | 15.6.27323.2 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Component.VC.Runtime.OSSupport | UWP 的 Visual C++ 執行階段 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 必要
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 核心編輯器 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 15.0.26621.2 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 必要
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | 必要
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 支援 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.VC.Tools.ARM | 適用於 ARM 的 Visual C++ 編譯器與程式庫 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | 適用於 ARM64 的 Visual C++ 編譯器與程式庫 | 15.9.28230.55 | 必要
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | 必要

## <a name="unaffiliated-components"></a>非附屬元件

這些是未隨附於任何工作負載但可選取來作為個別元件的元件。

元件識別碼 | 名稱 | 版本
--- | --- | ---
n/a | n/a | n/a

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
