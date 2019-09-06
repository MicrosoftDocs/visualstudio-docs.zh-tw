---
title: 對容器化應用程式進行單元測試
author: ghogen
description: 在 Visual Studio 中使用 Docker 專案的每個組建執行單元測試
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "70312035"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>HOW TO：執行容器化應用程式的單元測試

您可以藉由修改 Dockerfile，對容器化專案的每個組建執行單元測試。

## <a name="prerequisites"></a>必要條件

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- 安裝[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- 單元測試設定為使用[dotnet test](/dotnet/core/tools/dotnet-test)執行
- 安裝[容器視窗延伸](https://aka.ms/vscontainerspreview)模組

## <a name="add-unit-tests-to-the-dockerfile"></a>將單元測試新增至 Dockerfile

Visual Studio 在修改 Dockerfile 之前，會先執行一些特殊的效能優化。 建立**調試**設定時，Visual Studio 會在本機電腦上建立專案，並將結果複製到容器。 因此，只有多階段 Dockerfile 的第一個階段會依照 Dockerfile 中的指定執行。 如需詳細資訊，請參閱[Visual Studio 的容器工具組建進程](container-build.md)。

若要將單元測試加入至多階段 Dockerfile，請`unit-test`在`build`和`publish`階段之間新增 Dockerfile 的階段。

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

Visual Studio 只會在 [**調試**設定] 中執行第一個`unit-test`階段，因此階段只會在**發行**設定中執行。 但即使在**發行**設定中，記錄結果也不會包含在最終映射中，因為最終映射是從`base`階段建立`unit-test` ，而不是從階段。 若要執行測試並產生可供您查看記錄的影像，請使用下列命令：

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>後續步驟

接著，您可以使用 [[容器] 視窗](view-and-diagnose-containers.md)（如果已安裝延伸模組）來查看測試記錄。  

若要查看您的測試記錄，請使用**Ctrl** + **Q**並搜尋**容器**以開啟 [**容器**] 視窗。 在 [**容器**] 視窗中，尋找**您的容器，開啟 [檔案**] 索引標籤，在容器的檔案系統中尋找您的測試結果（.trx）檔案，然後開啟它以在 Visual Studio 中查看結果。

