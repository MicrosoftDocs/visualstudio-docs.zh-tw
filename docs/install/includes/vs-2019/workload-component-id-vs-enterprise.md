---
title: Visual Studio Enterprise 2019 工作負載和元件識別碼
titleSuffix: ''
description: 使用工作負載和元件識別碼透過命令列安裝 Visual Studio，或是在 VSIX 資訊清單中指定為相依性
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 5844e30a9ca1f73026ed86f45dd8eb3d8842594f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437656"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Visual Studio 核心編輯器 (隨附於 Visual Studio Enterprise 2019)

**識別碼：** Microsoft.VisualStudio.Workload.CoreEditor

**描述：** Visual Studio 核心殼層體驗，包括語法感知程式碼編輯、原始程式碼控制及工作項目管理。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 核心編輯器 | 16.1.28811.260 | 必要
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | C++ 使用者的 Visual Studio 起始畫面 | 16.0.28315.86 | 選用

## <a name="azure-development"></a>Azure 開發

**識別碼：** Microsoft.VisualStudio.Workload.Azure

**描述：** Azure SDK、工具和專案，用於使用 .NET Core 和 .NET 框架開發雲應用和創建資源。 還包括用於容器化應用程式的工具，包括 Docker 支援。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.0.28714.129 | 必要
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs 工具 | 16.0.28714.129 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.0.28315.86 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 必要
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
微軟.NetCore.元件.開發工具 | .NET 核心開發工具 | 16.5.29721.120 | 必要
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 必要
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 必要
微軟.NetCore.元件.Web | .NET 核心開發工具 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.1.28810.153 | 必要
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 必要
Microsoft.VisualStudio.Component.CloudExplorer | 雲端總管 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Azure 開發必要條件 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs 工具 | 16.0.28621.142 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 必要
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 與串流分析工具 | 16.5.29721.120 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET 核心 2.1 LTS 運行時 | 16.5.29905.7 | 建議
Microsoft.VisualStudio.Component.AspNet45 | 進階的 ASP.NET 功能 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | 適用於 Kubernetes 的 Visual Studio Tools | 16.0.28625.61 | 建議
微軟.VisualStudio.元件.Azure.電源外殼 | Azure Powershell | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager 核心工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric 工具 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 16.3.29207.166 | 建議
Microsoft.VisualStudio.Component.Debugger.Snapshot | 快照集偵錯工具 | 16.5.29813.82 | 建議
Microsoft.VisualStudio.Component.Debugger.TimeTravel | 時間移動偵錯工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure 雲端服務工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager 工具 | 16.0.28528.71 | 建議
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.0.28517.75 | 選用
微軟.Net.元件.4.8.目標包 | .NET 框架 4.8 目標包 | 16.4.29313.120 | 選用
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選用
微軟.Net.元件組.4.8.開發者工具 | .NET 框架 4.8 開發工具 | 16.4.29318.151 | 選用
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure 儲存體 AzCopy | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 選用

## <a name="data-storage-and-processing"></a>資料儲存體和流程

**識別碼：** Microsoft.VisualStudio.Workload.Data

**描述：** 使用 SQL Server、Azure Data Lake 或 Hadoop 來連線、開發及測試資料解決方案。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.0.28714.129 | 建議
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.0.28315.86 | 建議
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 與串流分析工具 | 16.5.29721.120 | 建議
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 建議
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 建議
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.1.28810.153 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 16.3.29207.166 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | 雲端總管 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 建議
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 建議
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 建議
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 建議
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 建議
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.4.29318.151 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 16.0.28315.86 | 選用

## <a name="data-science-and-analytical-applications"></a>資料科學和分析應用程式

**識別碼：** Microsoft.VisualStudio.Workload.DataScience

**描述：** 用於創建資料科學應用程式的語言和工具，包括 Python 和 F#。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.PythonTools | Python 語言支援 | 16.5.29515.121 | 建議
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | 建議
Microsoft.Component.PythonTools.Web | Python Web 支援 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 建議
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 建議
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python 原生開發工具 | 16.2.29020.229 | 選用
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.25） | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 選用

