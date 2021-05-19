---
title: Visual Studio 容器工具啟動設定
author: ghogen
description: 瞭解 Visual Studio 如何處理容器化應用程式的相關容器工具啟動設定。
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: e50935145913bcd1f3c4457f4704376a0ac0f6ef
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973235"
---
# <a name="container-tools-launch-settings"></a>容器工具啟動設定

在 ASP.NET Core 專案的 [ *屬性* ] 資料夾中，您可以找到檔案上的 launchSettings.js，其中包含的設定可控制您的 web 應用程式在開發電腦上的啟動方式。 如需有關如何在 ASP.NET 開發中使用此檔案的詳細資訊，請參閱 [在 ASP.NET Core 中使用多個環境](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true)。 在 *launchSettings.js* 中， **Docker** 區段中的設定與 Visual Studio 處理容器化應用程式的方式有關。

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

CommandName 設定會識別此區段適用于容器工具。 下表顯示可在此區段中設定的屬性：

::: moniker range="vs-2017"

|設定名稱|版本|範例|描述|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser"： true|指出是否要在成功啟動專案之後啟動瀏覽器。|
|launchUrl|Visual Studio 2017|"launchUrl"： "{配置}：//{ServiceHost}： {ServicePort}"|此 URL 會在啟動瀏覽器時使用。  此字串支援的替代權杖為：<br>   {配置}-根據是否使用 SSL，以 "HTTP" 或 "HTTPs" 取代。<br>   {ServiceHost}-通常取代為 "localhost"。 不過，以 Windows 10 RS3 或更舊版本上的 Windows 容器為目標時，它會以容器的 IP 取代。<br>   {ServicePort}-通常會以 sslPort 或 HTTPPort 取代，視是否使用 SSL 而定。  不過，以 Windows 10 RS3 或更舊版本上的 Windows 容器為目標時，會以 "443" 或 "80" 取代，視是否使用 SSL 而定。|

::: moniker-end

::: moniker range=">=vs-2019"

| 設定名稱         | 範例                                               | 描述                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| >my.application.commandlineargs      | ">my.application.commandlineargs"： "--出名為 mysetting myvalue"              | 當您在容器中啟動專案時，會使用這些命令列引數來啟動您的應用程式。                                     |
| environmentVariables | "environmentVariables"： {                             | 這些環境變數值會在容器中啟動時傳遞至進程。                       |
|                      | "ASPNETCORE_URLS"： " https://+:443 ; http://+:80 "，       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT"： "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| HTTPPort             | "HTTPPort"：24051                                     | 啟動容器時，主機上的此埠會對應至容器的埠80。                                |
|                      |                                                       | 如果未指定，則會從 iisSettings 值取得值。                                                          |
| launchBrowser        | "launchBrowser"： true                                 | 指出是否要在成功啟動專案之後啟動瀏覽器。                                       |
| launchUrl            | "launchUrl"： "{配置}：//{ServiceHost}： {ServicePort}" | 此 URL 會在啟動瀏覽器時使用。 此字串支援的替代權杖為：                          |
|                      |                                                       | -{配置}-根據是否使用 SSL，以 "HTTP" 或 "HTTPs" 取代。                                   |
|                      |                                                       | -{ServiceHost}-通常取代為 "localhost"。                                                                    |
|                      |                                                       | 不過，以 Windows 10 RS3 或更舊版本上的 Windows 容器為目標時，它會以容器的 IP 取代。           |
|                      |                                                       | -{ServicePort}-通常會以 sslPort 或 HTTPPort 取代，視是否使用 SSL 而定。                   |
|                      |                                                       | 不過，以 Windows 10 RS3 或更舊版本上的 Windows 容器為目標時，它會以 "443" 或 "80" 取代。         |
|                      |                                                       | 取決於是否使用 SSL。                                                                                       |
| sslPort              | "sslPort"：44381                                      | 啟動容器時，主機上的此埠會對應至容器的埠443。                               |
|                      |                                                       | 如果未指定，則會從 iisSettings 值取得值。                                                          |
| useSSL               | "useSSL"： true                                        | 指出是否要在啟動專案時使用 SSL。 如果未指定 useSSL，則會在 sslPort > 0 時使用 SSL。 |

::: moniker-end

## <a name="next-steps"></a>下一步

藉由設定 [容器工具組建屬性](container-msbuild-properties.md)來設定您的專案。

## <a name="see-also"></a>另請參閱

- [Docker Compose 組建屬性](docker-compose-properties.md)
- [管理 Docker Compose 的啟動設定檔](launch-profiles.md)
