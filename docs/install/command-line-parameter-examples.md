---
title: 適用於安裝的命令列參數範例
description: 自訂這些範例來建立您自己的 Visual Studio 命令列安裝。
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5685de34235dcd9b903cbf5be6371ebf3f1e84c3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307540"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Visual Studio 安裝的命令列參數範例

為了說明如何[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)，以下是幾個範例，您可以自訂以符合您的需求。

在每個範例中，`vs_enterprise.exe`、`vs_professional.exe` 和 `vs_community.exe` 表示 Visual Studio 啟動載入器的個別版本，這是起始下載程序的小型檔案 (約 1 MB)。 如果您使用不同的版本，請取代為適當的啟動載入器名稱。

> [!NOTE]
> 所有命令都需要提升系統管理權限，如果未從已提升權限的提示字元啟動程序，則會顯示 [使用者帳戶控制] 提示。
>
> [!NOTE]
> 您可以在命令列結尾處使用 `^` 字元，將多行串連成單一命令。 或者，您也可以直接將這幾行放到一列。 在 PowerShell 中，對等項目為倒引號 (`` ` ``) 字元。

如需您可以使用命令列安裝的工作負載和元件的清單，請參閱 [Visual Studio 工作負載和元件識別碼](workload-and-component-ids.md)頁面。

## <a name="using---installpath"></a>使用 --installPath

* 安裝 Visual Studio 的最小執行個體，不會顯示互動式提示，但會顯示進度：

  ```shell
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* 使用命令列更新 Visual Studio 執行個體，不顯示互動式提示，但顯示進度：

   ```shell
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > 這兩個命令都有建議。 第一個命令更新 Visual Studio 安裝程式。 第二個命令更新 Visual Studio 執行個體。 若要避免 [使用者帳戶控制] 對話方塊，請以系統管理員身分執行命令提示字元。

* 使用法文語言套件以無訊息方式安裝 Visual Studio 的桌面執行個體，並只在安裝產品時傳回。

  ```shell
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>使用 --wait

* 在批次檔或指令碼中使用，以等候 Visual Studio 安裝程式完成，然後再執行下一個命令。 For batch files, an `%ERRORLEVEL%` environment variable will contain the return value of the command, as documented in the [Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md) page. 有些命令公用程式需要額外的參數來等候完成，以及取得安裝程式的傳回值。 以下為與 PowerShell 指令碼命令 'Start-Process' 搭配使用的其他參數範例：

   ```shell
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $process = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   Write-Output $process.ExitCode 
   ```

   或

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* 第一個 '--wait ' 會由 Visual Studio 安裝程式所使用，而 'Start-Process' 會使用第二個 '-Wait' 來等候完成。 'Start-Process' 會使用 '-PassThru' 參數，來使用安裝程式的結束代碼作為其傳回值。

## <a name="using---layout"></a>使用 --layout

* 下載 Visual Studio 核心編輯器 (最基本的 Visual Studio 設定)。 只包含英文語言套件：

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* 下載 .NET 桌面和 .NET Web 工作負載，以及所有建議的元件和 GitHub 延伸模組。 只包含英文語言套件：

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>使用 --all

* 啟動 Visual Studio Enterprise 版中可用的所有工作負載和元件互動式安裝：

   ```shell
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>使用 --includeRecommended

* 在已安裝 Visual Studio Community 版電腦上安裝第二個名為 Visual Studio Professional 的執行個體，並提供 Node.js 開發的支援：

   ```shell
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>使用 --remove

::: moniker range="vs-2017"

* 從預設安裝的 Visual Studio 執行個體移除程式碼剖析工具元件：

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* 從預設安裝的 Visual Studio 執行個體移除程式碼剖析工具元件：

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range=">=vs-2022"

* 從預設安裝的 Visual Studio 執行個體移除程式碼剖析工具元件：

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>使用 --path

::: moniker range="vs-2017"

這些命令列參數是 **在 15.7 中新增的**。 如需詳細資訊，請參閱 [Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md) (使用命令列參數安裝 Visual Studio) 頁面。

::: moniker-end

* 使用安裝、快取和共用路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* 只使用安裝和快取路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* 只使用安裝和共用路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* 只使用安裝路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>使用 export

::: moniker range="vs-2017"

此命令列命令是 **15.9 中的新功能**。 如需其詳細資訊，請參閱[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 頁面。

::: moniker-end

* 使用 export 可儲存來自安裝的選取項目：

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* 使用 export 可從頭開始儲存自訂選取項目：

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>使用 --config

::: moniker range="vs-2017"

此命令列參數是 **15.9 中的新功能**。 如需其詳細資訊，請參閱[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 頁面。

::: moniker-end

* 使用 --config 可從先前儲存的安裝組態檔安裝工作負載和元件：

  ```shell
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* 使用 --config 可將工作負載和元件新增至現有的安裝：

  ```shell
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
