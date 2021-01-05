---
title: Visual Studio 容器工具組建屬性
author: ghogen
description: 瞭解如何編輯容器工具組建屬性，以自訂 Visual Studio 組建和執行容器專案的方式。
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 4e8675bd0ea12b30ce678ce454bcedee457ddacd
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846730"
---
# <a name="container-tools-build-properties"></a>容器工具組建屬性

您可以設定 MSBuild 用來建立專案的屬性，以自訂 Visual Studio 建立容器專案的方式。 例如，您可以變更 Dockerfile 的名稱、指定影像的標籤和標籤、提供傳遞給 Docker 命令的額外引數，以及控制 Visual Studio 是否進行某些效能優化，例如在容器環境之外建立。 您也可以設定偵錯工具屬性，例如要啟動的可執行檔名稱，以及要提供的命令列引數。

若要設定屬性的值，請編輯專案檔。 例如，假設您的 Dockerfile 名為 *MyDockerfile*。 您可以在專案檔中設定屬性，如下所示 `DockerfileFile` 。

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

您可以將屬性設定加入至現有的專案 `PropertyGroup` ，如果沒有，則建立新的 `PropertyGroup` 元素。

下表顯示適用于容器專案的 MSBuild 屬性。 NuGet 套件版本會套用至 [VisualStudio](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/)的版本。

| 屬性名稱 | 描述 | 預設值  | NuGet 套件版本|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | 控制是否啟用「內部主機」優化 ( 「快速模式」的偵錯工具) 。  允許的值為 **Fast** 和 **Regular**。 | 快速 |1.0.1872750 或更新版本|
| ContainerVsDbgPath | VSDBG 偵錯工具的路徑。 | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 或更新版本|
| DockerDebuggeeArguments | 進行偵錯工具時，會指示偵錯工具將這些引數傳遞至已啟動的可執行檔。 | 不適用於 ASP.NET .NET Framework 專案 |1.7.8 或更新版本|
| DockerDebuggeeProgram | 進行偵錯工具時，會指示偵錯工具啟動這個可執行檔。 | 針對 .NET Core 專案： dotnet、ASP.NET .NET Framework projects：不適用 (IIS 一律會使用)  |1.7.8 或更新版本|
| DockerDebuggeeKillProgram | 此命令可用來終止容器中的執行中進程。 | 不適用於 ASP.NET .NET Framework 專案 |1.7.8 或更新版本|
| DockerDebuggeeWorkingDirectory | 進行偵錯工具時，會指示偵錯工具使用此路徑做為工作目錄。 | C:\app (Windows) 或/app (Linux)  |1.7.8 或更新版本|
| DockerDefaultTargetOS | 建立 Docker 映射時所使用的預設目標作業系統。 | 依 Visual Studio 設定。 |1.0.1985401 或更新版本|
| DockerImageLabels | 套用至 Docker 映射的預設標籤集合。 | MSBuildProjectName 的建立方式 = visual studio、.com-studio. 專案名稱 = $ ()  |1.5.4 或更新版本|
| DockerFastModeProjectMountDirectory|在 **快速模式** 中，此屬性會控制專案輸出目錄在執行中容器中的磁片區載入位置。|C:\app (Windows) 或/app (Linux) |1.9.2 或更新版本|
| DockerfileBuildArguments | 傳遞至 [Docker build](https://docs.docker.com/engine/reference/commandline/build/) 命令的其他引數。 | 不適用。 |1.0.1872750 或更新版本|
| DockerfileCoNtext | 建立 Docker 映射時所使用的預設內容，做為相對於 Dockerfile 的路徑。 | 依 Visual Studio 設定。 |1.0.1872750 或更新版本|
| DockerfileFastModeStage | Dockerfile 階段 (也就是在「偵錯工具」模式中建立映射時，要使用的目標) 。 | 在 Dockerfile (基底) 中找到的第一個階段 |
| DockerfileFile | 描述將用來建立/執行專案容器的預設 Dockerfile。 這也可以是路徑。 | Dockerfile |1.0.1872750 或更新版本|
| DockerfileRunArguments | 傳遞至 [Docker run](https://docs.docker.com/engine/reference/commandline/run/) 命令的其他引數。 | 不適用。 |1.0.1872750 或更新版本|
| DockerfileRunEnvironmentFiles | 在 Docker 執行期間套用的環境檔案清單（以分號分隔）。 | 不適用。 |1.0.1872750 或更新版本|
| DockerfileTag | 建立 Docker 映射時將使用的標記。 在偵錯工具中，會將 ":d ev" 附加至標記。 | 使用下列規則來移除非英數位元之後的元件名稱： <br/> 如果結果標記全部都是數位，則會將 "image" 插入為首碼 (例如，image2314)  <br/> 如果結果標記為空字串，則會使用 "image" 作為標記。 |1.0.1872750 或更新版本|

## <a name="example"></a>範例

下列專案檔會顯示其中部分設定的範例。

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>後續步驟

如需 MSBuild 屬性的一般資訊，請參閱 [Msbuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="see-also"></a>請參閱

[Docker Compose 組建屬性](docker-compose-properties.md)

[容器工具啟動設定](container-launch-settings.md)

[MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
