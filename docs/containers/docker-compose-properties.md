---
title: 視覺化工作室容器工具 Docker 撰寫生成設置
author: ghogen
description: 容器工具生成流程概述
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 85cb8745a14439cfb09036a1bc96e6bd0fa15ae4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988510"
---
# <a name="docker-compose-build-properties"></a>Docker 組合生成屬性

除了容器[工具生成屬性](container-msbuild-properties.md)中描述的控制單個 Docker 專案的屬性外，還可以通過設置 MSBuild 用於構建解決方案的 Docker 合成屬性來自訂 Visual Studio 如何構建 Docker 合成專案。 您還可以通過在 Docker Compose 設定檔中設置檔標籤來控制視覺化工作室調試器如何運行 Docker 合成應用。

## <a name="how-to-set-the-msbuild-properties"></a>如何設置 MSBuild 屬性

要設置屬性的值，請編輯專案檔案。 對於 Docker Compose 屬性，此專案檔案是具有 .dcproj 副檔名的檔，除非在下一節中的表中另有說明。 例如，假設您要指定在開始調試時啟動瀏覽器。 您可以在 .dcproj 專案檔案中設置`DockerLaunchAction`屬性，如下所示。

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

您可以將屬性設置添加到現有`PropertyGroup`元素，如果沒有，則創建新`PropertyGroup`元素。

## <a name="docker-compose-msbuild-properties"></a>Docker Compose MSBuild 屬性

下表顯示了可用於 Docker 撰寫專案的 MSBuild 屬性。

| 屬性名稱 | Location | 描述 | 預設值  |
|---------------|----------|-------------|----------------|
|其他組合檔路徑|直流普羅伊|指定分號分隔清單中的其他撰寫檔，以便發送到所有命令的 docker-compose.exe。 允許從 Docker 組合專案檔案 （dcproj） 中相對路徑。|-|
|DockerCompose 基礎檔路徑|直流普羅伊|指定 Docker-compose 檔的檔案名的第一部分，而不指定 *.yml*副檔名。 例如： <br>1. DockerComposeBaseFilePath = null/未定義：使用基本檔路徑*Docker-compose，* 檔將命名為*docker-compose.yml*和*docker-compose.override.yml*<br>2. DockerComposeBaseFilePath =*我的dockercompose：* 檔將命名為*mydockercompose.yml*和*mydockercompose.override.yml*<br> 3. DockerComposeBase檔路徑 = *..\mydockercompose*： 檔將向上一級。 |碼頭組成|
|DockerCompose 構建參數|直流普羅伊|指定要傳遞給`docker-compose build`命令的額外參數。 例如， `--parallel --pull` |
|DockerCompose 向下參數|直流普羅伊|指定要傳遞給`docker-compose down`命令的額外參數。 例如， `--timeout 500`|-|  
|DockerCompose 專案路徑|csproj 或 vbproj|Docker 組合專案 （dcproj） 檔的相對路徑。 在發佈服務專案時設置此屬性以查找存儲在 docker-compose.yml 檔中的關聯映射生成設置。|-|
|DockerComposeUp 參數|直流普羅伊|指定要傳遞給`docker-compose up`命令的額外參數。 例如， `--timeout 500`|-|
|碼頭開發模式|直流普羅伊| 控制是否啟用了"主機上的構建"優化（"快速模式"調試）。  允許的值是**快速**和**常規**的 。 | 快速 |
|DockerLaunchAction| 直流普羅伊 | 指定要在 F5 或 Ctrl+F5 上執行的啟動操作。  允許的值為"無"、啟動瀏覽器和啟動WCF測試用戶端|None|
|Docker啟動瀏覽器| 直流普羅伊 | 指示是否啟動瀏覽器。 如果指定了 DockerLaunchAction，則忽略該操作。 | False |
|Docker服務名稱| 直流普羅伊|如果指定了 DockerLaunchAction 或 DockerLaunchBrowser，則 DockerServiceName 是應啟動的服務的名稱。  使用此屬性可確定將啟動 Docker 組合檔可能引用的許多專案中的哪些專案。|-|
|DockerServiceUrl| 直流普羅伊 | 啟動瀏覽器時使用的 URL。  有效的替換權杖是"[服務 IPAddress]"、"[服務埠]"和"{Scheme}"。  例如： [Scheme]：//[服務 IP位址]：[服務埠]|-|
|DockerTargetOS| 直流普羅伊 | 構建 Docker 映射時使用的目標作業系統。|-|

## <a name="example"></a>範例

如果通過設置`DockerComposeBaseFilePath`到相對路徑來更改 Docker 撰寫檔的位置，則還需要確保更改生成上下文，以便它引用解決方案資料夾。 例如，如果 Docker 撰寫檔是名為*DockerComposeFiles 的*資料夾，則 Docker 撰寫檔應將生成上下文設置為".."或"./.."，具體取決於它與解決方案資料夾相關的位置。

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

*mydockercompose.yml*檔應如下所示，生成上下文設置為解決方案資料夾的相對路徑（在本例中為`..`）。

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
> DockerComposeBuild 參數、DockerComposeDown 參數和 DockerComposeUp 參數在 Visual Studio 2019 版本 16.3 中是新的。

## <a name="docker-compose-file-labels"></a>Docker 撰寫檔標籤

您還可以通過將名為*docker-compose.vs.debug.yml（* 用於**調試**配置）或*docker-compose.vs.is.is.yml（* 用於**發佈**配置）的檔放在與*docker-compose.yml*檔相同的目錄中來覆蓋某些設置。  在此檔中，您可以按照如下方式指定設置：

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

在值周圍使用雙引號，如前面的示例所示，並使用反斜線作為路徑中反斜線的逸出字元。

|標籤名稱|描述|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.參數|開始調試時傳遞給程式的參數。 對於 .NET Core 應用，這些參數通常是 NuGet 包的其他搜索路徑，然後是專案輸出程式集的路徑。|
|com.microsoft.visualstudio.debuggee.killprogram|此命令用於停止在容器內運行的偵錯工具（如有必要）。|
|com.microsoft.visualstudio.debuggee.程式|開始調試時啟動的程式。 對於 .NET 核心應用，此設置通常是**點網**。|
|com.microsoft.visualstudio.debuggee.工作目錄|開始調試時用作起始目錄的目錄。 此設置通常是 Linux 容器的 */app，* 或 Windows 容器的*C：\app。*|

## <a name="customize-the-app-startup-process"></a>自訂應用啟動過程

在使用`entrypoint`該設置啟動應用並使之依賴于配置之前，可以運行命令或自訂腳本。 例如，如果只需在**調試**模式下通過運行`update-ca-certificates`來設置證書，而不需要在**發佈**模式下設置證書，則只能在*docker-compose.vs.debug.yml*中添加以下代碼：

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

如果省略*docker-compose.vs.release.yml*或*docker-compose.vs.s.debug.yml，* 則 Visual Studio 會根據預設設置生成一個。

## <a name="next-steps"></a>後續步驟

有關 MSBuild 屬性的資訊，請參閱[MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="see-also"></a>另請參閱

[容器工具生成屬性](container-msbuild-properties.md)

[容器工具啟動設置](container-launch-settings.md)

[MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
