---
title: 視覺化工作室容器工具產生屬性
author: ghogen
description: 容器工具產生流程概述
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 3caa8a76f461515c0d2265590383861b6e10d0a1
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472662"
---
# <a name="container-tools-build-properties"></a>容器工具產生屬性

您可以通過設定 MSBuild 用於生成專案的屬性來自定義 Visual Studio 如何建構容器專案。 例如,您可以更改 Dockerfile 的名稱,為圖像指定標記和標籤,提供傳遞給 Docker 命令的其他參數,並控制 Visual Studio 是否執行某些性能優化,例如在容器環境之外生成。 還可以設置調試屬性,如要啟動的可執行檔的名稱和要提供的命令列參數。

要設置屬性的值,請編輯專案檔。 例如,假設您的 Dockerfile 名為*MyDockerfile。* 您可以在專案檔中設置`DockerfileFile`屬性,如下所示。

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

您可以將屬性設置添加到現有`PropertyGroup`元素,如果沒有,則創建`PropertyGroup`新 元素。

下表顯示了可用於容器專案的 MSBuild 屬性。 NuGet 套件版本適用於[微軟.VisualStudio.Azure.容器.Tools.Target](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| 屬性名稱 | 描述 | 預設值  | NuGet 套件版本|
|---------------|-------------|----------------|----------------------|
| 開放模式 | 控制是否啟用了「主機上的構建」優化(「快速模式」調試)。  允許的值是**快速**與**一般**的 。 | 快速 |1.0.1872750 或更新|
| 容器VDbgPath | VSDBG 除錯器的路徑。 | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 或更新|
| 多克除錯參數 | 除錯時,指示調試器將這些參數傳遞給啟動的可執行檔。 | 不適用於 ASP.NET .NET 框架專案 |1.7.8 或更新|
| DockerDebuggee計劃 | 除錯時,除錯器將指示啟動此可執行檔。 | 對於 .NET 核心專案:dotnet,ASP.NET .NET 框架專案:不適用(始終使用 IIS) |1.7.8 或更新|
| 多克調試基基基爾計劃 | 此命令用於終止容器中的正在運行的進程。 | 不適用於 ASP.NET .NET 框架專案 |1.7.8 或更新|
| 多克除錯工作目錄 | 調試時,調試器將指示使用此路徑作為工作目錄。 | C:\應用程式(視窗)或/應用程式(Linux) |1.7.8 或更新|
| DockerDefaultTargetOS | 產生 Docker 映像時使用的預設目標作業系統。 | 由視覺工作室設置。 |1.0.1985401 或更新|
| DockerImage 標籤 | 套用於 Docker 映像的預設分頁集。 | com.microsoft.創建-由視覺工作室;com.microsoft.visual-studio.專案名稱=$(MSBuildProject名稱) |1.5.4 或更新|
| DockerFastMode 專案安裝目錄|在**快速模式下**,此屬性控制項目輸出目錄在正在運行的容器中安裝的卷的位置。|C:\應用程式(視窗)或/應用程式(Linux)|1.9.2 或更新|
| Dockerfile 建構參數 | 傳遞給 Docker 產生命令的其他參數。 | 不適用。 |1.0.1872750 或更新|
| Dockerfile 內容 | 構建 Docker 映像時使用的預設上下文,作為相對於 Dockerfile 的路徑。 | 由視覺工作室設置。 |1.0.1872750 或更新|
| DockerfileFastModeStage | 在除錯模式下建構映像時要使用的 Dockerfile 階段(即目標)。 | Dockerfile(基)中找到的第一階段 |
| Dockerfile | 描述將用於生成/執行專案的容器的預設 Dockerfile。 這也可以是一條路徑。 | Dockerfile |1.0.1872750 或更新|
| Dockerfile Run 參數 | 傳遞給 Docker 執行命令的其他參數。 | 不適用。 |1.0.1872750 或更新|
| DockerfileRun 環境檔案 | 在 Docker 執行期間應用的環境檔的分號分隔清單。 | 不適用。 |1.0.1872750 或更新|
| DockerfileTag | 生成 Docker 映像時將使用的標記。 在調試中,標記中附加了":dev"。 | 使用以下規則剝離非字母數字字元後,程式集名稱: <br/> 如果產生的標記都是數位的,則「圖像」將作為前綴插入(例如,image2314) <br/> 如果產生的標記是空字串,則使用"圖像"作為標記。 |1.0.1872750 或更新|

## <a name="next-steps"></a>後續步驟

有關 MSBuild 屬性的資訊,請參閱[MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="see-also"></a>另請參閱

[Docker 組合產生屬性](docker-compose-properties.md)

[容器工具啟動設定](container-launch-settings.md)

[MSBuild 保留和已知屬性](../msbuild/msbuild-reserved-and-well-known-properties.md)
