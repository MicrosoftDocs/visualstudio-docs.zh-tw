---
title: 管理 Docker Compose 專案的啟動設定檔
description: 瞭解如何使用 Docker Compose 啟動設定檔，以及控制當您在 Visual Studio 中使用 Docker Compose 時要啟動哪些服務。
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e740ea3b7950c14bf11522c4e438a105b09eb7f6
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433697"
---
# <a name="manage-launch-profiles-for-docker-compose"></a>管理 Docker Compose 的啟動設定檔

如果您的應用程式是由多個服務所組成並使用 Docker Compose，您可以在 Docker Compose 啟動設定中建立或編輯現有的啟動設定檔，以設定要執行和偵測的服務。 啟動設定檔可讓您以動態方式只執行與目前案例相關的服務。 您可以建立和選取啟動設定檔，以自訂您的偵錯工具體驗，並設定特定的啟動動作（例如） `Browser Launch URL` 。 您也可以選擇個別選擇每項服務，或選擇 Docker Compose 設定檔，這也會查看您的撰寫檔案，以判斷要執行的服務群組。

如需 Docker Compose 設定檔的詳細資訊，請參閱 [使用設定檔搭配撰寫](https://docs.docker.com/compose/profiles/)。
 
## <a name="prerequisites"></a>必要條件

- [Visual Studio 2019 16.10 版](https://visualstudio.microsoft.com/vs/) 或更新版本
- 具有[Docker Compose 容器協調流程](tutorial-multicontainer.md)的解決方案

## <a name="manage-launch-settings"></a>管理啟動設定

請考慮下列 Docker Compose 專案，其中 *>docker-compose.yml yml* 有五個服務和三個撰寫設定檔 (web、web1 和 web2) 。

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

有幾個選項可以開啟 Docker Compose 啟動設定] 對話方塊：
- 在 Visual Studio 中，選擇 [ **Debug**  >  **管理] Docker Compose 啟動設定**：

    ![Debug [管理撰寫設定] 功能表項目的螢幕擷取畫面](media/launch-settings/debug-dropdown-manage-compose.png)

- 以滑鼠右鍵按一下 Visual Studio `docker-compose` 專案，然後選取 [**管理 Docker Compose 啟動設定**]

    ![內容功能表項目的螢幕擷取畫面](media/launch-settings/launch-settings-context-menu.png)

- 使用快速啟動 (**Ctrl** + **Q**) 並搜尋 **Docker Compose** 以尋找上述命令。

在下列範例中， `web1` 已選取 [撰寫設定檔]，這會將 **服務** 清單篩選為該設定檔中包含的三個以外的三個：

![「啟動設定對話方塊的螢幕擷取畫面」](media/launch-settings/launch-settings-create-profile.png)

只有在 *>docker-compose.yml. yml* 檔案中定義了設定檔時，才會出現 [Docker Compose 設定檔] 區段。

下一個範例示範如何在個別服務之間進行選取，而不是篩選至撰寫設定檔中的服務。 在這裡，我們會示範當您建立新的啟動設定檔（名為）時，此對話方塊會顯示一個新的啟動設定檔 `test2` ，其中只會啟動兩個服務， `webapplication1` 其中包含偵錯工具和 `webapplication2` 不進行  此啟動設定檔也會在應用程式啟動時啟動瀏覽器，並將它開啟至的首頁 `webapplication1` 。 

![取消選取某些服務的 [啟動設定] 對話方塊螢幕擷取畫面](media/launch-settings/launch-settings-selected.png)

這項資訊會儲存在 *launchSettings.js* 中，如下所示

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>建立使用 Docker Compose 設定檔的啟動設定檔

您也可以建立使用撰寫設定檔的 Visual Studio 啟動設定檔，以進一步自訂啟動行為。

若要建立另一個使用撰寫設定檔的設定檔，請選取 [ **使用 Docker Compose 設定檔** ]，然後選擇 `web1` 。 現在啟動設定檔包含三個服務– `webapplication1` (屬於 `web` 和 `web1` 組成設定檔) 和 `external1` `external2` 。 依預設，不含原始程式碼的服務（例如 `external1` 和）會  `external2` 在不進行 **調試** 程式的情況下啟動預設動作。 使用原始程式碼的 .NET 應用程式將會預設為 **啟動調試** 程式。

> [!IMPORTANT]
> 如果服務未指定撰寫設定檔，則會隱含地將它包含在所有撰寫設定檔中。

![已建立另一個設定檔的 [啟動設定] 對話方塊螢幕擷取畫面](media/launch-settings/launch-settings-create-profile.png)

這項資訊將會儲存，如下列程式碼所示。 除非您變更預設動作，否則不會儲存服務的設定和其預設動作。

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

您也可以變更 >webapplication1.precompiledviews.dll 的動作，以在不進行偵錯工具的 **情況下啟動**。 *launchSettings.js* 中的設定，則看起來會像下列程式碼：

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>屬性

以下是 *launchSettings.js* 中每個屬性的描述：

|屬性| 描述|
| - | - |
|commandName| 命令的名稱。 預設值為 "DockerCompose"|
|commandVersion| 用來管理 DockerCompose 啟動設定檔架構的版本號碼。|
|composeProfile| 定義啟動設定檔定義的父屬性。 其子屬性為 `includes` 和 `serviceActions`|
|composeProfile-include | 組成啟動設定檔的組成設定檔名稱清單。|
|composeProfile-Serviceactions 所 | 列出選取的組成設定檔、服務，以及每個服務的啟動動作|
|Serviceactions 所 | 列出選取的服務和啟動動作。|
|composeLaunchServiceName| 如果指定了 DockerLaunchAction 或 DockerLaunchBrowser，DockerServiceName 就是應啟動的服務名稱。 您可以使用這個屬性來判斷 Docker Compose 檔案中的哪個服務將會啟動。|
|composeLaunchAction| 指定要在 **f5** 或 **Ctrl** F5 執行的啟動動作 + ****。 允許的值為 None、LaunchBrowser 和 LaunchWCFTestClient。|
|composeLaunchUrl| 要在啟動瀏覽器時使用的 URL。 有效的取代權杖為 "{ServiceIPAddress}"、"{ServicePort}" 和 "{配置}"。 例如： {配置}：//{ServiceIPAddress}： {ServicePort}|

## <a name="next-steps"></a>下一步

若要深入瞭解容器工具的運作方式，請閱讀 [Visual Studio 容器工具組建和偵錯工具總覽](container-build.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 容器工具啟動設定](container-launch-settings.md)

- [Docker Compose 組建設定](docker-compose-properties.md)