## <a name="net-desktop-development"></a>.NET 桌面開發

**識別碼：** Microsoft.VisualStudio.Workload.ManagedDesktop

**描述：** 使用 C#、可視基本版和 F# 使用 .NET 核心和 .NET 框架構建 WPF、Windows 表單和主控台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 必要
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 必要
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面開發工具 | 16.5.29514.35 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | 建議
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET 核心 2.1 LTS 運行時 | 16.5.29905.7 | 建議
微軟.NetCore.元件.開發工具 | .NET 核心開發工具 | 16.5.29721.120 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | 選用
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.0.28714.129 | 選用
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.0.28315.86 | 選用
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.0.28517.75 | 選用
微軟.Net.元件.4.8.目標包 | .NET 框架 4.8 目標包 | 16.4.29313.120 | 選用
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選用
微軟.Net.元件組.4.8.開發者工具 | .NET 框架 4.8 開發工具 | 16.4.29318.151 | 選用
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 16.0.28528.71 | 選用
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 16.0.28315.86 | 選用
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 選用
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 選用
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 選用
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 選用
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 選用
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 選用
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 16.5.29514.35 | 選用
微軟.VisualStudio.元件組.MSIX.包裝 | MSIX 包裝工具 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.4.29318.151 | 選用
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 選用

## <a name="game-development-with-unity"></a>使用 Unity 的遊戲程式開發

**識別碼：** Microsoft.VisualStudio.Workload.ManagedGame

**描述：** 使用強大的跨平台開發環境 Unity 來建立 2D 與 3D 遊戲。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開發工具 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 16.0.28315.86 | 必要
Component.UnityEngine.x64 | Unity 2019.2 64 位編輯器 | 16.5.29515.121 | 建議
Component.UnityEngine.x86 | Unity 5.6 32 位元編輯器 | 16.1.28811.260 | 建議

## <a name="linux-development-with-c"></a>使用 C++ 的 Linux 程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeCrossPlat

**描述：** 建立在 Linux 環境中執行的應用程式並對其進行偵錯。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.MDD.Linux | 適用於 Linux 開發的 C++ | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 必要
Component.Linux.CMake | 適用於 Linux 的 C++ CMake 工具 | 16.2.29003.222 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 建議
Component.MDD.Linux.GCC.arm | 內嵌與 IoT 開發工具 | 16.5.29515.121 | 選用

## <a name="desktop-development-with-c"></a>使用 C++ 的桌面開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeDesktop

**描述：** 使用您選擇的工具（包括 MSVC、Clang、CMake 或 MSBuild）為 Windows 構建現代C++應用。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 16.0.28528.71 | 必要
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 可轉散發更新 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | 適用於 C++ 的架構工具 | 16.0.28621.142 | 必要
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++ 核心桌面功能 | 16.2.29012.281 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
微軟.VisualStudio.元件.VC.ASAN | C++位址消毒器（實驗） | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.VC.ATL | C++ ATL，用於最新的 v142 構建工具 （x86 & x64） | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.VC.CMake.Project | 適用於 Windows 的 C++ CMake 工具 | 16.3.29103.31 | 建議
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Boost.Test 的測試配接器 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | 適用於 Google Test 的測試配接器 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.25） | 16.5.29721.120 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 建議
微軟.VisualStudio.元件組.WebTools 擴展.CMake | JSON 編輯器 | 16.3.29207.166 | 建議
Component.Incredibuild | IncrediBuild - 組建加速 | 16.5.29721.120 | 選用
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | 選用
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 16.0.28625.61 | 選用
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 選用
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 選用
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ 建置工具 (v14.00) | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.ATLMFC | C++用於最新 v142 構建工具的 MFC（x86 & x64） | 16.4.29313.120 | 選用
Microsoft.VisualStudio.Component.VC.CLI.Support | v142 構建工具的C++/CLI 支援 （14.25） | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.VC.Llvm.Clang | C++ Windows Clang 編譯器 （9.0.0） | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | 適用於 v142 建置工具的 C++ Clang-cl (x64/86) | 16.3.29207.166 | 選用
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 適用於 v142 建置工具的 C++ 模組 (x64/x86 – 實驗性) | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 建置工具 (v14.16) | 16.1.28829.92 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | 選用
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | C++適用于 Windows 的 Clang 工具 （9.0.0 - x64/x86） | 16.5.29514.35 | 選用

