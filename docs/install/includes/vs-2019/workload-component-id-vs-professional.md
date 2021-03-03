---
title: Visual Studio Professional 2019 工作負載和元件識別碼
titleSuffix: ''
description: 使用工作負載和元件識別碼透過命令列安裝 Visual Studio，或是在 VSIX 資訊清單中指定為相依性
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 3/2/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: c0c410865c32a42fabd0a59235e8832f104c5353
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750972"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2019"></a>Visual Studio 核心編輯器 (隨附於 Visual Studio Professional 2019)

**識別碼：** Microsoft.VisualStudio.Workload.CoreEditor

**描述：** Visual Studio 核心殼層體驗，包括語法感知程式碼編輯、原始程式碼控制及工作項目管理。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 核心編輯器 | 16.1.28811.260 | 必要
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | C++ 使用者的 Visual Studio 起始畫面 | 16.0.28315.86 | 選擇性

## <a name="azure-development"></a>Azure 開發

**識別碼：** Microsoft.VisualStudio.Workload.Azure

**描述：** 使用 .NET Core 和 .NET Framework 開發雲端應用程式及建立資源的 Azure Sdk、工具和專案。 也包含容器化應用程式的工具，包括 Docker 支援。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.9.31004.209 | 必要
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs 工具 | 16.9.31004.209 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.9.31004.209 | 必要
WebTools. BrowserLink. WebLivePreview | Web 即時預覽 | 0.4.12.14637 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
ComponentGroup。發佈 | .NET Core 的 ClickOnce 發行  | 16.9.31004.209 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 必要
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
NetCore. DevelopmentTools | .NET Core 開發工具 | 16.9.31004.209 | 必要
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 必要
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 必要
NetCore。 | .NET SDK | 16.9.31024.58 | 必要
NetCore。 | .NET Core 開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 必要
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Azure 開發必要條件 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs 工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 必要
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 與串流分析工具 | 16.9.31004.209 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 執行時間 (LTS)  | 16.9.31024.58 | 建議
Microsoft.VisualStudio.Component.AspNet45 | 進階的 ASP.NET 功能 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | 適用於 Kubernetes 的 Visual Studio Tools | 16.9.31004.209 | 建議
VisualStudio，Azure Powershell | Azure Powershell | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager 核心工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric 工具 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure 雲端服務工具 | 16.9.31019.194 | 建議
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager 工具 | 16.0.28528.71 | 建議
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net. 4.8. TargetingPack | .NET Framework 4.8 目標套件 | 16.4.29313.120 | 選擇性
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net. ComponentGroup. DeveloperTools | .NET Framework 4.8 開發工具 | 16.4.29318.151 | 選擇性
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure 儲存體 AzCopy | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 選擇性

## <a name="data-storage-and-processing"></a>資料的儲存與處理

**識別碼：** Microsoft.VisualStudio.Workload.Data

**描述：** 使用 SQL Server、Azure Data Lake 或 Hadoop 來連線、開發及測試資料解決方案。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.9.31004.209 | 建議
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.9.31004.209 | 建議
WebTools. BrowserLink. WebLivePreview | Web 即時預覽 | 0.4.12.14637 | 建議
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake 與串流分析工具 | 16.9.31004.209 | 建議
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 建議
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 建議
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 建議
NetCore。 | .NET SDK | 16.9.31024.58 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 建議
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 建議
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 建議
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 建議
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 16.0.28315.86 | 選擇性

## <a name="data-science-and-analytical-applications"></a>資料科學與分析應用程式

**識別碼：** Microsoft.VisualStudio.Workload.DataScience

**描述：** 用於建立資料科學應用程式的語言與工具，包括 Python 和 F #。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.PythonTools | Python 語言支援 | 16.5.29515.121 | 建議
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | 建議
Microsoft.Component.PythonTools.Web | Python Web 支援 | 16.9.31004.209 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 建議
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 建議
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python 原生開發工具 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (最新)  | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 16.4.29409.204 | 選擇性
VisualStudio. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0)  | 16.9.31004.209 | 選擇性

## <a name="net-desktop-development"></a>.NET 桌面開發

**識別碼：** Microsoft.VisualStudio.Workload.ManagedDesktop

**描述：** 使用 c #、Visual Basic 和 F # 搭配 .NET Core 和 .NET Framework 建立 WPF、Windows Forms 和主控台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 必要
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 必要
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 必要
NetCore。 | .NET SDK | 16.9.31024.58 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | 建議
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | 建議
ComponentGroup。發佈 | .NET Core 的 ClickOnce 發行  | 16.9.31004.209 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 執行時間 (LTS)  | 16.9.31024.58 | 建議
NetCore. DevelopmentTools | .NET Core 開發工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.9.31004.209 | 建議
VisualStudio. DotNetModelBuilder | ML.NET Model Builder (Preview)  | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 建議
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | 選擇性
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.9.31004.209 | 選擇性
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.9.31004.209 | 選擇性
WebTools. BrowserLink. WebLivePreview | Web 即時預覽 | 0.4.12.14637 | 選擇性
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net. 4.8. TargetingPack | .NET Framework 4.8 目標套件 | 16.4.29313.120 | 選擇性
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net. ComponentGroup. DeveloperTools | .NET Framework 4.8 開發工具 | 16.4.29318.151 | 選擇性
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 選擇性
Microsoft.VisualStudio.Component.FSharp.Desktop | F# 桌面語言支援 | 16.0.28315.86 | 選擇性
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 選擇性
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 選擇性
Microsoft.VisualStudio.Component.PortableLibrary | .NET 可攜式程式庫目標套件 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 選擇性
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 選擇性
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.ComponentGroup.MSIX. 封裝 | MSIX 封裝工具 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.9.31004.209 | 選擇性

## <a name="game-development-with-unity"></a>使用 Unity 的遊戲程式開發

**識別碼：** Microsoft.VisualStudio.Workload.ManagedGame

