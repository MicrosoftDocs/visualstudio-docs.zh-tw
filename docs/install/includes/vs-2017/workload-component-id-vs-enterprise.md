---
title: Visual Studio Enterprise 2017 工作負載和元件識別碼
titleSuffix: ''
description: 使用工作負載和元件識別碼透過命令列安裝 Visual Studio，或是在 VSIX 資訊清單中指定為相依性
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: d250a1b00c65c24d38a47f7a9a2791f9ef7a2e82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881829"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2017"></a>Visual Studio 核心編輯器 (隨附於 Visual Studio Enterprise 2017)

**識別碼：** Microsoft.VisualStudio.Workload.CoreEditor

**描述：** Visual Studio 核心殼層體驗，包括語法感知程式碼編輯、原始程式碼控制及工作項目管理。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 核心編輯器 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | C++ 使用者的 Visual Studio 起始畫面 | 15.0.27128.1 | 選擇性

## <a name="azure-development"></a>Azure 開發

**識別碼：** Microsoft.VisualStudio.Workload.Azure

**描述：** 用於開發雲端 App、建立資源及建置包含 Docker 支援之容器的 Azure SDK、工具及專案。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 必要
Component.Microsoft.VisualStudio.Web.AzureFunctions | Microsoft Azure WebJobs 工具 | 15.7.27617.1 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 15.8.27705.0 | 必要
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 必要
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Component.NetFX.Core.Runtime | .NET Core 執行階段 | 15.0.26208.0 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.NetCore.ComponentGroup.Web.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 15.9.28307.421 | 必要
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 15.9.28307.421 | 必要
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 15.8.27906.1 | 必要
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 容器開發工具 - 建置工具 | 15.7.27617.1 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 15.9.28307.421 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
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
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 必要
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Azure 開發必要條件 | 15.9.28107.0 | 必要
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Microsoft Azure WebJobs 工具 | 15.7.27617.1 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 15.9.28219.51 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 必要
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 與串流分析工具 | 15.9.28107.0 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.AspNet45 | 進階的 ASP.NET 功能 | 15.7.27625.0 | 建議
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | 15.7.27625.0 | 建議
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager 核心工具 | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric 工具 | 15.8.27825.0 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 15.7.27617.1 | 建議
Microsoft.VisualStudio.Component.Debugger.Snapshot | 快照集偵錯工具 | 15.8.28010.0 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | 建議
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure 雲端服務工具 | 15.0.26504.0 | 建議
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager 工具 | 15.0.27005.2 | 建議
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 開發工具 | 15.8.27825.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.NetCore.1x.ComponentGroup.Web | 適用於網路的 .NET Core 1.0 - 1.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0 開發工具 | 15.8.27729.1 | 選擇性
Microsoft.NetCore.ComponentGroup.Web | .NET Core 2.0 開發工具 | 15.7.27625.0 | 選擇性
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure 儲存體 AzCopy | 15.0.26906.1 | 選擇性
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | 選擇性

## <a name="data-storage-and-processing"></a>資料的儲存與處理

**識別碼：** Microsoft.VisualStudio.Workload.Data

**描述：** 使用 SQL Server、Azure Data Lake 或 Hadoop 來連線、開發及測試資料解決方案。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 建議
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 15.8.27705.0 | 建議
Component.Redgate.ReadyRoll | Redgate ReadyRoll Core | 1.17.18155.10346 | 建議
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt Core | 9.2.0.5601 | 建議
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 3.1.7.2062 | 建議
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 建議
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 與串流分析工具 | 15.9.28107.0 | 建議
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 建議
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 15.6.27406.0 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 15.9.28307.421 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 15.9.28307.421 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 15.9.28125.51 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 15.7.27617.1 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 15.8.27906.1 | 建議
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 容器開發工具 - 建置工具 | 15.7.27617.1 | 建議
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 建議
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 建議
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 15.0.26621.2 | 建議
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 建議
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 建議
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 15.8.27825.0 | 建議
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 15.9.28219.51 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 建議
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 15.8.27825.0 | 選擇性