## <a name="game-development-with-c"></a>使用 C++ 的遊戲程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeGame

**描述：** 使用 C++ 的完整功能來建置由 DirectX、Unreal 或 Cocos2d 提供技術的專業遊戲。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 可轉散發更新 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.25） | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
微軟.VisualStudio.元件.VC.ASAN | C++位址消毒器（實驗） | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 建議
Component.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | 選用
Component.Android.SDK25.Private | Android SDK 安裝程式 (API 層級 25) (可用於以 C++ 進行行動裝置開發的本機安裝) | 16.0.28625.61 | 選用
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | 選用
Component.Cocos | Cocos | 16.0.28315.86 | 選用
Component.Incredibuild | IncrediBuild - 組建加速 | 16.5.29721.120 | 選用
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | 選用
Component.MDD.Android | C++ Android 開發工具 | 16.0.28517.75 | 選用
Component.OpenJDK | OpenJDK (Microsoft 散發) | 16.1.28811.260 | 選用
Component.Unreal | Unreal Engine 安裝程式 | 16.1.28810.153 | 選用
Component.Unreal.Android | Unreal 引擎的 Android IDE 支援 | 16.1.28810.153 | 選用
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 選用
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 選用
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 選用
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 目標和建置工作 | 16.1.28829.92 | 選用
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 選用
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | 選用

## <a name="mobile-development-with-c"></a>使用 C++ 進行行動裝置開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeMobile

**描述：** 使用 C++ 來建置適用於 iOS、Android 或 Windows 的跨平台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK 安裝程式 (API 層級 25) (可用於以 C++ 進行行動裝置開發的本機安裝) | 16.0.28625.61 | 必要
Component.OpenJDK | OpenJDK (Microsoft 散發) | 16.1.28811.260 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 必要
Component.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | 建議
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | 建議
Component.MDD.Android | C++ Android 開發工具 | 16.0.28517.75 | 建議
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32 位元) | 16.5.29916.74 | 選用
Component.Google.Android.Emulator.API25.Private | Google Android 模擬器 (API 層級 25) (本機安裝) | 16.1.28810.153 | 選用
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (本機安裝) | 16.0.28528.71 | 選用
Component.Incredibuild | IncrediBuild - 組建加速 | 16.5.29721.120 | 選用
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | 選用
Component.MDD.IOS | C++ iOS 開發工具 | 16.0.28517.75 | 選用

## <a name="net-core-cross-platform-development"></a>.NET Core 跨平台開發

**識別碼：** Microsoft.VisualStudio.Workload.NetCoreTools

**描述：** 使用 .NET Core、ASP.NET Core、HTML/JavaScript 及包括 Docker 支援的容器來建置跨平台的應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.0.28714.129 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.0.28315.86 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 必要
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
微軟.NetCore.元件.開發工具 | .NET 核心開發工具 | 16.5.29721.120 | 必要
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 必要
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 必要
微軟.NetCore.元件.Web | .NET 核心開發工具 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | 建議
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs 工具 | 16.0.28714.129 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET 核心 2.1 LTS 運行時 | 16.5.29905.7 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.1.28810.153 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | 雲端總管 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Debugger.Snapshot | 快照集偵錯工具 | 16.5.29813.82 | 建議
Microsoft.VisualStudio.Component.Debugger.TimeTravel | 時間移動偵錯工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | 建議
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs 工具 | 16.0.28621.142 | 建議
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | 適用於 Web 開發的雲端工具 | 16.2.29003.222 | 建議
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 選用
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | 開發時間的 IIS 支援 | 16.0.28315.86 | 選用
微軟.VisualStudio.元件組.MSIX.包裝 | MSIX 包裝工具 | 16.4.29409.204 | 選用

