---
title: Docker Compose 組建設定
author: ghogen
description: 瞭解如何編輯 Docker Compose 組建屬性，以自訂 Visual Studio 建立和執行 Docker Compose 應用程式的方式。
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 7f1ebb11133c640c2e0bdcfd84660592792d4205
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825000"
---
# <a name="docker-compose-build-properties"></a>Docker Compose 組建屬性

除了控制個別 Docker 專案的屬性（如 [容器工具組建屬性](container-msbuild-properties.md)中所述），您也可以藉由設定 MSBuild 用來建立方案的 Docker Compose 屬性，自訂 Visual Studio 建立 Docker Compose 專案的方式。 您也可以藉由在 Docker Compose 設定檔中設定檔案卷標，來控制 Visual Studio 偵錯工具如何執行 Docker Compose 應用程式。

## <a name="how-to-set-the-msbuild-properties"></a>如何設定 MSBuild 屬性

若要設定屬性的值，請編輯專案檔。 針對 Docker Compose 屬性，除非在下一節的表格中另有說明，否則這個專案檔是副檔名為 docker-compose.dcproj 的專案檔。 例如，假設您想要指定在啟動偵錯工具時啟動瀏覽器。 您可以 `DockerLaunchAction` 在 docker-compose.dcproj 專案檔案中設定屬性，如下所示。

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

您可以將屬性設定加入至現有的專案 `PropertyGroup` ，如果沒有，則建立新的 `PropertyGroup` 元素。

## <a name="docker-compose-msbuild-properties"></a>Docker Compose MSBuild 屬性

下表顯示可用於 Docker Compose 專案的 MSBuild 屬性。

| 屬性名稱 | Location | 描述 | 預設值  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|docker-compose.dcproj|以分號分隔的清單，指定要傳送給所有命令 docker-compose.exe 的其他撰寫檔。 允許 (docker-compose.dcproj) 的 docker 撰寫專案檔的相對路徑。|-|
|DockerComposeBaseFilePath|docker-compose.dcproj|指定 docker 組成檔案的第一個部分，不含副檔名為 *yml* 的檔案。 例如： <br>1. DockerComposeBaseFilePath = null/undefined：使用以 *docker 撰寫* 的基底檔案路徑，檔案將命名為 *>docker-compose.yml. yml* 和 *>docker-compose.yml. yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*：檔案將命名為 *mydockercompose. yml* 和 *mydockercompose。 yml*<br> 3. DockerComposeBaseFilePath = *.。。\mydockercompose*：檔案將會啟動一個層級。 |>docker-compose.yml|
|DockerComposeBuildArguments|docker-compose.dcproj|指定要傳遞給命令的額外參數 `docker-compose build` 。 例如， `--parallel --pull` |
|DockerComposeDownArguments|docker-compose.dcproj|指定要傳遞給命令的額外參數 `docker-compose down` 。 例如， `--timeout 500`|-|
|DockerComposeProjectName| docker-compose.dcproj | 如果有指定，會覆寫 docker 撰寫專案的專案名稱。 | "dockercompose" + 自動產生的雜湊 |
|DockerComposeProjectPath|.csproj 或 vbproj|Docker 撰寫專案的相對路徑 (docker-compose.dcproj) 檔。 發佈服務專案時設定此屬性，以尋找儲存在 >docker-compose.yml. yml 檔案中的相關聯映射組建設定。|-|
|DockerComposeUpArguments|docker-compose.dcproj|指定要傳遞給命令的額外參數 `docker-compose up` 。 例如， `--timeout 500`|-|
|DockerDevelopmentMode|docker-compose.dcproj| 控制是否啟用「內部主機」優化 ( 「快速模式」的偵錯工具) 。  允許的值為 `Fast` 和 `Regular` 。 | `Fast` 在 Debug 設定或 `Regular` 所有其他設定中 |
|DockerLaunchAction| docker-compose.dcproj | 指定要在 F5 或 Ctrl + F5 執行的啟動動作。  允許的值為 None、LaunchBrowser 和 LaunchWCFTestClient。|無|
|DockerLaunchBrowser| docker-compose.dcproj | 指出是否要啟動瀏覽器。 如果已指定 DockerLaunchAction，則會忽略。 | 否 |
|DockerServiceName| docker-compose.dcproj|如果指定了 DockerLaunchAction 或 DockerLaunchBrowser，則 DockerServiceName 是應啟動之服務的名稱。  您可以使用這個屬性來判斷哪些專案可能會啟動 docker 組成檔案可以參考的專案。|-|
|DockerServiceUrl| docker-compose.dcproj | 要在啟動瀏覽器時使用的 URL。  有效的取代權杖為 "{ServiceIPAddress}"、"{ServicePort}" 和 "{配置}"。  例如： {配置}：//{ServiceIPAddress}： {ServicePort}|-|
|DockerTargetOS| docker-compose.dcproj | 建立 Docker 映射時所使用的目標 OS。|-|

