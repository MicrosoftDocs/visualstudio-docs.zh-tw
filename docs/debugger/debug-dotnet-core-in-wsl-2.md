---
title: 在 WSL 2 中偵錯工具 .NET Core 應用程式
description: 瞭解如何在 WSL 2 中執行和偵測您的 .NET Core 應用程式，而不需要離開 Visual Studio。
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 6ae43b79b9db766d752a25fb538b7f208e6f5e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865614"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>使用 Visual Studio 在 WSL 2 中調試 .NET Core 應用程式

您可以輕鬆地在 Linux 中執行和錯用 .NET Core 應用程式，而不需要離開 Visual Studio 使用 WSL 2。 如果您是跨平臺開發人員，您可以使用此方法來測試更多目標環境的簡單方式。

針對以 Linux 為目標的 Windows .NET 使用者，WSL 2 在生產環境的真實性與生產力之間有最棒的地方。 在 Visual Studio 中，您可以在遠端 Linux 環境中使用 [遠端偵錯程式](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)或使用 [容器工具](../containers/overview.md)的容器來進行偵錯工具。 如果您的主要考慮是生產環境，您應該使用其中一個選項。 當簡單快速的內部迴圈更為重要時，WSL 2 是絕佳的選擇。

您不需要只選擇一個方法！ 您可以在相同的專案中有 Docker 和 WSL 2 的啟動設定檔，並挑選哪一個適合特定執行。 部署應用程式之後，如果發生問題，您隨時都可以使用遠端偵錯程式來附加至該應用程式。

## <a name="prerequisites"></a>必要條件

- Visual Studio 2019 v 16.9 Preview 1 或更新版本，搭配使用 .NET Core 與 WSL 2 選擇性元件的調試。

  使用 .NET Core 跨平臺或 ASP.NET 和網頁程式開發工作負載時，預設會包含選用元件。 您必須安裝其中一個或兩個工作負載。

- 安裝 [WSL 2](/windows/wsl/about)。

- 安裝您選擇的 [散發](https://aka.ms/wslstore) 套件。

## <a name="start-debugging-with-wsl-2"></a>開始使用 WSL 2 進行調試

1. 安裝必要的元件之後，請在 Visual Studio 中開啟 ASP.NET Core 的 web 應用程式或 .NET Core 主控台應用程式，您會看到名為 WSL 2 的新啟動設定檔：

   ![啟動配置檔案清單中的 WSL 2 啟動設定檔](media/linux-wsl2-debugging-select-launch-profile.png)

1. 選取此設定檔，將它新增至您 *的launchSettings.js*。

   下列範例會顯示檔案中的某些索引鍵屬性。

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   一旦您選取新的設定檔，此延伸模組會檢查您的 WSL 2 發佈是否已設定為執行 .NET Core 應用程式，並協助您安裝任何遺漏的相依性。 安裝這些相依性之後，您就可以在 WSL 2 中進行 debug。

1. 如往常般開始進行偵錯工具，您的應用程式將會在預設的 WSL 2 分佈中執行。

   驗證您在 Linux 中執行的簡單方法是檢查的值 `Environment.OSVersion` 。

>[!NOTE]
> 只有 Ubuntu 和 Debian 經過測試且受支援。 .NET Core 支援的其他散發套件應該可以運作，但需要手動安裝 [.Net Core 運行](https://aka.ms/wsldotnet) 時間和 [捲曲](https://curl.haxx.se/)。

## <a name="choose-a-specific-distribution"></a>選擇特定的散發

根據預設，WSL 2 啟動設定檔會使用 *wsl.exe* 中設定的預設散發。 如果您想要讓啟動設定檔以特定發佈為目標，則不論該預設值為何，您都可以修改啟動設定檔。 例如，如果您要對 web 應用程式進行偵錯工具，並想要在 Ubuntu 20.04 上進行測試，您的啟動設定檔看起來會像這樣：

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>目標多個散發套件

如果您正在處理需要在多個散發套件中執行的應用程式，而且想要快速測試每個散發套件，您可以有多個啟動設定檔。 比方說，如果您需要在 Debian、Ubuntu 18.04 和 Ubuntu 20.04 上測試主控台應用程式，您可以使用下列啟動設定檔：

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

使用這些啟動設定檔時，您可以輕鬆地在目標散發之間來回切換，而不需要離開 Visual Studio。

![啟動配置檔案清單中的多個 WSL 2 啟動設定檔](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>啟動設定檔中的 WSL 設定

下表顯示啟動設定檔中支援的設定。

|名稱|預設|目的|支援權杖？|
|-|-|-|-|
|executablePath|dotnet|要執行的可執行檔|是|
|>my.application.commandlineargs|TargetPath 對應至 WSL 環境的 MSBuild 屬性值|傳遞至 executablePath 的命令列引數|是|
|workingDirectory|主控台應用程式： {*OutDir*}</br>針對 web 應用程式： {*ProjectDir*}|要啟動調試的工作目錄|是|
|environmentVariables||要針對已調試的進程設定之環境變數的索引鍵值組。|是|
|setupScriptPath||要在進行調試之前執行的腳本。 適用于執行 ~/.bash_profile 等腳本。|是|
|distributionName||要使用之 WSL 散發的名稱。|否|
|launchBrowser|false|是否要啟動瀏覽器|否|
|launchUrl||LaunchBrowser 為 true 時要啟動的 Url|否|

支援的權杖：

{*ProjectDir*}-專案目錄的路徑

{*OutDir*}-MSBuild 屬性的值 `OutDir`

>[!NOTE]
> 所有路徑都適用于 WSL 而非 Windows。