## <a name="mobile-development-with-net"></a>使用 .NET 的行動應用程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NetCrossPlat

**描述：** 使用 Xamarin 來建置適用於 iOS、Android 或 Windows 的跨平台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (Microsoft 散發) | 16.1.28811.260 | 必要
Component.Xamarin | Xamarin | 16.5.29721.120 | 必要
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 必要
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
微軟.NetCore.元件.開發工具 | .NET 核心開發工具 | 16.5.29721.120 | 必要
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 必要
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.Merq | 通用的 Xamarin 內部工具 | 16.2.29012.281 | 必要
Microsoft.VisualStudio.Component.MonoDebugger | Mono 偵錯工具 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET 範本引擎 | 16.0.28315.86 | 必要
Component.Android.SDK28 | Android SDK 安裝程式 (API 層級 28) | 16.2.29003.222 | 建議

## <a name="aspnet-and-web-development"></a>ASP.NET 和 Web 開發

**識別碼：** Microsoft.VisualStudio.Workload.NetWeb

**描述：** 使用ASP.NET核心、ASP.NET、HTML/JavaScript 和容器（包括 Docker 支援）構建 Web 應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.0.28714.129 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.0.28315.86 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 必要
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
微軟.NetCore.元件.開發工具 | .NET 核心開發工具 | 16.5.29721.120 | 必要
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 必要
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 必要
微軟.NetCore.元件.Web | .NET 核心開發工具 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | 建議
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs 工具 | 16.0.28714.129 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET 核心 2.1 LTS 運行時 | 16.5.29905.7 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.AspNet45 | 進階的 ASP.NET 功能 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.1.28810.153 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | 雲端總管 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Debugger.Snapshot | 快照集偵錯工具 | 16.5.29813.82 | 建議
Microsoft.VisualStudio.Component.Debugger.TimeTravel | 時間移動偵錯工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs 工具 | 16.0.28621.142 | 建議
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | 適用於 Web 開發的雲端工具 | 16.2.29003.222 | 建議
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.0.28517.75 | 選用
微軟.Net.元件.4.8.目標包 | .NET 框架 4.8 目標包 | 16.4.29313.120 | 選用
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選用
微軟.Net.元件組.4.8.開發者工具 | .NET 框架 4.8 開發工具 | 16.4.29318.151 | 選用
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 16.0.28528.71 | 選用
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Web 效能與負載測試工具 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 選用
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | 其他專案範本 (舊版) | 16.0.28621.142 | 選用
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 16.5.29514.35 | 選用
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | 開發時間的 IIS 支援 | 16.0.28315.86 | 選用

## <a name="nodejs-development"></a>Node.js 開發

**識別碼：** Microsoft.VisualStudio.Workload.Node

**描述：** 使用非同步的事件驅動 JavaScript 執行階段 Node.js 來建置可調整的網路應用程式。 

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.Node.Tools | Node.js 開發工具 | 16.5.29515.121 | 必要
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.25） | 16.5.29721.120 | 選用

## <a name="officesharepoint-development"></a>Office/SharePoint 程式開發

**識別碼：** Microsoft.VisualStudio.Workload.Office

**描述：** 使用 C#、VB 及 JavaScript 來建立 Office 與 SharePoint 增益集、SharePoint 解決方案，以及 VSTO 增益集。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.0.28714.129 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.0.28315.86 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 必要
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 必要
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 必要
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面開發工具 | 16.5.29514.35 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 必要
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 必要
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.0.28517.75 | 選用
微軟.Net.元件.4.8.目標包 | .NET 框架 4.8 目標包 | 16.4.29313.120 | 選用
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選用
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選用
微軟.Net.元件組.4.8.開發者工具 | .NET 框架 4.8 開發工具 | 16.4.29318.151 | 選用
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 選用
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | 選用