## <a name="data-science-and-analytical-applications"></a>資料科學與分析應用程式

**識別碼：** Microsoft.VisualStudio.Workload.DataScience

**描述：** 用於建立資料科學應用程式的語言與工具，包括 Python、R 和 F#。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64 位元 (5.2.0) | 5.2.0 | 建議
Microsoft.Component.CookiecutterTools | Cookiecutter 範本支援 | 15.0.26621.2 | 建議
Microsoft.Component.PythonTools | Python 語言支援 | 15.0.26823.1 | 建議
Microsoft.Component.PythonTools.Web | Python Web 支援 | 15.9.28107.0 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 15.8.27825.0 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 建議
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.RHost | R 開發工具的執行階段支援 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.RTools | R 語言支援 | 15.0.26919.1 | 建議
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 建議
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 建議
Component.Anaconda2.x64 | Anaconda2 64 位元 (5.2.0) | 5.2.0 | 選擇性
Component.Anaconda2.x86 | Anaconda2 32 位元 (5.2.0) | 5.2.0 | 選擇性
Component.Anaconda3.x86 | Anaconda3 32 位元 (5.2.0) | 5.2.0 | 選擇性
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 15.6.27309.0 | 選擇性
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python 原生開發工具 | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Win81 | 圖形工具 Windows 8.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.VC.140 | 桌上型電腦版的 VC++ 2015.3 v14.00 (v140) 工具組 | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 15.0.26823.1 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | 選擇性

## <a name="net-desktop-development"></a>.NET 桌面開發

**識別碼：** Microsoft.VisualStudio.Workload.ManagedDesktop

**描述：** 使用 C#、Visual Basic 與 F# 來建置 WPF、Windows Forms 和主控台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面開發工具 | 15.7.27625.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 必要
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 15.0.27005.2 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | 建議
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | 選擇性
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 選擇性
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 15.8.27705.0 | 選擇性
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 選擇性
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 開發工具 | 15.8.27825.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 選擇性
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0 開發工具 | 15.8.27729.1 | 選擇性
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 選擇性
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 選擇性
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 15.8.27906.1 | 選擇性
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 容器開發工具 - 建置工具 | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 15.0.27005.2 | 選擇性
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 選擇性
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 15.0.26621.2 | 選擇性
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | 選擇性
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 選擇性
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | 選擇性
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 15.9.28219.51 | 選擇性
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 選擇性

## <a name="game-development-with-unity"></a>使用 Unity 的遊戲程式開發

**識別碼：** Microsoft.VisualStudio.Workload.ManagedGame

**描述：** 使用強大的跨平台開發環境 Unity 來建立 2D 與 3D 遊戲。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開發工具 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 15.7.27617.1 | 必要
Component.UnityEngine.x64 | Unity 2018.3 64 位元編輯器 | 15.9.28307.271 | 建議
Component.UnityEngine.x86 | Unity 5.6 32 位元編輯器 | 15.6.27406.0 | 建議

## <a name="linux-development-with-c"></a>使用 C++ 的 Linux 程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeCrossPlat

**描述：** 建立在 Linux 環境中執行的應用程式並對其進行偵錯。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.MDD.Linux | 適用於 Linux 開發的 Visual C++ | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 15.6.27406.0 | 必要
Component.Linux.CMake | 適用於 CMake 和 Linux 的 Visual C++ 工具 | 15.9.28307.102 | 建議
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 建議
Component.MDD.Linux.GCC.arm | 內嵌及 IoT 開發 | 15.6.27309.0 | 選擇性

## <a name="desktop-development-with-c"></a>使用 C++ 的傳統型開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeDesktop

**描述：** 使用 Microsoft C++ 工具組、ATL 或 MFC 建置 Windows 傳統型應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 15.0.27005.2 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 必要
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 可轉散發更新 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | 適用於 C++ 的架構工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ 核心桌面功能 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 15.0.27005.2 | 建議
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.Graphics.Win81 | 圖形工具 Windows 8.1 SDK | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 建議
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.VC.ATL | x86 與 x64 版 Visual C++ ATL | 15.7.27625.0 | 建議
Microsoft.VisualStudio.Component.VC.CMake.Project | 適用於 CMake 的 Visual C++ 工具 | 15.9.28307.102 | 建議
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 15.0.26823.1 | 建議
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Boost.Test 的測試配接器 | 15.8.27906.1 | 建議
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | 適用於 Google Test 的測試配接器 | 15.8.27906.1 | 建議
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 建議
Component.Incredibuild | IncrediBuild - 組建加速 | 15.7.27617.1 | 選擇性
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | 選擇性
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 15.6.27309.0 | 選擇性
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.VC.140 | 桌上型電腦版的 VC++ 2015.3 v14.00 (v140) 工具組 | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.VC.ATLMFC | x86 與 x64 版 Visual C++ MFC | 15.7.27625.0 | 選擇性
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 支援 | 15.6.27309.0 | 選擇性
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 標準程式庫的模組 (實驗性) | 15.6.27309.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | 適用於桌面 C++ 的 Windows 10 SDK (10.0.15063.0) [x86 及 x64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C#、VB、JS | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C++ | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | 適用於桌面 C++ 的 Windows 10 SDK (10.0.16299.0) [x86 及 x64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | 適用於桌面 C++ 的 Windows 10 SDK (10.0.16299.0) [ARM 及 ARM64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | 適用於 UWP 的 Windows 10 SDK (10.0.16299.0)：C#、VB、JS | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | 適用於 UWP 的 Windows 10 SDK (10.0.16299.0)：C++ | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.WinXP | C++ 的 Windows XP 支援 | 15.8.27924.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK 與 UCRT SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | C++ 的 Windows XP 支援 | 15.8.27705.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | 選擇性

## <a name="game-development-with-c"></a>使用 C++ 的遊戲程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeGame

**描述：** 使用 C++ 的完整功能來建置由 DirectX、Unreal 或 Cocos2d 提供技術的專業遊戲。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 可轉散發更新 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 必要
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.Graphics.Win81 | 圖形工具 Windows 8.1 SDK | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 15.0.26823.1 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 建議
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | 選擇性
Component.Android.SDK23.Private | Android SDK 安裝程式 (API 層級 23) (可供使用 JavaScript / C++ 進行行動裝置開發之用的本機安裝) | 15.9.28016.0 | 選擇性
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | 選擇性
Component.Cocos | Cocos | 15.0.26906.1 | 選擇性
Component.Incredibuild | IncrediBuild - 組建加速 | 15.7.27617.1 | 選擇性
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | 選擇性
Component.MDD.Android | C++ Android 開發工具 | 15.0.26606.0 | 選擇性
Component.OpenJDK | Microsoft 的 OpenJDK 散發 | 15.9.28125.51 | 選擇性
Component.Unreal | Unreal Engine 安裝程式 | 15.8.27729.1 | 選擇性
Component.Unreal.Android | Unreal 引擎的 Visual Studio Android 支援 | 15.9.28307.341 | 選擇性
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 15.6.27309.0 | 選擇性
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 選擇性
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 目標和建置工作 | 15.9.28016.0 | 選擇性
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 選擇性
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | 適用於桌面 C++ 的 Windows 10 SDK (10.0.15063.0) [x86 及 x64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C#、VB、JS | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C++ | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | 適用於桌面 C++ 的 Windows 10 SDK (10.0.16299.0) [x86 及 x64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | 適用於桌面 C++ 的 Windows 10 SDK (10.0.16299.0) [ARM 及 ARM64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | 適用於 UWP 的 Windows 10 SDK (10.0.16299.0)：C#、VB、JS | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | 適用於 UWP 的 Windows 10 SDK (10.0.16299.0)：C++ | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK 與 UCRT SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | 選擇性

## <a name="mobile-development-with-c"></a>使用 C++ 的行動裝置程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeMobile

**描述：** 使用 C++ 來建置適用於 iOS、Android 或 Windows 的跨平台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Android.SDK19.Private | Android SDK 安裝程式 (API 層級 19) (可供使用 JavaScript / C++ 進行行動裝置開發之用的本機安裝) | 15.9.28107.0 | 必要
Component.Android.SDK21.Private | Android SDK 安裝程式 (API 層級 21) (可供使用 JavaScript / C++ 進行行動裝置開發之用的本機安裝) | 15.9.28016.0 | 必要
Component.Android.SDK22.Private | Android SDK 安裝程式 (API 層級 22) (可供使用 JavaScript / C++ 進行行動裝置開發之用的本機安裝) | 15.9.28016.0 | 必要
Component.Android.SDK23.Private | Android SDK 安裝程式 (API 層級 23) (可供使用 JavaScript / C++ 進行行動裝置開發之用的本機安裝) | 15.9.28016.0 | 必要
Component.Android.SDK25.Private | Android SDK 安裝程式 (API 層級 25) (可供使用 JavaScript / C++ 進行行動裝置開發之用的本機安裝) | 15.9.28016.0 | 必要
Component.OpenJDK | Microsoft 的 OpenJDK 散發 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 必要
Component.Android.NDK.R15C | Android NDK (R15C) | 15.2.1 | 建議
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | 建議
Component.MDD.Android | C++ Android 開發工具 | 15.0.26606.0 | 建議
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | 選擇性
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 位元) | 12.1.11 | 選擇性
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.7 | 選擇性
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 位元) | 13.1.8 | 選擇性
Component.Android.NDK.R15C_3264 | Android NDK (R15C) (32 位元) | 15.2.1 | 選擇性
Component.Google.Android.Emulator.API23.Private | Google Android 模擬器 (API 層級 23) (本機安裝) | 15.6.27413.0 | 選擇性
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (本機安裝) | 15.9.28307.421 | 選擇性
Component.Incredibuild | IncrediBuild - 組建加速 | 15.7.27617.1 | 選擇性
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | 選擇性
Component.MDD.IOS | C++ iOS 開發工具 | 15.0.26621.2 | 選擇性