**描述：** 使用強大的跨平台開發環境 Unity 來建立 2D 與 3D 遊戲。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開發工具 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 16.0.28315.86 | 必要
Component.UnityEngine.x64 | Unity 中樞 | 16.9.31004.209 | 建議
Component.UnityEngine.x86 | Unity 5.6 32 位元編輯器 | 16.1.28811.260 | 建議

## <a name="linux-development-with-c"></a>使用 C++ 的 Linux 程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeCrossPlat

**描述：** 建立在 Linux 環境中執行的應用程式並對其進行偵錯。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.MDD.Linux | 適用於 Linux 開發的 C++ | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 必要
Component.Linux.CMake | 適用於 Linux 的 C++ CMake 工具 | 16.2.29003.222 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 建議
Component.MDD.Linux.GCC.arm | 內嵌與 IoT 開發工具 | 16.5.29515.121 | 選擇性

## <a name="desktop-development-with-c"></a>使用 C++ 的傳統型開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeDesktop

**描述：** 使用您選擇的工具建立適用于 Windows 的新式 c + + 應用程式，包括 MSVC、Clang、CMake 或 MSBuild。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 可轉散發更新 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++ 核心桌面功能 | 16.2.29012.281 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 建議
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 建議
VisualStudio. ASAN。 | C + + AddressSanitizer | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.VC.ATL | 適用于最新適用于 v142 build tools (x86 & x64) 的 c + + ATL | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.VC.CMake.Project | 適用於 Windows 的 C++ CMake 工具 | 16.3.29103.31 | 建議
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Boost.Test 的測試配接器 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | 適用於 Google Test 的測試配接器 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (最新)  | 16.9.31004.209 | 建議
VisualStudio. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0)  | 16.9.31004.209 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 建議
VisualStudio. ComponentGroup. WebToolsExtensions. CMake | JSON 編輯器 | 16.9.31004.209 | 建議
Component.Incredibuild | IncrediBuild - 組建加速 | 16.5.29721.120 | 選擇性
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | 選擇性
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 通用 CRT SDK | 16.0.28625.61 | 選擇性
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 選擇性
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 選擇性
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ 建置工具 (v14.00) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.ATLMFC | 適用于最新適用于 v142 build tools (x86 & x64) 的 c + + MFC | 16.4.29313.120 | 選擇性
Microsoft.VisualStudio.Component.VC.CLI.Support | 適用于適用于 v142 build tools (最新) 的 c + +/CLI 支援 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.Llvm.Clang | 適用于 Windows 的 c + + Clang 編譯器 (11.0.0)  | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | 適用於 v142 建置工具的 C++ Clang-cl (x64/86) | 16.3.29207.166 | 選擇性
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 適用於 v142 建置工具的 C++ 模組 (x64/x86 – 實驗性) | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 建置工具 (v14.16) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 選擇性
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | 適用于 Windows 的 c + + Clang 工具 (11.0.0 版-x64/x86)  | 16.9.31004.209 | 選擇性

## <a name="game-development-with-c"></a>使用 C++ 的遊戲程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeGame

**描述：** 使用 C++ 的完整功能來建置由 DirectX、Unreal 或 Cocos2d 提供技術的專業遊戲。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 可轉散發更新 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (最新)  | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
VisualStudio. ASAN。 | C + + AddressSanitizer | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 建議
VisualStudio. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0)  | 16.9.31004.209 | 建議
Component.Android.NDK.R16B | Android NDK (R16B) | 16.9.31023.347 | 選擇性
Component.Android.SDK25.Private | Android SDK 安裝程式 (API 層級 25) (可用於以 C++ 進行行動裝置開發的本機安裝) | 16.0.28625.61 | 選擇性
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | 選擇性
Component.Cocos | Cocos | 16.0.28315.86 | 選擇性
Component.Incredibuild | IncrediBuild - 組建加速 | 16.5.29721.120 | 選擇性
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | 選擇性
Component.MDD.Android | C++ Android 開發工具 | 16.0.28517.75 | 選擇性
Component.OpenJDK | OpenJDK (Microsoft 散發) | 16.1.28811.260 | 選擇性
Component.Unreal | Unreal Engine 安裝程式 | 16.1.28810.153 | 選擇性
Component.Unreal.Android | Unreal 引擎的 Android IDE 支援 | 16.1.28810.153 | 選擇性
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 選擇性
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 選擇性
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 選擇性
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 目標和建置工作 | 16.1.28829.92 | 選擇性
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 選擇性
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 選擇性

## <a name="mobile-development-with-c"></a>使用 C++ 的行動裝置程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NativeMobile

**描述：** 使用 C++ 來建置適用於 iOS、Android 或 Windows 的跨平台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK 安裝程式 (API 層級 25) (可用於以 C++ 進行行動裝置開發的本機安裝) | 16.0.28625.61 | 必要
Component.OpenJDK | OpenJDK (Microsoft 散發) | 16.1.28811.260 | 必要
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 必要
Component.Android.NDK.R16B | Android NDK (R16B) | 16.9.31023.347 | 建議
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | 建議
Component.MDD.Android | C++ Android 開發工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32 位元) | 16.9.31023.347 | 選擇性
Component.Google.Android.Emulator.API25.Private | Google Android 模擬器 (API 層級 25) (本機安裝) | 16.1.28810.153 | 選擇性
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (本機安裝) | 16.0.28528.71 | 選擇性
Component.Incredibuild | IncrediBuild - 組建加速 | 16.5.29721.120 | 選擇性
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | 選擇性
Component.MDD.IOS | C++ iOS 開發工具 | 16.0.28517.75 | 選擇性

## <a name="net-core-cross-platform-development"></a>.NET Core 跨平台開發

**識別碼：** Microsoft.VisualStudio.Workload.NetCoreTools

