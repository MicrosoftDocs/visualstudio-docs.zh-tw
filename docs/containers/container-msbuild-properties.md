---
title: Visual Studio 容器工具組建屬性
author: ghogen
description: 容器工具組建流程的總覽
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 427a70d9bc4f6ef326ffb16e7d26df9d8fae2365
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283199"
---
# <a name="container-tools-build-properties"></a>容器工具組建屬性

您可以藉由設定 MSBuild 用來建立專案的屬性，自訂 Visual Studio 建立容器專案的方式。 例如，您可以變更 Dockerfile 的名稱、指定影像的標記和標籤、提供傳遞至 Docker 命令的其他引數，以及控制 Visual Studio 是否執行特定效能優化，例如在容器環境外建立。 您也可以設定偵錯工具屬性，例如要啟動之可執行檔的名稱，以及要提供的命令列引數。

若要設定屬性的值，請編輯專案檔。 例如，假設您的 Dockerfile 名為*MyDockerfile*。 您可以 `DockerfileFile` 在專案檔中設定屬性，如下所示。

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

您可以將屬性設定加入至現有的專案 `PropertyGroup` ，如果沒有的話，請建立新的 `PropertyGroup` 元素。

下表顯示適用于容器專案的 MSBuild 屬性。 NuGet 套件版本適用于[VisualStudio. Azure 容器](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/)。

| 屬性名稱 | 描述 | 預設值  | NuGet 套件版本|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | 控制是否啟用「內部主機」優化（「快速模式」的調試功能）。  允許的值為**快速**和**一般**。 | 快速 |1.0.1872750 或更新版本|
| ContainerVsDbgPath | VSDBG 偵錯工具的路徑。 | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 或更新版本|
| DockerDebuggeeArguments | 在進行調試時，會指示偵錯工具將這些引數傳遞至已啟動的可執行檔。 | 不適用於 ASP.NET .NET Framework 專案 |1.7.8 或更新版本|
| DockerDebuggeeProgram | 在進行調試時，會指示偵錯工具啟動此可執行檔。 | 針對 .NET Core 專案： dotnet、ASP.NET .NET Framework 專案：不適用（一律會使用 IIS） |1.7.8 或更新版本|
| DockerDebuggeeKillProgram | 此命令可用來終止容器中的執行中進程。 | 不適用於 ASP.NET .NET Framework 專案 |1.7.8 或更新版本|
| DockerDebuggeeWorkingDirectory | 在進行調試時，會指示偵錯工具使用此路徑作為工作目錄。 | C:\app （Windows）或/app （Linux） |1.7.8 或更新版本|
| DockerDefaultTargetOS | 建立 Docker 映射時使用的預設目標作業系統。 | 由 Visual Studio 設定。 |1.0.1985401 或更新版本|
| DockerImageLabels | 適用于 Docker 映射的預設標籤集。 | .com： by = visual studio; .com. visual studio。專案名稱 = $ （MSBuildProjectName） |1.5.4 或更新版本|
| DockerFastModeProjectMountDirectory|在**快速模式**中，這個屬性會控制將專案輸出目錄裝載到執行中容器的位置。|C:\app （Windows）或/app （Linux）|1.9.2 或更新版本|
| DockerfileBuildArguments | 傳遞至[Docker build](https://docs.docker.com/engine/reference/commandline/build/)命令的其他引數。 | 不適用。 |1.0.1872750 或更新版本|
| DockerfileCoNtext | 建立 Docker 映射時使用的預設內容，做為相對於 Dockerfile 的路徑。 | 由 Visual Studio 設定。 |1.0.1872750 或更新版本|
| DockerfileFastModeStage | 在 [偵錯工具] 模式中建立映射時，所要使用的 Dockerfile 階段（也就是目標）。 | 在 Dockerfile 中找到的第一個階段（base） |
| DockerfileFile | 描述將用來建立/執行專案容器的預設 Dockerfile。 這也可以是路徑。 | Dockerfile |1.0.1872750 或更新版本|
| DockerfileRunArguments | 傳遞至[Docker run](https://docs.docker.com/engine/reference/commandline/run/)命令的額外引數。 | 不適用。 |1.0.1872750 或更新版本|
| DockerfileRunEnvironmentFiles | 在 Docker 執行期間套用的環境檔案清單（以分號分隔）。 | 不適用。 |1.0.1872750 或更新版本|
| DockerfileTag | 建立 Docker 映射時將使用的標記。 在調試中，會將 ":d ev" 附加至標記。 | 使用下列規則來去除非英數位元之後的元件名稱： <br/> 如果產生的標記全都是數值，則會插入 "image" 做為前置詞（例如，image2314） <br/> 如果產生的標記是空字串，則會使用 "image" 做為標記。 |1.0.1872750 或更新版本|

## <a name="example"></a>範例

下列專案檔會顯示其中一些設定的範例。

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

如需有關 MSBuild 屬性的一般資訊，請參閱[Msbuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="see-also"></a>另請參閱

[Docker Compose 組建屬性](docker-compose-properties.md)

[容器工具啟動設定](container-launch-settings.md)

[MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