## <a name="net-core-cross-platform-development"></a>.NET Core 跨平台開發

**識別碼：** Microsoft.VisualStudio.Workload.NetCoreTools

**描述：** 使用 .NET Core、ASP.NET Core、HTML/JavaScript 及包括 Docker 支援的容器來建置跨平台的應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 15.8.27705.0 | 必要
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 必要
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.NetCore.ComponentGroup.Web.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 15.8.27906.1 | 必要
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 容器開發工具 - 建置工具 | 15.7.27617.1 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 15.9.28307.421 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
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
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 必要
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 15.9.28219.51 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 必要
Component.Microsoft.VisualStudio.Web.AzureFunctions | Microsoft Azure WebJobs 工具 | 15.7.27617.1 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 15.9.28307.421 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 15.9.28307.421 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 15.9.28125.51 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | 建議
Microsoft.VisualStudio.Component.Debugger.Snapshot | 快照集偵錯工具 | 15.8.28010.0 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | 建議
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 15.8.27825.0 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | 建議
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Microsoft Azure WebJobs 工具 | 15.7.27617.1 | 建議
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | 適用於 Web 開發的雲端工具 | 15.8.27729.1 | 建議
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.NetCore.1x.ComponentGroup.Web | 適用於網路的 .NET Core 1.0 - 1.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0 開發工具 | 15.8.27729.1 | 選擇性
Microsoft.NetCore.ComponentGroup.Web | .NET Core 2.0 開發工具 | 15.7.27625.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | 開發時間的 IIS 支援 | 15.9.28219.51 | 選擇性

