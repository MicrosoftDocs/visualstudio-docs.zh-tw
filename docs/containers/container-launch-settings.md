---
title: 視覺化工作室容器工具啟動設定
author: ghogen
description: 容器工具產生流程概述
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 63cf881fdedf9608d5cb773bbcb6b969a0f51624
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472653"
---
# <a name="container-tools-launch-settings"></a>容器工具啟動設定

在ASP.NET核心專案中的 *「屬性」* 資料夾中,您可以找到啟動Settings.json檔,該檔包含控制開發電腦上 Web 應用啟動方式的設定。 有關此檔案在ASP.NET開發中如何使用的詳細資訊,請參閱[在 ASP.NET 酷中使用多個環境](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2)。 在*啟動設置.json*中 **,"Docker"** 部分中的設置與 Visual Studio 處理容器化應用的方式有關。

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

命令名稱設置標識此部分適用於容器工具。 下表顯示了可在本節中設置的屬性:

::: moniker range="vs-2017"

|設定名稱|版本|範例|描述|
|------------|-------|-------|---------------|
|啟動瀏覽器|Visual Studio 2017|"啟動瀏覽器":真|指示在成功啟動專案後是否啟動瀏覽器。|
|啟動網址|Visual Studio 2017|"啟動Url":"[計劃][服務主機]:[服務埠]"|啟動瀏覽器時使用此 URL。  此字串受支援的取代權杖包括:<br>   [Scheme] - 替換為"HTTP"或"Ht',,具體取決於是否使用 SSL。<br>   [服務主機] - 通常替換為"本地主機"。 但是,在 Windows 10 RS3 或更舊版上定位 Windows 容器時,它將替換為容器的 IP。<br>   [服務埠] - 通常替換為 sslPort 或 HTTPPort,具體取決於是否使用 SSL。  但是,在 Windows 10 RS3 或更舊版上定位 Windows 容器時,根據是否使用 SSL,它將替換為"443"或"80"。|

::: moniker-end

::: moniker range=">=vs-2019"

| 設定名稱         | 範例                                               | 描述                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 指令LineArgs      | "命令線":"-我的價值"              | 在容器中啟動專案時,將使用用於啟動應用的這些命令列參數。                                     |
| 環境變數 | "環境變數": |                             | 當這些環境變數值在容器中啟動時,它將傳遞到進程。                       |
|                      | "ASPNETCORE_URLS":"";""";"https://+:443http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT":"44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| HTTPPort             | "HTTPPort": 24051                                     | 啟動容器時,主機上的此埠將映射到容器的埠 80。                                |
|                      |                                                       | 如果未指定,則該值取自 iisSettings 值。                                                          |
| 啟動瀏覽器        | "啟動瀏覽器":真                                 | 指示在成功啟動專案後是否啟動瀏覽器。                                       |
| 啟動網址            | "啟動Url":"[計劃][服務主機]:[服務埠]" | 啟動瀏覽器時使用此 URL。 此字串受支援的取代權杖包括:                          |
|                      |                                                       | - [Scheme] - 替換為"HTTP"或"Ht',具體取決於是否使用 SSL。                                   |
|                      |                                                       | - [服務主機] - 通常替換為"本地主機"。                                                                    |
|                      |                                                       | 但是,在 Windows 10 RS3 或更舊版上定位 Windows 容器時,它將替換為容器的 IP。           |
|                      |                                                       | - [服務埠] - 通常替換為 sslPort 或 HTTPPort,具體取決於是否使用 SSL。                   |
|                      |                                                       | 但是,當在 Windows 10 RS3 或更舊版上定位 Windows 容器時,它將替換為「443」或「80」,         |
|                      |                                                       | 取決於是否使用 SSL。                                                                                       |
| sslPort              | "sslPort": 44381                                      | 啟動容器時,主機上的此埠映射到容器的埠 443。                               |
|                      |                                                       | 如果未指定,則該值取自 iisSettings 值。                                                          |
| 使用SSL               | "使用 SSL":真                                        | 指示在啟動專案時是否使用 SSL。 如果未指定使用 SSL,則當 sslPort > 0 時使用 SSL。 |

::: moniker-end

## <a name="next-steps"></a>後續步驟

通過設置[容器工具生成屬性](container-msbuild-properties.md)來配置專案。

## <a name="see-also"></a>另請參閱

[Docker 組合產生屬性](docker-compose-properties.md)
