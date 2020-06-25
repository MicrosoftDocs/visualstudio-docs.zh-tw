---
title: Visual Studio 容器工具啟動設定
author: ghogen
description: 容器工具組建流程的總覽
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 07dd9dd4c5c61014eecf245719b142cdbaecbc38
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283329"
---
# <a name="container-tools-launch-settings"></a>容器工具啟動設定

在 ASP.NET Core 專案的 [*屬性*] 資料夾中，您可以在檔案上找到 launchSettings.js，其中包含的設定可控制您的 web 應用程式在開發電腦上的啟動方式。 如需有關如何在 ASP.NET 開發中使用此檔案的詳細資訊，請參閱[在 ASP.NET Core 中使用多個環境](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2)。 在*launchSettings.js開啟*[ **Docker** ] 區段中的設定，與 Visual Studio 處理容器化應用程式的方式有關。

::: moniker range="vs-2017"
```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

CommandName 設定會指出此區段適用于容器工具。 下表顯示可在此區段中設定的屬性：

::: moniker range="vs-2017"

|設定名稱|版本|範例|描述|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser"： true|指出是否要在成功啟動專案之後啟動瀏覽器。|
|launchUrl|Visual Studio 2017|"launchUrl"： "{配置}：//{ServiceHost}： {ServicePort}"|此 URL 會在啟動瀏覽器時使用。  此字串支援的取代標記為：<br>   {配置}-根據是否使用 SSL 而取代為 "HTTP" 或 "HTTPs"。<br>   {ServiceHost}-通常會以 "localhost" 取代。 不過，以 Windows 10 RS3 或更舊版本上的 Windows 容器為目標時，它會取代為容器的 IP。<br>   {ServicePort}-通常會使用 sslPort 或 HTTPPort 來取代，視是否使用 SSL 而定。  以 Windows 10 RS3 或更舊版本為目標的 Windows 容器時，會以 "443" 或 "80" 取代，視是否使用 SSL 而定。|

::: moniker-end

::: moniker range=">=vs-2019"

| 設定名稱         | 範例                                               | 描述                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| My.application.commandlineargs      | "My.application.commandlineargs"： "--mysetting myvalue"              | 在容器中啟動您的專案時，會使用這些命令列引數來啟動您的應用程式。                                     |
| environmentVariables | "environmentVariables"： {                             | 這些環境變數值會在容器中啟動時傳遞至進程。                       |
|                      | "ASPNETCORE_URLS"： " https://+:443 ; http://+:80 "，       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT"： "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| HTTPPort             | "HTTPPort"：24051                                     | 啟動容器時，主機上的此埠會對應至容器的埠80。                                |
|                      |                                                       | 如果未指定，則會從 iisSettings 值取得值。                                                          |
| launchBrowser        | "launchBrowser"： true                                 | 指出是否要在成功啟動專案之後啟動瀏覽器。                                       |
| launchUrl            | "launchUrl"： "{配置}：//{ServiceHost}： {ServicePort}" | 此 URL 會在啟動瀏覽器時使用。 此字串支援的取代標記為：                          |
|                      |                                                       | -{配置}-根據是否使用 SSL 而取代為 "HTTP" 或 "HTTPs"。                                   |
|                      |                                                       | -{ServiceHost}-通常會以 "localhost" 取代。                                                                    |
|                      |                                                       | 不過，以 Windows 10 RS3 或更舊版本上的 Windows 容器為目標時，它會取代為容器的 IP。           |
|                      |                                                       | -{ServicePort}-通常會使用 sslPort 或 HTTPPort 來取代，視是否使用 SSL 而定。                   |
|                      |                                                       | 不過，以 Windows 10 RS3 或更舊版本的 Windows 容器為目標時，它會取代為 "443" 或 "80"，         |
|                      |                                                       | 視是否使用 SSL 而定。                                                                                       |
| sslPort              | "sslPort"：44381                                      | 啟動容器時，主機上的此埠會對應至容器的埠443。                               |
|                      |                                                       | 如果未指定，則會從 iisSettings 值取得值。                                                          |
| useSSL               | "useSSL"： true                                        | 指出是否要在啟動專案時使用 SSL。 如果未指定 useSSL，則在 sslPort > 0 時，會使用 SSL。 |

::: moniker-end

## <a name="next-steps"></a>後續步驟

藉由設定 [[容器工具] 組建屬性](container-msbuild-properties.md)，來設定您的專案。

## <a name="see-also"></a>另請參閱

[Docker Compose 組建屬性](docker-compose-properties.md)