## <a name="mobile-development-with-net"></a>使用 .NET 的行動應用程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NetCrossPlat

**描述：** 使用 Xamarin 來建置適用於 iOS、Android 或 Windows 的跨平台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Xamarin | Xamarin | 15.8.27906.1 | 必要
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.6.27323.2 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開發工具 | 15.6.27406.0 | 必要
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0 開發工具 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.Merq | 通用的 Xamarin 內部工具 | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.MonoDebugger | Mono 偵錯工具 | 15.0.26720.2 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET 範本引擎 | 15.8.27729.1 | 必要
Component.Android.SDK27 | Android SDK 安裝程式 (API 層級 27) | 15.9.28016.0 | 建議
Component.Google.Android.Emulator.API27 | Google Android 模擬器 (API 層級 27) | 15.9.28307.421 | 建議
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (全域安裝) | 15.9.28307.421 | 建議
Component.OpenJDK | Microsoft 的 OpenJDK 散發 | 15.9.28125.51 | 建議
Component.Xamarin.Profiler | Xamarin Profiler | 15.0.27005.2 | 建議
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | 選擇性
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 選擇性
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 15.0.27005.2 | 選擇性
Microsoft.VisualStudio.Component.Graphics | 影像與 3D 模型編輯器 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | 適用於 Xamarin 的通用 Windows 平台工具 | 15.9.28307.102 | 選擇性

## <a name="aspnet-and-web-development"></a>ASP.NET 和 Web 開發

**識別碼：** Microsoft.VisualStudio.Workload.NetWeb

**描述：** 使用 ASP.NET、ASP.NET Core、HTML/JavaScript 及包括 Docker 支援的容器來建置 Web 應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 15.8.27705.0 | 必要
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 必要
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.NetCore.ComponentGroup.Web.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 15.8.27906.1 | 必要
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 容器開發工具 - 建置工具 | 15.7.27617.1 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 15.9.28307.421 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
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
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 必要
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 15.9.28219.51 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 必要
Component.Microsoft.VisualStudio.Web.AzureFunctions | Microsoft Azure WebJobs 工具 | 15.7.27617.1 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.6.27406.0 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 建議
Microsoft.VisualStudio.Component.AspNet45 | 進階的 ASP.NET 功能 | 15.7.27625.0 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 15.9.28307.421 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 15.9.28307.421 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 15.9.28125.51 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | 建議
Microsoft.VisualStudio.Component.Debugger.Snapshot | 快照集偵錯工具 | 15.8.28010.0 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | 建議
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | 建議
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Microsoft Azure WebJobs 工具 | 15.7.27617.1 | 建議
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | 適用於 Web 開發的雲端工具 | 15.8.27729.1 | 建議
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 開發工具 | 15.8.27825.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.NetCore.1x.ComponentGroup.Web | 適用於網路的 .NET Core 1.0 - 1.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 2.0 開發工具 | 15.8.27729.1 | 選擇性
Microsoft.NetCore.ComponentGroup.Web | .NET Core 2.0 開發工具 | 15.7.27625.0 | 選擇性
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 15.0.27005.2 | 選擇性
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Web 效能與負載測試工具 | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | 開發時間的 IIS 支援 | 15.9.28219.51 | 選擇性
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | 選擇性

## <a name="nodejs-development"></a>Node.js 開發

**識別碼：** Microsoft.VisualStudio.Workload.Node

**描述：** 使用非同步的事件驅動 JavaScript 執行階段 Node.js 來建置可調整的網路應用程式。 

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.Node.Build | Node.js MSBuild 支援 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.Node.Tools | Node.js 開發支援 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.TestTools.Core | 測試工具的核心功能 | 15.7.27520.0 | 必要
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 選擇性
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 選擇性

## <a name="officesharepoint-development"></a>Office/SharePoint 程式開發

**識別碼：** Microsoft.VisualStudio.Workload.Office