**描述：** 使用 .NET Core、ASP.NET Core、HTML/JavaScript 及包括 Docker 支援的容器來建置跨平台的應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.9.31004.209 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.9.31004.209 | 必要
WebTools. BrowserLink. WebLivePreview | Web 即時預覽 | 0.4.12.14637 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
ComponentGroup。發佈 | .NET Core 的 ClickOnce 發行  | 16.9.31004.209 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 必要
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
NetCore. DevelopmentTools | .NET Core 開發工具 | 16.9.31004.209 | 必要
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 必要
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 必要
NetCore。 | .NET SDK | 16.9.31024.58 | 必要
NetCore。 | .NET Core 開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | 建議
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs 工具 | 16.9.31004.209 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 執行時間 (LTS)  | 16.9.31024.58 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.9.31004.209 | 建議
VisualStudio. DotNetModelBuilder | ML.NET Model Builder (Preview)  | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
VisualStudio. WslDebugging | 使用 WSL 2 的 .NET Core 偵錯 | 16.9.31019.194 | 建議
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs 工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | 適用於 Web 開發的雲端工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | 開發時間的 IIS 支援 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.ComponentGroup.MSIX. 封裝 | MSIX 封裝工具 | 16.9.31004.209 | 選擇性

## <a name="mobile-development-with-net"></a>使用 .NET 的行動應用程式開發

**識別碼：** Microsoft.VisualStudio.Workload.NetCrossPlat

**描述：** 使用 Xamarin 來建置適用於 iOS、Android 或 Windows 的跨平台應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (Microsoft 散發) | 16.1.28811.260 | 必要
Component.Xamarin | Xamarin | 16.9.31004.209 | 必要
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.9.31004.209 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
ComponentGroup。發佈 | .NET Core 的 ClickOnce 發行  | 16.9.31004.209 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 必要
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
NetCore. DevelopmentTools | .NET Core 開發工具 | 16.9.31004.209 | 必要
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 必要
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 必要
NetCore。 | .NET SDK | 16.9.31024.58 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.Merq | 通用的 Xamarin 內部工具 | 16.2.29012.281 | 必要
Microsoft.VisualStudio.Component.MonoDebugger | Mono 偵錯工具 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET 範本引擎 | 16.9.31004.209 | 必要
SDK30 |  (API 層級 30) 的 Android SDK 安裝程式 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議

## <a name="aspnet-and-web-development"></a>ASP.NET 和 Web 開發

**識別碼：** Microsoft.VisualStudio.Workload.NetWeb

**描述：** 使用 ASP.NET Core、ASP.NET、HTML/JavaScript 及容器（包括 Docker 支援）來建立 web 應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.9.31004.209 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.9.31004.209 | 必要
WebTools. BrowserLink. WebLivePreview | Web 即時預覽 | 0.4.12.14637 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
ComponentGroup。發佈 | .NET Core 的 ClickOnce 發行  | 16.9.31004.209 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 必要
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
NetCore. DevelopmentTools | .NET Core 開發工具 | 16.9.31004.209 | 必要
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 必要
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 必要
NetCore。 | .NET SDK | 16.9.31024.58 | 必要
NetCore。 | .NET Core 開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.FSharp | F# 語言支援 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web 專案的 F# 語言支援 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.9.31004.209 | 必要
VisualStudio. ComponentGroup. 用戶端 | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | 建議
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs 工具 | 16.9.31004.209 | 建議
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 建議
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開發工具 | 16.0.28516.191 | 建議
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 執行時間 (LTS)  | 16.9.31024.58 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 建議
Microsoft.VisualStudio.Component.AspNet45 | 進階的 ASP.NET 功能 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 建議
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 工具 | 16.0.28315.86 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
VisualStudio. WslDebugging | 使用 WSL 2 的 .NET Core 偵錯 | 16.9.31019.194 | 建議
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs 工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | 適用於 Web 開發的雲端工具 | 16.9.31004.209 | 建議
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net. 4.8. TargetingPack | .NET Framework 4.8 目標套件 | 16.4.29313.120 | 選擇性
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net. ComponentGroup. DeveloperTools | .NET Framework 4.8 開發工具 | 16.4.29318.151 | 選擇性
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | 其他專案範本 (舊版) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | 開發時間的 IIS 支援 | 16.9.31004.209 | 選擇性

## <a name="nodejs-development"></a>Node.js 開發

**識別碼：** Microsoft.VisualStudio.Workload.Node

**描述：** 使用非同步的事件驅動 JavaScript 執行階段 Node.js 來建置可調整的網路應用程式。 

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Node.Tools | Node.js 開發工具 | 16.5.29515.121 | 必要
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 必要
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 選擇性
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (最新)  | 16.9.31004.209 | 選擇性

## <a name="officesharepoint-development"></a>Office/SharePoint 程式開發

**識別碼：** Microsoft.VisualStudio.Workload.Office

**描述：** 使用 C#、VB 及 JavaScript 來建立 Office 與 SharePoint 增益集、SharePoint 解決方案，以及 VSTO 增益集。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.9.31004.209 | 必要
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.9.31004.209 | 必要
WebTools. BrowserLink. WebLivePreview | Web 即時預覽 | 0.4.12.14637 | 必要
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 必要
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 必要
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 必要
NetCore。 | .NET SDK | 16.9.31024.58 | 必要
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 必要
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET 桌面開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.4.29409.204 | 必要
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 必要
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 必要
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 必要
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | 必要
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | 必要
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 目標套件 | 16.9.31004.209 | 選擇性
Microsoft.Net. 4.8. TargetingPack | .NET Framework 4.8 目標套件 | 16.4.29313.120 | 選擇性
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開發工具 | 16.3.29207.166 | 選擇性
Microsoft.Net. ComponentGroup. DeveloperTools | .NET Framework 4.8 開發工具 | 16.4.29318.151 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | 選擇性

## <a name="python-development"></a>Python 開發

**識別碼：** Microsoft.VisualStudio.Workload.Python

