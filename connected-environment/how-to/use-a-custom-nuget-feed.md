---
title: 如何在連線環境中使用自訂的 NuGet 摘要 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在連線環境中使用自訂的 NuGet 摘要，以存取和使用 NuGet 套件。
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 71fcf1c3cfb37d783de13514f6a048c3b3711a53
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031217"
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>在連線環境中使用自訂的 NuGet 摘要。

NuGet 摘要可讓您以便利的方式將套件來源併入專案。 連線環境必須能夠存取這個摘要，才能將相依性正確安裝至 Docker 容器中。

若要設定 NuGet 摘要：
1. 將[套件參考](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files)新增至 `PackageReference` 節點下的 `*.csproj` 檔案中。

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. 在專案資料夾中建立 [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) 檔案。
     * 使用 `packageSources` 區段來參考您的 NuGet 摘要位置。 重要事項：NuGet 摘要必須可以公開存取。
     * 使用 `packageSourceCredentials` 區段來設定使用者名稱和密碼認證。 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. 如果您是使用原始程式碼控制：
    - 請參考 `.gitignore` 檔案中的 `NuGet.Config`，以免不小心認可來源存放庫的認證。
    - 開啟專案中的 `vsce.yaml` 檔案，並找出 `build` 區段，然後插入下列程式碼片段，確保 `NuGet.Config` 檔案會同步至 Azure，以便在容器映像建置程序期間使用該檔案  (連線環境預設不會同步處理符合 `.gitignore` 和 `.dockerignore` 規則的檔案)。

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>後續步驟

完成上述步驟後，在下一次執行 `vsce up` (或在 VSCode 或 Visual Studio 中點擊 `F5`) 時，連線環境即會將 `NuGet.Config` 檔案同步至 Azure，以便系統使用 `dotnet restore` 將套件相依性安裝到容器中。