**描述：** 使用 C#、VB 及 JavaScript 來建立 Office 與 SharePoint 增益集、SharePoint 解決方案，以及 VSTO 增益集。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 15.8.27705.0 | 必要
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 必要
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 15.8.27906.1 | 必要
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 容器開發工具 - 建置工具 | 15.7.27617.1 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面開發工具 | 15.7.27625.0 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 15.0.26621.2 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 必要
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | 必要
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 必要
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.8.27825.0 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 15.9.28219.51 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 15.7.27625.0 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | 建議
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 15.8.27825.0 | 選擇性
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 開發工具 | 15.8.27825.0 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 選擇性

## <a name="python-development"></a>Python 開發

**識別碼：** Microsoft.VisualStudio.Workload.Python

**描述︰** 對 Python 進行編輯、偵錯、互動式開發及原始檔控制。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.PythonTools | Python 語言支援 | 15.0.26823.1 | 必要
Component.CPython3.x64 | Python 3 64 位元 (3.6.6) | 3.6.6 | 建議
Microsoft.Component.CookiecutterTools | Cookiecutter 範本支援 | 15.0.26621.2 | 建議
Microsoft.Component.PythonTools.Web | Python Web 支援 | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 15.9.28107.0 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 建議
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 建議
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 建議
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 建議
Component.Anaconda2.x64 | Anaconda2 64 位元 (5.2.0) | 5.2.0 | 選擇性
Component.Anaconda2.x86 | Anaconda2 32 位元 (5.2.0) | 5.2.0 | 選擇性
Component.Anaconda3.x64 | Anaconda3 64 位元 (5.2.0) | 5.2.0 | 選擇性
Component.Anaconda3.x86 | Anaconda3 32 位元 (5.2.0) | 5.2.0 | 選擇性
Component.CPython2.x64 | Python 2 64 位元 (2.7.14) | 2.7.14 | 選擇性
Component.CPython2.x86 | Python 2 32 位元 (2.7.14) | 2.7.14 | 選擇性
Component.CPython3.x86 | Python 3 32 位元 (3.6.6) | 3.6.6 | 選擇性
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 15.0.26720.2 | 選擇性
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 15.8.27705.0 | 選擇性
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 選擇性
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 選擇性
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 選擇性
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | 選擇性
Microsoft.Component.PythonTools.UWP | Python IoT 支援 | 15.0.26606.0 | 選擇性
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 15.6.27309.0 | 選擇性
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python 原生開發工具 | 15.9.28307.102 | 選擇性
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 選擇性
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 選擇性
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 選擇性
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 15.9.28307.421 | 選擇性
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 15.9.28307.421 | 選擇性
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 15.9.28125.51 | 選擇性
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 15.9.28107.0 | 選擇性
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 15.8.27906.1 | 選擇性
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 容器開發工具 - 建置工具 | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 15.0.27005.2 | 選擇性
Microsoft.VisualStudio.Component.Graphics | 影像與 3D 模型編輯器 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Win81 | 圖形工具 Windows 8.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 選擇性
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 選擇性
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 選擇性
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 15.0.26621.2 | 選擇性
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | 選擇性
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.VC.140 | 桌上型電腦版的 VC++ 2015.3 v14.00 (v140) 工具組 | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 15.0.26823.1 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 選擇性
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 15.9.28219.51 | 選擇性

## <a name="universal-windows-platform-development"></a>通用 Windows 平台開發

**識別碼：** Microsoft.VisualStudio.Workload.Universal

