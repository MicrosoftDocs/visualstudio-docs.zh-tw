---
title: Visual Studio 容器工具 Docker Compose 組建設定
author: ghogen
description: 容器工具組建流程的總覽
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 226078127d2fe61675a592bbafa06d732afc7c49
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826454"
---
# <a name="docker-compose-build-properties"></a>Docker Compose 組建屬性

除了可控制個別 Docker 專案的屬性（[容器工具組建屬性](container-msbuild-properties.md)中所述）之外，您也可以藉由設定 MSBuild 用來建立方案的 Docker Compose 屬性，自訂 Visual Studio 建立 Docker Compose 專案的方式。 您也可以藉由在 Docker Compose 設定檔案中設定檔案卷標，來控制 Visual Studio 偵錯工具如何執行 Docker Compose 應用程式。

## <a name="how-to-set-the-msbuild-properties"></a>如何設定 MSBuild 屬性

若要設定屬性的值，請編輯專案檔。 對於 Docker Compose 屬性，這個專案檔是副檔名為 docker-compose.dcproj 的檔案，除非下一節的表格中另有指示。 例如，假設您想要指定在開始進行偵錯工具時啟動瀏覽器。 您可以在 docker-compose.dcproj 專案檔中設定 `DockerLaunchAction` 屬性，如下所示。

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

您可以將屬性設定加入現有的 `PropertyGroup` 專案，如果沒有，則建立新的 `PropertyGroup` 元素。

## <a name="docker-compose-msbuild-properties"></a>Docker Compose MSBuild 屬性

下表顯示可用於 Docker Compose 專案的 MSBuild 屬性。

| 屬性名稱 | 位置 | 描述 | 預設值  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|docker-compose.dcproj|針對所有命令，在以分號分隔的清單中指定要傳送至 docker-compose.dev.debug.yml 的其他撰寫檔案。 允許來自 docker 撰寫專案檔（docker-compose.dcproj）的相對路徑。|-|
|DockerComposeBaseFilePath|docker-compose.dcproj|指定 docker 撰寫檔案之檔案名的第一個部分，不含副檔名*yml* 。 例如： <br>1. DockerComposeBaseFilePath = null/undefined：使用基底檔案路徑*docker-撰寫*，而檔案將命名為*docker-compose.dev.debug.yml. yml*和*docker-compose.dev.debug.yml。 yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*：檔案將命名為*mydockercompose. yml*和*mydockercompose. override. yml*<br> 3. DockerComposeBaseFilePath = *.。\mydockercompose*：檔案會在一個層級上啟動。 |docker-compose.dev.debug.yml|
|DockerComposeBuildArguments|docker-compose.dcproj|指定要傳遞給 `docker-compose build` 命令的額外參數。 例如：`--parallel --pull` |
|DockerComposeDownArguments|docker-compose.dcproj|指定要傳遞給 `docker-compose down` 命令的額外參數。 例如：`--timeout 500`|-|  
|DockerComposeProjectPath|.csproj 或 vbproj|Docker 撰寫專案（docker-compose.dcproj）檔案的相對路徑。 發佈服務專案時設定此屬性，以尋找儲存在 docker-compose.dev.debug.yml. yml 檔案中的相關聯映射組建設定。|-|
|DockerComposeUpArguments|docker-compose.dcproj|指定要傳遞給 `docker-compose up` 命令的額外參數。 例如：`--timeout 500`|-|
|DockerLaunchAction| docker-compose.dcproj | 指定要在 F5 或 Ctrl + F5 上執行的啟動動作。  允許的值為 None、LaunchBrowser 和 LaunchWCFTestClient|None|
|DockerLaunchBrowser| docker-compose.dcproj | 指出是否要啟動瀏覽器。 如果已指定 DockerLaunchAction，則會忽略。 | False |
|DockerServiceName| docker-compose.dcproj|如果指定了 DockerLaunchAction 或 DockerLaunchBrowser，則 DockerServiceName 就是應該啟動的服務名稱。  使用此屬性可判斷 docker 撰寫檔案可以參考的其中一個可能的專案將會啟動。|-|
|DockerServiceUrl| docker-compose.dcproj | 啟動瀏覽器時要使用的 URL。  有效的取代權杖為 "{ServiceIPAddress}"、"{ServicePort}" 和 "{圖式}"。  例如： {配置}：//{ServiceIPAddress}： {ServicePort}|-|
|DockerTargetOS| docker-compose.dcproj | 建立 Docker 映射時使用的目標 OS。|-|

## <a name="example"></a>範例

如果您變更 docker 撰寫檔案的位置，其方式是將 `DockerComposeBaseFilePath` 設定為相對路徑，您也必須確定組建內容已變更，使其參考方案資料夾。 例如，如果您的 docker 撰寫檔案是名為*DockerComposeFiles*的資料夾，則 docker 撰寫檔案應該將組建內容設定為 "..." 或 ".。/... "，視其相對於方案資料夾的位置而定。

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

*Mydockercompose. yml*檔案看起來應該像這樣，而組建內容設定為方案資料夾的相對路徑（在此案例中為 `..`）。

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
> DockerComposeBuildArguments、DockerComposeDownArguments 和 DockerComposeUpArguments 是 Visual Studio 2019 16.3 版的新功能。

## <a name="docker-compose-file-labels"></a>Docker Compose 檔案卷標

您也可以在與*docker-compose.dev.debug.yml*檔案相同的目錄中放置名為*docker-compose.dev.debug.yml*的檔案，或 Yml （適用于**debug**設定）或*docker-compose.dev.debug.yml. yml* （針對**發行**設定）來覆寫某些設定。  在此檔案中，您可以指定設定，如下所示：

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

如上述範例所示，使用雙引號括住值，並使用反斜線做為路徑中反斜線的 escape 字元。

|標籤名稱|描述|
|----------|-----------|
|visualstudio。引數|啟動偵錯工具時，傳遞給程式的引數。 針對 .NET Core 應用程式，這些引數通常是 NuGet 套件的額外搜尋路徑，後面接著專案輸出元件的路徑。|
|visualstudio 調試 killprogram。|此命令可用來停止在容器內執行的偵錯工具程式（如有必要）。|
|visualstudio 偵錯工具。|啟動偵錯工具時啟動的程式。 針對 .NET Core 應用程式，這種設定通常是**dotnet**。|
|visualstudio 調試 workingdirectory。|開始進行調試時，做為啟動目錄使用的目錄。 此設定通常是針對 Linux 容器 */app* ，或是適用于 Windows 容器的*C:\app* 。|

## <a name="customize-the-app-startup-process"></a>自訂應用程式啟動進程

您可以先執行命令或自訂腳本，再使用 `entrypoint` 設定啟動應用程式，並使其依賴設定。 例如，如果您只需要執行 `update-ca-certificates`，而不是在 [**發行**] 模式中，只在 [ **debug** ] 模式中設定憑證，您只能在*docker-compose.dev.debug.yml. yml*中新增下列程式碼：

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

如果您省略*docker-compose.dev.debug.yml. yml*或*docker-compose.dev.debug.yml. yml* ，則 Visual Studio 會根據預設值產生一個。

## <a name="next-steps"></a>後續步驟

如需有關 MSBuild 屬性的一般資訊，請參閱[Msbuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="see-also"></a>請參閱

[容器工具組建屬性](container-msbuild-properties.md)

[容器工具啟動設定](container-launch-settings.md)

[MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