## <a name="python-development"></a>Python 開發

**識別碼：** Microsoft.VisualStudio.Workload.Python

**描述︰** 對 Python 進行編輯、偵錯、互動式開發及原始檔控制。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.PythonTools | Python 語言支援 | 16.5.29515.121 | 必要
Component.CPython3.x64 | Python 3 64 位 （3.7.5） | 3.7.5 | 建議
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | 建議
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | 建議
Microsoft.Component.PythonTools.Web | Python Web 支援 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.5.29721.120 | 建議
微軟.VisualStudio.元件.TypeScript.3.8 | 類型腳本 3.8 SDK | 16.0.29813.82 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.0.28621.142 | 建議
Component.CPython2.x64 | Python 2 64 位元 (2.7.16) | 2.7.16 | 選用
Component.CPython2.x86 | Python 2 32 位元 (2.7.16) | 2.7.16 | 選用
Component.CPython3.x86 | Python 32 位 （3.7.5） | 3.7.5 | 選用
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.0.28714.129 | 選用
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.0.28315.86 | 選用
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 選用
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python 原生開發工具 | 16.2.29020.229 | 選用
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 選用
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 選用
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 選用
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 選用
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 選用
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 選用
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 選用
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.1.28810.153 | 選用
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 選用
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 16.3.29207.166 | 選用
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 選用
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 選用
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 選用
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 選用
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 選用
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 選用
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 選用
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 選用
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.25） | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 選用
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.4.29318.151 | 選用

## <a name="universal-windows-platform-development"></a>通用 Windows 平台開發

**識別碼：** Microsoft.VisualStudio.Workload.Universal

**描述：** 使用 C#、VB 或可選C++為通用 Windows 平臺創建應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.5.29515.121 | 必要
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
微軟.NetCore.元件.運行時.3.1 | .NET 核心 3.1 LTS 運行時 | 16.5.29905.7 | 必要
微軟.NetCore.元件.SDK | .NET Core SDK | 16.5.29905.7 | 必要
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.Graphics | 影像與 3D 模型編輯器 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 必要
微軟.VisualStudio.元件組.MSIX.包裝 | MSIX 包裝工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native 和.NET Standard | 16.3.29102.218 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.Support | 通用 Windows 平台工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | 適用於 Xamarin 的通用 Windows 平台工具 | 16.5.29514.35 | 必要
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 選用
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 選用
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 16.0.28528.71 | 選用
Microsoft.VisualStudio.Component.CodeClone | 重複程式碼 | 16.4.29409.204 | 選用
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | 即時相依性驗證 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | 適用於 v142 建置工具 (ARM64) 的 C++ 通用 Windows 平台支援 | 16.3.29207.166 | 選用
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.0.28625.61 | 選用
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 可轉散發更新 | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - VS 2019 C++ ARM 構建工具 （v14.25） | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - VS 2019 C++ ARM64 構建工具 （v14.25） | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.25） | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ ARM 建置工具 (v14.16) | 16.2.29003.222 | 選用
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64 建置工具 (v14.16) | 16.1.28829.92 | 選用
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 建置工具 (v14.16) | 16.1.28829.92 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | 選用
微軟.VisualStudio.元件.Windows10SDK.19041 | Windows 10 預覽 SDK （10.0.19041.0） | 16.5.29721.120 | 選用
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | USB 裝置連線 | 16.5.29515.121 | 選用
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | 架構與分析工具 | 16.5.29514.35 | 選用
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | 適用於 C++ 的架構工具 | 16.0.28621.142 | 選用
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++ 核心桌面功能 | 16.2.29012.281 | 選用
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ (v142) 通用 Windows 平台工具 | 16.3.29207.166 | 選用
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++ (v141) 通用 Windows 平台工具 | 16.1.28810.153 | 選用

## <a name="visual-studio-extension-development"></a>Visual Studio 擴充功能開發