**描述︰** 對 Python 進行編輯、偵錯、互動式開發及原始檔控制。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.PythonTools | Python 語言支援 | 16.5.29515.121 | 必要
Component.CPython3.x64 | Python 3 64 位 (3.7.8)  | 3.7.8 | 建議
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.3587 | 建議
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | 建議
Microsoft.Component.PythonTools.Web | Python Web 支援 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Common.Azure.Tools | 連接與發行工具 | 16.4.29409.204 | 建議
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-in-Time 偵錯工具 | 16.0.28517.75 | 建議
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript 與 TypeScript 語言支援 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 建議
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 建議
VisualStudio，元件的 TypeScript | TypeScript 4.1 SDK | 16.0.31004.209 | 建議
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | 建議
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET 和 Web 開發 | 16.9.31004.209 | 建議
Component.CPython2.x64 | Python 2 64 位 (2.7.18)  | 2.7.18.1 | 選擇性
Component.CPython2.x86 | Python 2 32 位 (2.7.18)  | 2.7.18.1 | 選擇性
Component.CPython3.x86 | Python 3 32 位 (3.7.8)  | 3.7.8 | 選擇性
Component.Microsoft.VisualStudio.RazorExtension | Razor 語言服務 | 16.9.31004.209 | 選擇性
Component.Microsoft.Web.LibraryManager | 程式庫管理員 | 16.9.31004.209 | 選擇性
WebTools. BrowserLink. WebLivePreview | Web 即時預覽 | 0.4.12.14637 | 選擇性
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 選擇性
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python 原生開發工具 | 16.9.31004.209 | 選擇性
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 選擇性
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 選擇性
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 選擇性
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 選擇性
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 選擇性
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 選擇性
NetCore。 | .NET SDK | 16.9.31024.58 | 選擇性
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 製作工具 | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure Libraries for .NET | 16.0.28315.86 | 選擇性
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure 計算模擬器 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure 儲存體模擬器 | 16.4.29313.120 | 選擇性
Microsoft.VisualStudio.Component.Azure.Waverton | Azure 雲端服務核心工具 | 16.9.31019.194 | 選擇性
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure 雲端服務建置工具 | 16.9.31019.194 | 選擇性
Microsoft.VisualStudio.Component.DockerTools | 容器開發工具 | 16.4.29409.204 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | 選擇性
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診斷 | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed 桌面工作負載核心 | 16.4.29318.151 | 選擇性
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC 驅動程式 | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | 選擇性
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 選擇性
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 執行階段 | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 選擇性
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 支援的資料來源 | 16.0.28315.86 | 選擇性
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | 選擇性
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ 分析工具 | 16.5.29515.121 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (最新)  | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Web | ASP.NET 與網頁程式開發工具 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK | Windows 通用 C 執行階段 | 16.4.29409.204 | 選擇性
VisualStudio. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0)  | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET 和 Web 開發工具的必要條件 | 16.9.31004.209 | 選擇性

## <a name="universal-windows-platform-development"></a>通用 Windows 平台開發

**識別碼：** Microsoft.VisualStudio.Workload.Universal

**描述：** 使用 c #、VB 或選擇性的 c + + 建立適用于通用 Windows 平臺的應用程式。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.5.29515.121 | 必要
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | 必要
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 目標套件 | 16.0.28517.75 | 必要
NetCore. 3.1 版 | .NET Core 3.1 執行時間 (LTS)  | 16.9.31024.58 | 必要
NetCore. 5.0 版 | .NET 5.0 執行時間 | 16.9.31024.58 | 必要
NetCore。 | .NET SDK | 16.9.31024.58 | 必要
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 必要
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.Graphics | 影像與 3D 模型編輯器 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server 的 CLR 資料類型 | 16.0.28315.86 | 必要
VisualStudio. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0)  | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.MSIX. 封裝 | MSIX 封裝工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native 和.NET Standard | 16.3.29102.218 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.Support | 通用 Windows 平台工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | 適用於 Xamarin 的通用 Windows 平台工具 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 選擇性
Microsoft.VisualStudio.Component.Graphics.Tools | 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具 | 16.0.28625.61 | 選擇性
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | 適用於 v142 建置工具 (ARM64) 的 C++ 通用 Windows 平台支援 | 16.3.29207.166 | 選擇性
Microsoft.VisualStudio.Component.VC.CoreIde | C++ 核心功能 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC 適用于 v142-VS 2019 c + + ARM build tools (最新)  | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC 適用于 v142-VS 2019 c + + ARM64 build tools (最新)  | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (最新)  | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ ARM 建置工具 (v14.16) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64 建置工具 (v14.16) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 建置工具 (v14.16) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | 選擇性
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | USB 裝置連線 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ (v142) 通用 Windows 平台工具 | 16.9.31004.209 | 選擇性
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++ (v141) 通用 Windows 平台工具 | 16.1.28810.153 | 選擇性

## <a name="visual-studio-extension-development"></a>Visual Studio 擴充功能開發

**識別碼：** Microsoft.VisualStudio.Workload.VisualStudioExtension

**描述：** 建立適用於 Visual Studio 的附加元件與擴充功能，包括新的命令、程式碼分析器及工具視窗。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 必要
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 目標套件 | 16.0.28517.75 | 必要
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 目標套件 | 16.9.31004.209 | 必要
Net.tcp. 4.8。 | .NET Framework 4.8 SDK | 16.4.29313.120 | 必要
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 開發工具 | 16.3.29207.166 | 必要
Microsoft.VisualStudio.Component.NuGet | NuGet 套件管理員 | 16.1.28829.92 | 必要
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 與 Visual Basic Roslyn 編譯程式 | 16.0.28714.129 | 必要
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 和 Visual Basic | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | 必要
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio 擴充功能開發必要條件 | 16.9.31004.209 | 必要
Microsoft.VisualStudio.Component.DiagnosticTools | .NET 分析工具 | 16.9.31004.209 | 建議
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.9.31019.194 | 建議
Microsoft.VisualStudio.Component.TextTemplating | 文字範本轉換 | 16.0.28625.61 | 建議
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 16.2.29003.222 | 選擇性
Microsoft.VisualStudio.Component.AppInsights.Tools | 開發人員分析工具 | 16.5.29515.121 | 選擇性
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 16.0.28315.86 | 選擇性