**描述：** 使用 C#、VB、JavaScript 或選用 C++ 來建立適用於通用 Windows 平台的應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 必要
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | 必要
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 開發工具 | 15.8.27924.0 | 必要
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.Graphics | 影像與 3D 模型編輯器 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 必要
Microsoft.VisualStudio.Component.UWP.Support | 通用 Windows 平台工具 | 15.9.28119.51 | 必要
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | 適用於 Cordova 的通用 Windows 平台工具 | 15.9.28307.102 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native 和.NET Standard | 15.8.27906.1 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | 適用於 Xamarin 的通用 Windows 平台工具 | 15.9.28307.102 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.Component.VC.Runtime.OSSupport | UWP 的 Visual C++ 執行階段 | 15.6.27406.0 | 選擇性
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 15.0.27005.2 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Win81 | 圖形工具 Windows 8.1 SDK | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Windows 10 行動模擬器 (Fall Creators Update) | 15.0.27406.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | 適用於 ARM64 的 C++ 通用 Windows 平台工具 | 15.0.28125.51 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.ARM | 適用於 ARM 的 Visual C++ 編譯器與程式庫 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | 適用於 ARM64 的 Visual C++ 編譯器與程式庫 | 15.9.28230.55 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | 適用於桌面 C++ 的 Windows 10 SDK (10.0.15063.0) [x86 及 x64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C#、VB、JS | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | 適用於 UWP 的 Windows 10 SDK (10.0.15063.0)：C++ | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | 適用於桌面 C++ 的 Windows 10 SDK (10.0.16299.0) [x86 及 x64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | 適用於桌面 C++ 的 Windows 10 SDK (10.0.16299.0) [ARM 及 ARM64] | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | 適用於 UWP 的 Windows 10 SDK (10.0.16299.0)：C#、VB、JS | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | 適用於 UWP 的 Windows 10 SDK (10.0.16299.0)：C++ | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | USB 裝置連線 | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ 通用 Windows 平台工具 | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | 選擇性

## <a name="visual-studio-extension-development"></a>Visual Studio 擴充功能開發

**識別碼：** Microsoft.VisualStudio.Workload.VisualStudioExtension

**描述：** 建立適用於 Visual Studio 的附加元件與擴充功能，包括新的命令、程式碼分析器及工具視窗。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 必要
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必要
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 15.6.27406.0 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開發工具 | 15.8.27825.0 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 15.9.28016.0 | 必要
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 15.6.27309.0 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 靜態分析工具 | 15.0.26208.0 | 必要
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.8.27729.1 | 必要
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio 擴充功能開發必要條件 | 15.7.27625.0 | 必要
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.8.27729.1 | 建議
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 15.0.26208.0 | 建議
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | 選擇性
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 15.0.27729.1 | 選擇性
Microsoft.Component.VC.Runtime.OSSupport | UWP 的 Visual C++ 執行階段 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.CodeMap | Code Map | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 15.0.27005.2 | 選擇性
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 15.0.27005.2 | 選擇性
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 選擇性
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.VC.ATL | x86 與 x64 版 Visual C++ ATL | 15.7.27625.0 | 選擇性
Microsoft.VisualStudio.Component.VC.ATLMFC | x86 與 x64 版 Visual C++ MFC | 15.7.27625.0 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ 核心功能 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 15.9 版 v14.16 最新的 v141 工具 | 15.9.28230.55 | 選擇性
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 15.0.26208.0 | 選擇性

## <a name="mobile-development-with-javascript"></a>使用 JavaScript 的行動裝置程式開發

**識別碼：** Microsoft.VisualStudio.Workload.WebCrossPlat

**描述：** 使用適用於 Apache Cordova 的工具來建置 Android、iOS 及 UWP 應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Cordova 6.3.1 工具組 | 15.7.27625.0 | 必要
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | 必要
Microsoft.VisualStudio.Component.Cordova | 使用 JavaScript 核心功能的行動應用程式開發 | 15.0.26606.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem 及共用工具 | 15.0.26606.0 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 15.9.28125.51 | 必要
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.8.27729.1 | 必要
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 15.8.27825.0 | 必要
Component.Android.SDK23.Private | Android SDK 安裝程式 (API 層級 23) (可供使用 JavaScript / C++ 進行行動裝置開發之用的本機安裝) | 15.9.28016.0 | 選擇性
Component.Google.Android.Emulator.API23.Private | Google Android 模擬器 (API 層級 23) (本機安裝) | 15.6.27413.0 | 選擇性
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (本機安裝) | 15.9.28307.421 | 選擇性
Component.OpenJDK | Microsoft 的 OpenJDK 散發 | 15.9.28125.51 | 選擇性
Microsoft.Component.ClickOnce | ClickOnce 發行 | 15.8.27825.0 | 選擇性
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 15.8.27825.0 | 選擇性
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 15.8.27729.1 | 選擇性
Microsoft.VisualStudio.Component.Git | 適用於 Windows 的 Git | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.Graphics | 影像與 3D 模型編輯器 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Windows 10 行動模擬器 (Fall Creators Update) | 15.0.27406.0 | 選擇性
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 15.0.26208.0 | 選擇性
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 15.6.27406.0 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | 選擇性
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | 適用於 Cordova 的通用 Windows 平台工具 | 15.9.28307.102 | 選擇性

## <a name="unaffiliated-components"></a>非附屬元件

這些是未隨附於任何工作負載但可選取來作為個別元件的元件。

元件識別碼 | 名稱 | 版本
--- | --- | ---
Component.Android.Emulator | Visual Studio Emulator for Android | 15.6.27413.0
Component.Android.NDK.R11C | Android NDK (R11C) | 11.3.14
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 位元) | 11.3.16
Component.Android.SDK23 | Android SDK 安裝程式 (API 層級 23) (全域安裝) | 15.9.28107.0
Component.Android.SDK25 | Android SDK 安裝程式 (API 層級 25) | 15.9.28107.0
Component.GitHub.VisualStudio | Visual Studio 的 GitHub 擴充功能 | 2.5.2.2500
Component.Google.Android.Emulator.API23.V2 | Google Android 模擬器 (API 層級 23) (全域安裝) | 15.6.27413.0
Component.Google.Android.Emulator.API25 | Google Android 模擬器 (API 層級 25) | 15.7.27604.0
Microsoft.Component.Blend.SDK.WPF | 適用於 .NET 的 Blend for Visual Studio SDK | 15.6.27406.0
Microsoft.Component.HelpViewer | 說明檢視器 | 15.9.28307.421
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL 工具 | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 行動模擬器 (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Windows 10 行動模擬器 (Creators Update) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | 適用於以 Node.js v6.4.0 (x86) 為基礎之元件的執行階段 | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | 適用於以 Node.js v7.4.0 (x86) 為基礎之元件的執行階段 | 15.7.27617.1
Microsoft.VisualStudio.Component.TestTools.CodedUITest | 自動程式碼 UI 測試 | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | TypeScript 2.7 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | TypeScript 2.9 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | TypeScript 3.0 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | 適用於 ARM 的 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | 適用於 ARM 的 Visual C++ ATL 與 Spectre 風險降低 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | 適用於 ARM64 的 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | 適用於 ARM64 的 Visual C++ ATL 與 Spectre 風險降低 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) 與 Spectre 風險降低 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | 適用於 x86/x64 的 Visual C++ MFC 與 Spectre 風險降低 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (實驗性) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | 適用於 ARM 的 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | 適用於 ARM 的 Visual C++ MFC 與 Spectre 風險降低 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | 適用於 ARM64 的 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | 適用於 ARM64 的 Visual C++ MFC 支援與 Spectre 風險降低 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | 適用於 Spectre (ARM) 的 VC++ 2017 15.9 版 v14.16 程式庫 | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | 適用於 Spectre (ARM64) 的 VC++ 2017 15.9 版 v14.16 程式庫 | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | 適用於 Spectre (x86 與 x64) 的 VC++ 2017 15.9 版 v14.16 程式庫 | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | VC++ 2017 版本 15.4 v14.11 工具組 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | VC++ 2017 15.5 版 v14.12 工具組 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | VC++ 2017 15.6 版 v14.13 工具組 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | VC++ 2017 15.7 版 v14.14 工具組 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | VC++ 2017 15.8 版 v14.15 工具組 | 15.0.28230.55