**識別碼：** Microsoft.VisualStudio.Workload.VisualStudioExtension

**描述：** 建立適用於 Visual Studio 的附加元件與擴充功能，包括新的命令、程式碼分析器及工具視窗。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.0.28517.75 | 必要
微軟.Net.元件.4.8.SDK | .NET 框架 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | 必要
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio 擴充功能開發必要條件 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 建議
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 16.2.29003.222 | 選用
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 選用
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 16.0.28315.86 | 選用

## <a name="unaffiliated-components"></a>非附屬元件

這些是未隨附於任何工作負載但可選取來作為個別元件的元件。

元件識別碼 | 名稱 | 版本
--- | --- | ---
Component.GitHub.VisualStudio | Visual Studio 的 GitHub 擴充功能 | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | ClickOnce 發行 | 16.4.29409.204
Microsoft.Component.HelpViewer | 說明檢視器 | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET 核心 2.2 運行時 （EOL） | 16.5.29813.82
微軟.Net.Core.元件.SDK.3.0 | .NET 核心 3.0 運行時 （EOL） | 16.5.29905.7
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | 開發工具加上 .NET 核心 2.1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Web 開發工具加上 .NET 核心 2.1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Azure DevOps Office 整合 | 16.0.28625.61
微軟.VisualStudio.元件.調試器.VSOnline | 視覺化工作室線上環境調試器 | 16.5.29813.82
Microsoft.VisualStudio.Component.Git | 適用於 Windows 的 Git | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL 工具 | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | 自動程式碼 UI 測試 | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM 建置工具 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 已開啟 Spectre 風險降低功能的程式庫 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64 建置工具 (v14.20) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 已開啟 Spectre 風險降低功能的程式庫 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | 適用於 v142 建置工具的 C++ v14.20 ATL (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | 適用於 v142 建置工具的 C++ v14.20 ATL (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 ATL (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | 適用於 v142 建置工具的 C++ v14.20 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | 適用於 v142 建置工具的 C++/CLI 支援 (14.20) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.20.MFC | 適用於 v142 建置工具的 C++ v14.20 MFC (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | 適用於 v142 建置工具的 C++ v14.20 MFC (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 MFC (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | 適用於 v142 建置工具的 C++ v14.20 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 已開啟 Spectre 風險降低功能的程式庫 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ ARM 建置工具 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 已開啟 Spectre 風險降低功能的程式庫 (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ ARM64 建置工具 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 已開啟 Spectre 風險降低功能的程式庫 (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | 適用於 v142 建置工具的 C++ v14.21 ATL (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | 適用於 v142 建置工具的 C++ v14.21 ATL (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.21 ATL (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | 適用於 v142 建置工具的 C++ v14.21 ATL (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.21 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.21 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | 適用於 v142 建置工具的 C++/CLI 支援 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | 適用於 v142 建置工具的 C++ v14.21 MFC (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | 適用於 v142 建置工具的 C++ v14.21 MFC (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.21 MFC (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | 適用於 v142 建置工具的 C++ v14.21 MFC (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.21 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.21 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 已開啟 Spectre 風險降低功能的程式庫 (v14.21) | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.ARM | MSVC v142 - VS 2019 C++ ARM 建置工具 (v14.22) | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 已開啟 Spectre 風險降低功能的程式庫 (v14.22) | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.ARM64 | MSVC v142 - VS 2019 C++ ARM64 建置工具 (v14.22) | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.ARM64.前景 | MSVC v142 - VS 2019 C++ ARM64 已開啟 Spectre 風險降低功能的程式庫 (v14.22) | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.ATL | C++ v14.22 ATL 用於 v142 構建工具（x86 & x64） | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.ATL.ARM | C++ v14.22 ATL 用於 v142 構建工具 （ARM） | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.ATL.ARM.Spectre | C++ v14.22 ATL，用於 v142 構建工具，帶有 Spectre 緩解 （ARM） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.22.ATL.ARM64 | C++ v14.22 ATL 用於 v142 構建工具 （ARM64） | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.ATL.ARM64.前景 | C++ v14.22 ATL，用於使用 Spectre 緩解措施 （ARM64） 構建工具 | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.ATL.Spectre | C++ v14.22 ATL，用於 v142 構建工具，帶有 Spectre 緩解措施 （x86 & x64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.CLI.支援 | 適用於 v142 建置工具的 C++/CLI 支援 (14.22) | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.MFC | C++ v14.22 MFC 用於 v142 構建工具 （x86 & x64） | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.MFC.ARM | C++ v14.22 MFC，用於 v142 構建工具 （ARM） | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.MFC.ARM.Spectre | C++ v14.22 MFC，用於 v142 構建工具，帶有 Spectre 緩解 （ARM） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.MFC.ARM64 | 用於 v142 構建工具（ARM64）的C++ v14.22 MFC | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.MFC.ARM64.Spectre | C++ v14.22 MFC，用於 v142 構建工具，帶有 Spectre 緩解 （ARM64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.MFC.前景 | C++ v14.22 MFC，用於 v142 構建工具，帶有 Spectre 緩解功能（x86 & x64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.22.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.22) | 16.4.29313.120
微軟.VisualStudio.元件.VC.14.22.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 已開啟 Spectre 風險降低功能的程式庫 (v14.22) | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ARM | MSVC v142 - VS 2019 C++ ARM 構建工具 （v14.23） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 幽靈緩解 libs （v14.23） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ARM64 | MSVC v142 - VS 2019 C++ ARM64 構建工具 （v14.23） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ARM64.前景 | MSVC v142 - VS 2019 C++ ARM64 幽靈緩解 libs （v14.23） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ATL | C++ v14.23 ATL 用於 v142 構建工具 （x86 & x64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ATL.ARM | C++ v14.23 ATL，用於 v142 構建工具 （ARM） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ATL.ARM.Spectre | C++ v14.23 ATL，用於使用 Spectre 緩解 （ARM） 構建工具 | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.23.ATL.ARM64 | C++ v14.23 ATL 用於 v142 構建工具 （ARM64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ATL.ARM64.前景 | C++ v14.23 ATL，用於使用 Spectre 緩解措施 （ARM64） 構建工具 | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.ATL.Spectre | C++ v14.23 ATL，適用于具有 Spectre 緩解功能的 v142 構建工具（x86 & x64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.CLI.支援 | v142 構建工具的C++/CLI 支援 （14.23） | 16.4.29409.204
微軟.VisualStudio.元件.VC.14.23.MFC | C++ v14.23 MFC 用於 v142 構建工具 （x86 & x64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.MFC.ARM | C++ v14.23 MFC 用於 v142 構建工具 （ARM） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.MFC.ARM.Spectre | C++ v14.23 MFC，用於 v142 構建工具，帶有 Spectre 緩解 （ARM） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.MFC.ARM64 | C++ v14.23 MFC 用於 v142 構建工具 （ARM64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.MFC.ARM64.Spectre | C++ v14.23 MFC，用於使用 Spectre 緩解措施 （ARM64） 構建工具 | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.MFC.前景 | C++ v14.23 MFC，用於 v142 構建工具，帶有 Spectre 緩解功能 （x86 & x64） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.23） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.23.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 幽靈緩解 libs （v14.23） | 16.5.29515.121
微軟.VisualStudio.元件.VC.14.24.ARM | MSVC v142 - VS 2019 C++ ARM 構建工具 （v14.24） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 幽靈緩解 libs （v14.24） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ARM64 | MSVC v142 - VS 2019 C++ ARM64 構建工具 （v14.24） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ARM64.前景 | MSVC v142 - VS 2019 C++ ARM64 幽靈緩解 libs （v14.24） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ATL | C++ v14.24 ATL 用於 v142 構建工具 （x86 & x64） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ATL.ARM | C++ v14.24 ATL 用於 v142 構建工具 （ARM） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ATL.ARM.Spectre | C++ v14.24 ATL，用於 v142 構建工具，帶有 Spectre 緩解 （ARM） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ATL.ARM64 | C++ v14.24 ATL 用於 v142 構建工具 （ARM64） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ATL.ARM64.前景 | C++ v14.24 ATL，用於使用 Spectre 緩解措施 （ARM64） 構建工具 | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.ATL.Spectre | C++ v14.24 ATL，用於 v142 構建工具，帶有 Spectre 緩解功能 （x86 & x64） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.CLI.支援 | v142 構建工具的C++/CLI 支援 （14.24） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.MFC | C++ v14.24 MFC 用於 v142 構建工具 （x86 & x64） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.MFC.ARM | C++ v14.24 MFC，用於 v142 構建工具 （ARM） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.MFC.ARM.Spectre | C++ v14.24 MFC，用於使用 Spectre 緩解 （ARM） 構建工具 | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.MFC.ARM64 | C++ v14.24 MFC 用於 v142 構建工具 （ARM64） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.MFC.ARM64.Spectre | C++ v14.24 MFC，用於使用 Spectre 緩解措施 （ARM64） 構建工具 | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.MFC.前景 | C++ v14.24 MFC，用於 v142 構建工具，帶有 Spectre 緩解功能 （x86 & x64） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 構建工具 （v14.24） | 16.5.29721.120
微軟.VisualStudio.元件.VC.14.24.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 幽靈緩解 libs （v14.24） | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ ATL，用於最新的 v142 構建工具 （ARM） | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ ATL，使用 Spectre 緩解方案 （ARM） 提供最新的 v142 構建工具 | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ ATL，用於最新的 v142 構建工具 （ARM64） | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ ATL，用於使用 Spectre 緩解措施 （ARM64） 的最新 v142 構建工具 | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ ATL，使用 Spectre 緩解措施（x86 & x64） 提供最新的 v142 構建工具 | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++ MFC，用於使用 Spectre 緩解措施的最新 v142 構建工具 （x86 & x64） | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++ MFC，用於最新的 v142 構建工具 （ARM） | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ MFC，用於使用幽靈緩解 （ARM） 的最新 v142 構建工具 | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++ MFC，用於最新的 v142 構建工具 （ARM64） | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++ MFC，用於使用 Spectre 緩解措施 （ARM64） 的最新 v142 構建工具 | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 可轉散發 MSM | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 幽靈緩解 libs （v14.25） | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 幽靈緩解 libs （v14.25） | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 幽靈緩解 libs （v14.25）  | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - VS 2017 C++ ARM 已開啟 Spectre 風險降低功能的程式庫 (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - VS 2017 C++ ARM64 已開啟 Spectre 風險降低功能的程式庫 (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | 適用於 v141 建置工具的 C++ ALT (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | 適用於 v141 建置工具的 C++ ALT (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | 適用於 v141 建置工具且具有 Spectre 風險降低功能的 C++ ATL (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | 適用於 v141 建置工具的 C++ ALT (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | 適用於 v141 建置工具且具有 Spectre 風險降低功能的 C++ ATL (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | 適用於 v141 建置工具且具有 Spectre 風險降低功能的 C++ ATL (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | 適用於 v141 建置工具的 C++/CLI 支援 (14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | 適用於 v141 建置工具的 C++ MFC (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | 適用於 v141 建置工具的 C++ MFC (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | 適用於 v141 建置工具且具有 Spectre 風險降低功能的 C++ MFC (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | 適用於 v141 建置工具的 C++ MFC (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | 適用於 v141 建置工具且具有 Spectre 風險降低功能的 C++ MFC (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | 適用於 v141 建置工具且具有 Spectre 風險降低功能的 C++ MFC (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - VS 2017 C++ x64/x86 已開啟 Spectre 風險降低功能的程式庫 (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | 資料來源與服務參考 | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | 適用於 VS 2017 (v141) 工具的 C++ Windows XP 支援 [已淘汰] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