## <a name="unaffiliated-components"></a>非附屬元件

這些是未隨附於任何工作負載但可選取來作為個別元件的元件。

元件識別碼 | 名稱 | 版本
--- | --- | ---
Component.GitHub.VisualStudio | Visual Studio 的 GitHub 擴充功能 | 2.5.9.5485
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Microsoft.Component.ClickOnce | ClickOnce 發行 | 16.4.29409.204
Microsoft.Component.HelpViewer | 說明檢視器 | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2 執行時間 (不支援)  | 16.9.31024.58
Net.tcp. SDK. 3。0 | .NET Core 3.0 執行時間 (不支援)  | 16.9.31024.58
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | 開發工具加上 .NET Core 2。1 | 16.9.31004.209
Microsoft.NetCore.ComponentGroup.Web.2.1 | Web 開發工具加上 .NET Core 2。1 | 16.9.31004.209
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Azure DevOps Office 整合 | 16.0.28625.61
Microsoft.VisualStudio.Component.ClassDesigner | 類別設計工具 | 16.0.28528.71
Microsoft.VisualStudio.Component.DependencyValidation.Community | 相依性驗證 | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | 適用於 Windows 的 Git | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | DGML 編輯器 | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL 工具 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM 建置工具 (v14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 已開啟 Spectre 風險降低功能的程式庫 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64 建置工具 (v14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 已開啟 Spectre 風險降低功能的程式庫 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | 適用於 v142 建置工具的 C++ v14.20 ATL (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | 適用於 v142 建置工具的 C++ v14.20 ATL (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 ATL (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | 適用於 v142 建置工具的 C++ v14.20 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | 適用於 v142 建置工具的 C++/CLI 支援 (14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.MFC | 適用於 v142 建置工具的 C++ v14.20 MFC (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | 適用於 v142 建置工具的 C++ v14.20 MFC (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 MFC (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | 適用於 v142 建置工具的 C++ v14.20 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | 適用於 v142 建置工具且具有 Spectre 風險降低功能的 C++ v14.20 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.20) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 已開啟 Spectre 風險降低功能的程式庫 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ ARM 建置工具 (v14.21) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 已開啟 Spectre 風險降低功能的程式庫 (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ ARM64 建置工具 (v14.21) | 16.9.31004.209
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
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.21) | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 已開啟 Spectre 風險降低功能的程式庫 (v14.21) | 16.5.29515.121
VisualStudio. 14.22. ARM | MSVC v142 - VS 2019 C++ ARM 建置工具 (v14.22) | 16.9.31004.209
VisualStudio. 14.22. Spectre。 | MSVC v142 - VS 2019 C++ ARM 已開啟 Spectre 風險降低功能的程式庫 (v14.22) | 16.5.29515.121
VisualStudio. 14.22. ARM64 | MSVC v142 - VS 2019 C++ ARM64 建置工具 (v14.22) | 16.9.31004.209
VisualStudio. 14.22. ARM64. Spectre | MSVC v142 - VS 2019 C++ ARM64 已開啟 Spectre 風險降低功能的程式庫 (v14.22) | 16.5.29515.121
VisualStudio. 14.22。 | 適用于適用于 v142 build tools (x86 & x64) 的 c + + v 14.22 ATL | 16.4.29313.120
VisualStudio. 14.22. ARM。 | 適用于適用于 v142 build tools (ARM) 的 c + + v 14.22 ATL | 16.4.29313.120
VisualStudio. 14.22. Spectre （） | 適用于適用于 v142 組建工具的 c + + v 14.22 ATL， (ARM) 的 Spectre 緩和措施 | 16.5.29721.120
VisualStudio. 14.22. ARM64。 | C + + v 14.22 ATL for 適用于 v142 build tools (ARM64)  | 16.4.29313.120
VisualStudio. 14.22. ARM64.. Spectre | C + + v 14.22 ATL for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.5.29515.121
VisualStudio. 14.22. Spectre。 | C + + v 14.22 ATL for 適用于 v142 build tools (x86 & x64)  | 16.5.29515.121
VisualStudio. 14.22. 支援服務 | 適用於 v142 建置工具的 C++/CLI 支援 (14.22) | 16.9.31004.209
VisualStudio. 14.22. MFC | C + + v 14.22 MFC for 適用于 v142 build tools (x86 & x64)  | 16.4.29313.120
VisualStudio. 14.22. a.. ARM | C + + v 14.22 MFC for 適用于 v142 build tools (ARM)  | 16.4.29313.120
VisualStudio. 14.22. Spectre （） | 適用于適用于 v142 的 c + + v 14.22 適用于 Spectre 緩和 (ARM) 的組建工具 | 16.5.29515.121
VisualStudio. 14.22. ARM64。 | C + + v 14.22 MFC for 適用于 v142 build tools (ARM64)  | 16.4.29313.120
VisualStudio. 14.22. ARM64.. Spectre | C + + v 14.22 MFC for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.5.29515.121
VisualStudio. 14.22. Spectre。 | C + + v 14.22 MFC for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.5.29515.121
VisualStudio. 14.22. x86。 | MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.22) | 16.9.31004.209
VisualStudio. 14.22. Spectre <。 | MSVC v142 - VS 2019 C++ x64/x86 已開啟 Spectre 風險降低功能的程式庫 (v14.22) | 16.5.29515.121
VisualStudio. v14.23. ARM | MSVC 適用于 v142-VS 2019 c + + ARM build tools (v v14.23)  | 16.9.31004.209
VisualStudio. v14.23. Spectre。 | MSVC 適用于 v142-VS 2019 c + + ARM Spectre-降低的程式庫 (v v14.23)  | 16.5.29515.121
VisualStudio. v14.23. ARM64 | MSVC 適用于 v142-VS 2019 c + + ARM64 build tools (v v14.23)  | 16.9.31004.209
VisualStudio. v14.23. ARM64. Spectre | MSVC 適用于 v142-VS 2019 c + + ARM64 Spectre-降低的程式庫 (v v14.23)  | 16.5.29515.121
VisualStudio. v14.23。 | 適用于適用于 v142 build tools (x86 & x64) 的 c + + v v14.23 ATL | 16.5.29515.121
VisualStudio. v14.23. ARM。 | 適用于適用于 v142 build tools (ARM) 的 c + + v v14.23 ATL | 16.5.29515.121
VisualStudio. v14.23. Spectre （） | 適用于適用于 v142 組建工具的 c + + v v14.23 ATL， (ARM) 的 Spectre 緩和措施 | 16.5.29721.120
VisualStudio. v14.23. ARM64。 | C + + v v14.23 ATL for 適用于 v142 build tools (ARM64)  | 16.5.29515.121
VisualStudio. v14.23. ARM64.. Spectre | C + + v v14.23 ATL for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.5.29515.121
VisualStudio. v14.23. Spectre。 | C + + v v14.23 ATL for 適用于 v142 build tools (x86 & x64)  | 16.5.29515.121
VisualStudio. v14.23. 支援服務 | 適用于 v142 build tools (14.23) 的 c + +/CLI 支援 | 16.9.31004.209
VisualStudio. v14.23. MFC | C + + v v14.23 MFC for 適用于 v142 build tools (x86 & x64)  | 16.5.29515.121
VisualStudio. v14.23. a.. ARM | C + + v v14.23 MFC for 適用于 v142 build tools (ARM)  | 16.5.29515.121
VisualStudio. v14.23. Spectre （） | 適用于適用于 v142 的 c + + v v14.23 適用于 Spectre 緩和 (ARM) 的組建工具 | 16.5.29515.121
VisualStudio. v14.23. ARM64。 | C + + v v14.23 MFC for 適用于 v142 build tools (ARM64)  | 16.5.29515.121
VisualStudio. v14.23. ARM64.. Spectre | C + + v v14.23 MFC for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.5.29515.121
VisualStudio. v14.23. Spectre。 | C + + v v14.23 MFC for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.5.29515.121
VisualStudio. v14.23. x86。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (v v14.23)  | 16.9.31004.209
VisualStudio. v14.23. Spectre <。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 Spectre-降低的程式庫 (v v14.23)  | 16.5.29515.121
VisualStudio. 14.24. ARM | MSVC 適用于 v142-VS 2019 c + + ARM build tools (v 14.24)  | 16.9.31004.209
VisualStudio. 14.24. Spectre。 | MSVC 適用于 v142-VS 2019 c + + ARM Spectre-降低的程式庫 (v 14.24)  | 16.5.29721.120
VisualStudio. 14.24. ARM64 | MSVC 適用于 v142-VS 2019 c + + ARM64 build tools (v 14.24)  | 16.9.31004.209
VisualStudio. 14.24. ARM64. Spectre | MSVC 適用于 v142-VS 2019 c + + ARM64 Spectre-降低的程式庫 (v 14.24)  | 16.5.29721.120
VisualStudio. 14.24。 | 適用于適用于 v142 build tools (x86 & x64) 的 c + + v 14.24 ATL | 16.5.29721.120
VisualStudio. 14.24. ARM。 | 適用于適用于 v142 build tools (ARM) 的 c + + v 14.24 ATL | 16.5.29721.120
VisualStudio. 14.24. Spectre （） | 適用于適用于 v142 組建工具的 c + + v 14.24 ATL， (ARM) 的 Spectre 緩和措施 | 16.5.29721.120
VisualStudio. 14.24. ARM64。 | C + + v 14.24 ATL for 適用于 v142 build tools (ARM64)  | 16.5.29721.120
VisualStudio. 14.24. ARM64.. Spectre | C + + v 14.24 ATL for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.5.29721.120
VisualStudio. 14.24. Spectre。 | C + + v 14.24 ATL for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.24. 支援服務 | 適用于 v142 build tools (14.24) 的 c + +/CLI 支援 | 16.9.31004.209
VisualStudio. 14.24. MFC | C + + v 14.24 MFC for 適用于 v142 build tools (x86 & x64)  | 16.5.29721.120
VisualStudio. 14.24. a.. ARM | C + + v 14.24 MFC for 適用于 v142 build tools (ARM)  | 16.5.29721.120
VisualStudio. 14.24. Spectre （） | 適用于適用于 v142 的 c + + v 14.24 適用于 Spectre 緩和 (ARM) 的組建工具 | 16.5.29721.120
VisualStudio. 14.24. ARM64。 | C + + v 14.24 MFC for 適用于 v142 build tools (ARM64)  | 16.5.29721.120
VisualStudio. 14.24. ARM64.. Spectre | C + + v 14.24 MFC for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. 14.24. Spectre。 | C + + v 14.24 MFC for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.24. x86。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (v 14.24)  | 16.9.31004.209
VisualStudio. 14.24. Spectre <。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 Spectre-降低的程式庫 (v 14.24)  | 16.5.29721.120
VisualStudio. v14.25. ARM | MSVC 適用于 v142-VS 2019 c + + ARM build tools (v v14.25)  | 16.9.31004.209
VisualStudio. v14.25. Spectre。 | MSVC 適用于 v142-VS 2019 c + + ARM Spectre-降低的程式庫 (v v14.25)  | 16.9.31004.209
VisualStudio. v14.25. ARM64 | MSVC 適用于 v142-VS 2019 c + + ARM64 build tools (v v14.25)  | 16.9.31004.209
VisualStudio. v14.25. ARM64. Spectre | MSVC 適用于 v142-VS 2019 c + + ARM64 Spectre-降低的程式庫 (v v14.25)  | 16.9.31004.209
VisualStudio. v14.25。 | 適用于適用于 v142 build tools (x86 & x64) 的 c + + v v14.25 ATL | 16.9.31004.209
VisualStudio. v14.25. ARM。 | 適用于適用于 v142 build tools (ARM) 的 c + + v v14.25 ATL | 16.9.31004.209
VisualStudio. v14.25. Spectre （） | 適用于適用于 v142 組建工具的 c + + v v14.25 ATL， (ARM) 的 Spectre 緩和措施 | 16.9.31004.209
VisualStudio. v14.25. ARM64。 | C + + v v14.25 ATL for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. v14.25. ARM64.. Spectre | C + + v v14.25 ATL for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. v14.25. Spectre。 | C + + v v14.25 ATL for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. v14.25. 支援服務 | 適用于 v142 build tools (14.25) 的 c + +/CLI 支援 | 16.9.31004.209
VisualStudio. v14.25. MFC | C + + v v14.25 MFC for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. v14.25. a.. ARM | C + + v v14.25 MFC for 適用于 v142 build tools (ARM)  | 16.9.31004.209
VisualStudio. v14.25. Spectre （） | 適用于適用于 v142 的 c + + v v14.25 適用于 Spectre 緩和 (ARM) 的組建工具 | 16.9.31004.209
VisualStudio. v14.25. ARM64。 | C + + v v14.25 MFC for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. v14.25. ARM64.. Spectre | C + + v v14.25 MFC for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. v14.25. Spectre。 | C + + v v14.25 MFC for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.9.31004.209
VisualStudio. v14.25. x86。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (v v14.25)  | 16.9.31004.209
VisualStudio. v14.25. Spectre <。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 Spectre-降低的程式庫 (v v14.25)  | 16.9.31004.209
VisualStudio. v14.26. ARM | MSVC 適用于 v142-VS 2019 c + + ARM build tools (v v14.26)  | 16.9.31004.209
VisualStudio. v14.26. Spectre。 | MSVC 適用于 v142-VS 2019 c + + ARM Spectre-降低的程式庫 (v v14.26)  | 16.9.31004.209
VisualStudio. v14.26. ARM64 | MSVC 適用于 v142-VS 2019 c + + ARM64 build tools (v v14.26)  | 16.9.31004.209
VisualStudio. v14.26. ARM64. Spectre | MSVC 適用于 v142-VS 2019 c + + ARM64 Spectre-降低的程式庫 (v v14.26)  | 16.9.31004.209
VisualStudio. v14.26。 | 適用于適用于 v142 build tools (x86 & x64) 的 c + + v v14.26 ATL | 16.9.31004.209
VisualStudio. v14.26. ARM。 | 適用于適用于 v142 build tools (ARM) 的 c + + v v14.26 ATL | 16.9.31004.209
VisualStudio. v14.26. Spectre （） | 適用于適用于 v142 組建工具的 c + + v v14.26 ATL， (ARM) 的 Spectre 緩和措施 | 16.9.31004.209
VisualStudio. v14.26. ARM64。 | C + + v v14.26 ATL for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. v14.26. ARM64.. Spectre | C + + v v14.26 ATL for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. v14.26. Spectre。 | C + + v v14.26 ATL for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. v14.26. 支援服務 | 適用于 v142 build tools (14.26) 的 c + +/CLI 支援 | 16.9.31004.209
VisualStudio. v14.26. MFC | C + + v v14.26 MFC for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. v14.26. a.. ARM | C + + v v14.26 MFC for 適用于 v142 build tools (ARM)  | 16.9.31004.209
VisualStudio. v14.26. Spectre （） | 適用于適用于 v142 的 c + + v v14.26 適用于 Spectre 緩和 (ARM) 的組建工具 | 16.9.31004.209
VisualStudio. v14.26. ARM64。 | C + + v v14.26 MFC for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. v14.26. ARM64.. Spectre | C + + v v14.26 MFC for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. v14.26. Spectre。 | C + + v v14.26 MFC for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.9.31004.209
VisualStudio. v14.26. x86。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (v v14.26)  | 16.9.31004.209
VisualStudio. v14.26. Spectre <。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 Spectre-降低的程式庫 (v v14.26)  | 16.9.31004.209
VisualStudio. 14.27. ARM | MSVC 適用于 v142-VS 2019 c + + ARM build tools (v 14.27)  | 16.9.31004.209
VisualStudio. 14.27. Spectre。 | MSVC 適用于 v142-VS 2019 c + + ARM Spectre-降低的程式庫 (v 14.27)  | 16.9.31004.209
VisualStudio. 14.27. ARM64 | MSVC 適用于 v142-VS 2019 c + + ARM64 build tools (v 14.27)  | 16.9.31004.209
VisualStudio. 14.27. ARM64. Spectre | MSVC 適用于 v142-VS 2019 c + + ARM64 Spectre-降低的程式庫 (v 14.27)  | 16.9.31004.209
VisualStudio. 14.27。 | 適用于適用于 v142 build tools (x86 & x64) 的 c + + v 14.27 ATL | 16.9.31004.209
VisualStudio. 14.27. ARM。 | 適用于適用于 v142 build tools (ARM) 的 c + + v 14.27 ATL | 16.9.31004.209
VisualStudio. 14.27. Spectre （） | 適用于適用于 v142 組建工具的 c + + v 14.27 ATL， (ARM) 的 Spectre 緩和措施 | 16.9.31004.209
VisualStudio. 14.27. ARM64。 | C + + v 14.27 ATL for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. 14.27. ARM64.. Spectre | C + + v 14.27 ATL for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. 14.27. Spectre。 | C + + v 14.27 ATL for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.27. 支援服務 | 適用于 v142 build tools (14.27) 的 c + +/CLI 支援 | 16.9.31004.209
VisualStudio. 14.27. MFC | C + + v 14.27 MFC for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.27. a.. ARM | C + + v 14.27 MFC for 適用于 v142 build tools (ARM)  | 16.9.31004.209
VisualStudio. 14.27. Spectre （） | 適用于適用于 v142 的 c + + v 14.27 適用于 Spectre 緩和 (ARM) 的組建工具 | 16.9.31004.209
VisualStudio. 14.27. ARM64。 | C + + v 14.27 MFC for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. 14.27. ARM64.. Spectre | C + + v 14.27 MFC for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. 14.27. Spectre。 | C + + v 14.27 MFC for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.27. x86。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (v 14.27)  | 16.9.31004.209
VisualStudio. 14.27. Spectre <。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 Spectre-降低的程式庫 (v 14.27)  | 16.9.31004.209
VisualStudio. 14.28. ARM | MSVC 適用于 v142-VS 2019 c + + ARM build tools (v 14.28-16.8)  | 16.9.31004.209
VisualStudio. 14.28. Spectre。 | MSVC 適用于 v142-VS 2019 c + + ARM Spectre-降低的程式庫 (v 14.28-16.8)  | 16.9.31004.209
VisualStudio. 14.28. ARM64 | MSVC 適用于 v142-VS 2019 c + + ARM64 build tools (v 14.28-16.8)  | 16.9.31004.209
VisualStudio. 14.28. ARM64. Spectre | MSVC 適用于 v142-VS 2019 c + + ARM64 Spectre-降低的程式庫 (v 14.28-16.8)  | 16.9.31004.209
VisualStudio. 14.28。 | C + + v 14.28 (16.8) ATL for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.28. ARM。 | C + + v 14.28 (16.8) ATL for 適用于 v142 build tools (ARM)  | 16.9.31004.209
VisualStudio. 14.28. Spectre （） | C + + v 14.28 (16.8) ATL for 適用于 v142 build tools 搭配 Spectre 緩和 (ARM)  | 16.9.31004.209
VisualStudio. 14.28. ARM64。 | C + + v 14.28 (16.8) ATL for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. 14.28. ARM64.. Spectre | C + + v 14.28 (16.8) ATL for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. 14.28. Spectre。 | C + + v 14.28 (16.8) ATL for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.28. 支援服務 | C + +/CLI 支援適用于 v142 build tools (14.28-16.8)  | 16.9.31004.209
VisualStudio. 14.28. MFC | C + + v 14.28 (16.8) MFC for 適用于 v142 build tools (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.28. a.. ARM | C + + v 14.28 (16.8) MFC for 適用于 v142 build tools (ARM)  | 16.9.31004.209
VisualStudio. 14.28. Spectre （） | C + + v 14.28 (16.8) MFC for 適用于 v142 build tools 搭配 Spectre 緩和 (ARM)  | 16.9.31004.209
VisualStudio. 14.28. ARM64。 | C + + v 14.28 (16.8) MFC for 適用于 v142 build tools (ARM64)  | 16.9.31004.209
VisualStudio. 14.28. ARM64.. Spectre | C + + v 14.28 (16.8) MFC for 適用于 v142 build tools with Spectre 緩和措施 (ARM64)  | 16.9.31004.209
VisualStudio. 14.28. Spectre。 | C + + v 14.28 (16.8) MFC for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.9.31004.209
VisualStudio. 14.28. x86。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 build tools (v 14.28-16.8)  | 16.9.31004.209
VisualStudio. 14.28. Spectre <。 | MSVC 適用于 v142-VS 2019 c + + x64/x86 Spectre-降低的程式庫 (v 14.28-16.8)  | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.ATL.ARM | 適用于最新適用于 v142 build tools (ARM) 的 c + + ATL | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | 適用于最新適用于 v142 build 工具的 c + + ATL (ARM) 的緩和措施 | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | 適用于最新適用于 v142 build tools (ARM64) 的 c + + ATL | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C + + ATL for 最新的適用于 v142 build tools with Spectre 緩和 (ARM64)  | 16.5.29515.121
VisualStudio。 ARM64EC 的部分 | 適用于最新適用于 v142 build tools (ARM64EC 的 c + + ATL-實驗性)  | 16.9.31004.209
VisualStudio. ARM64EC. Spectre。 | C + + ATL for 最新的適用于 v142 build tools with Spectre 緩和措施 (ARM64EC-實驗性)  | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C + + ATL for 適用于 v142 build tools with Spectre 緩和 (x86 & x64)  | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C + + MFC 適用于最新的適用于 v142 組建工具，具有 Spectre 緩和 (x86 & x64)  | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | 適用于最新適用于 v142 build tools (ARM) 的 c + + MFC | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C + + MFC 適用于具有 Spectre 緩和 (ARM) 的最新適用于 v142 組建工具 | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | 適用于最新適用于 v142 build tools (ARM64) 的 c + + MFC | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C + + MFC 適用于具有 Spectre 緩和 (的最新適用于 v142 build tools ARM64)  | 16.5.29721.120
VisualStudio （ARM64EC）。 | C + + MFC 適用于最新的適用于 v142 build tools (ARM64EC-實驗性)  | 16.9.31004.209
VisualStudio. ARM64EC. Spectre。 | C + + MFC 適用于具有 Spectre 緩和措施的最新適用于 v142 build tools (ARM64EC-實驗性)  | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 可轉散發 MSM | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC 適用于 v142-VS 2019 c + + ARM Spectre-降低 (最新) 的程式庫 | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC 適用于 v142-VS 2019 c + + ARM64 Spectre-降低 (最新) 的程式庫 | 16.9.31004.209
VisualStudio. ARM64EC. Spectre。 | MSVC 適用于 v142-VS 2019 c + + ARM64EC Spectre-減輕的程式庫 (最新-實驗性)  | 16.9.31004.209
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC 適用于 v142-VS 2019 c + + x64/x86 Spectre-降低 (最新) 的程式庫  | 16.9.31004.209
VisualStudio （ARM64EC）。 | MSVC 適用于 v142-VS 2019 c + + ARM64EC build tools (最新–實驗性)  | 16.9.31004.209
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
Microsoft.VisualStudio.Component.WinXP | 適用於 VS 2017 (v141) 工具的 C++ Windows XP 支援 [已淘汰] | 16.9.31004.209
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.9.31004.209
