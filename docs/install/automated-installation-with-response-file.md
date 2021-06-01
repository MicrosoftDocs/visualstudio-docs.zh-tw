---
title: 使用回應檔自動化安裝
description: 了解如何建立可協助您自動化 Visual Studio 安裝的 JSON 回應檔
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7554ac46d7c4171cfb71166c51689ff4ae95c0d5
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724547"
---
# <a name="automate-installs-by-using-settings-in-a-response-file"></a>使用回應檔中的設定自動安裝

部署 Visual Studio 的系統管理員可以使用 `--in` 參數指定回應檔，如下列範例所示：

```cmd
vs_enterprise.exe --in customInstall.json
```

回應檔是 [JSON](http://json-schema.org/) 檔案，其內容會鏡像命令列引數。  一般而言，如果命令列參數未採用任何引數 (例如 `--quiet`、`--passive` 等)，則回應檔中的值應該為 true/false。  如果命令列參數採用引數 (例如 `--installPath <dir>`)，則回應檔中的值應該為字串。  如果命令列參數採用引數且可在命令列上出現多次 (例如 `--add <id>`)，則其應該為字串陣列。

命令列上指定的參數會覆寫回應檔中的設定，但不含參數採用多個輸入時 (例如 `--add`)。 當您有多個輸入時，會合併命令列上提供的輸入與回應檔中的設定。

## <a name="setting-a-default-configuration-for-visual-studio"></a>設定 Visual Studio 的預設設定

如果您利用 `--layout` 建立了網路配置快取，即會在配置中建立初始的 `response.json` 檔案。 如果您建立部分配置，則此回應檔會包含配置中所含的工作負載和語言。  從此配置中執行安裝程式時，會自動使用這個 response.json 檔案，以選取配置中所含的工作負載和元件。  在安裝 Visual Studio 之前，使用者仍然可以選取或取消選取安裝程式 UI 中的任何工作負載。

建立配置的系統管理員可以修改配置中的 `response.json` 檔案，以控制使用者從配置中安裝 Visual Studio 時所看到的預設設定。  例如，如果系統管理員想要預設安裝的特定工作負載和元件，則可以設定 `response.json` 檔案來進行新增。

從配置資料夾執行 Visual Studio 安裝程式時，會「自動」使用配置資料夾中的回應檔。  您不需要使用 `--in` 選項。

您可以更新於離線配置資料夾中建立的 `response.json` 檔案，以針對從此配置安裝的使用者定義預設設定。

> [!WARNING]
> 請務必讓現有屬性保留為建立配置時所定義的樣子。

配置中的基底 `response.json` 檔案應該與下列範例類似，差異在於它會包含您想要安裝之產品和通道的值：

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

當您建立或更新配置時，也會建立 response.template.json 檔案。  這個檔案會包含可使用的所有工作負載、元件和語言識別碼。  針對自訂安裝中可以包含的所有項目，會提供此檔案作為範本。  系統管理員可以使用這個檔案作為自訂回應檔的起點。  只需要移除您不想要安裝之項目的識別碼，並將它儲存在您自己的回應檔中。  請不要自訂 response.template.json 檔案，否則，只要更新配置，您的變更就會遺失。

## <a name="example-layout-response-file-content"></a>範例配置回應檔的內容

下列範例會安裝 Visual Studio Enterprise 與六個常見的工作負載和元件，以及英文和法文 UI 語言。 您可以使用這個範例作為範本；只需要將工作負載和元件變更為您想要安裝的工作負載和元件：

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2019",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
* [當您安裝或使用 Visual Studio 時針對網路相關錯誤進行疑難排解](troubleshooting-network-related-errors-in-visual-studio.md)