## <a name="example"></a>範例

如果您變更 docker 撰寫檔案的位置，藉由設定 `DockerComposeBaseFilePath` 為相對路徑，您也必須確定組建內容已變更，使其參考方案資料夾。 例如，如果您的 docker 撰寫檔案是名為 *DockerComposeFiles* 的資料夾，則 docker 撰寫檔案應該將組建內容設定為 "..." 或 ".。。/...」，視其相對於方案資料夾的位置而定。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

*Mydockercompose. yml* 檔案看起來應該像這樣，但組建內容設定為解決方案資料夾的相對路徑 (在此案例中， `..`) 。

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments、DockerComposeDownArguments 和 DockerComposeUpArguments 是 Visual Studio 2019 16.3 版中的新功能。

## <a name="overriding-visual-studios-docker-compose-configuration"></a>覆寫 Visual Studio 的 Docker Compose 設定

您可以覆寫某些設定，方法是將名為 *>docker-compose.yml* 的檔案放在 yml (的 **快速** 模式) 或 *>docker-compose.yml。 yml* (適用于 **一般** 模式) 在與 *>docker-compose.yml. yml* 檔案相同的目錄中。 

>[!TIP] 
>若要找出任何這些設定的預設值，請查看 *>docker-compose.yml. yml* 或 *>docker-compose.yml. yml. g.*。

### <a name="docker-compose-file-labels"></a>Docker Compose 檔標籤

 在 *>docker-compose.yml* 中，您可以在 yml 或 *>docker-compose.yml* 中定義覆寫特定標籤，如下所示：

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

使用雙引號括住值（如上述範例所示），並使用反斜線做為路徑中反斜線的 escape 字元。

|標籤名稱|Description|
|----------|-----------|
|visualstudio。引數|啟動偵錯工具時傳遞給程式的引數。 若是 .NET Core 應用程式，這些引數通常是 NuGet 套件的額外搜尋路徑，後面接著專案輸出元件的路徑。|
|visualstudio.. 程式|啟動偵錯工具時啟動的程式。 若是 .NET Core 應用程式，這項設定通常是 **dotnet**。|
|visualstudio. workingdirectory。|開始調試時當做起始目錄使用的目錄。 這項設定通常會 */app* 適用于 Linux 容器，或適用于 Windows 容器的 *C:\app* 。|
|visualstudio. killprogram。|此命令可用來停止在容器內執行的偵錯工具程式 (必要時) 。|

### <a name="customize-the-docker-build-process"></a>自訂 Docker 組建進程

您可以使用屬性中的設定，宣告要在 Dockerfile 中建立的階段 `target` `build` 。 此覆寫只能用在 >docker-compose.yml. *yml* 或 >docker-compose.yml 中。 *yml* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>自訂應用程式啟動進程

您可以使用設定來執行命令或自訂腳本，然後再啟動應用程式 `entrypoint` ，並使其相依于 `DockerDevelopmentMode` 。 例如，如果您只需要在執行的 **快速** 模式中設定憑證 `update-ca-certificates` ，而不是在 **一般** 模式下，則 **只能** 在 *>docker-compose.yml 和 yml* 中新增下列程式碼：

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>下一步

如需 MSBuild 屬性的一般資訊，請參閱 [Msbuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="see-also"></a>另請參閱

[容器工具組建屬性](container-msbuild-properties.md)

[容器工具啟動設定](container-launch-settings.md)

[MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
