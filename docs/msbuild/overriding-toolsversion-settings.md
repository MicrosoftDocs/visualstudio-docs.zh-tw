---
title: 覆寫 ToolsVersion 設定 | Microsoft Docs
description: 瞭解您可以針對專案和方案變更或覆寫 MSBuild 工具組值的數種方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 855a07ab21d0396fea4605e5117e312608cb625e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918894"
---
# <a name="override-toolsversion-settings"></a>覆寫 ToolsVersion 設定

您可以使用三種方式中的其中一種來變更專案和方案的工具組︰

1. 從命令列建置專案或方案時，請使用 `-ToolsVersion` 參數 (或簡寫 `-tv`)。

2. 在 MSBuild 工作上設定 `ToolsVersion` 參數。

3. 在方案的專案上設定 `$(ProjectToolsVersion)` 屬性。 這可讓您使用與其他專案不同的工具組版本，以在方案中建置專案。

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>覆寫命令列組建上專案和方案的 ToolsVersion 設定

 雖然一般會使用專案檔中所指定的 ToolsVersion 來建置 Visual Studio 專案，但是您可以在命令列上使用 `-ToolsVersion` (或 `-tv`) 切換參數來覆寫該值，並使用不同的工具組來建置所有專案和其專案間相依性。 例如：

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 在此範例中，使用 ToolsVersion 12.0 建置所有專案  (不過，請參閱本主題稍後的「 [優先順序](#order-of-precedence) 」一節。 ) 

 在命令列上使用 `-tv` 切換參數時，您可以選擇性地在個別專案中使用 `$(ProjectToolsVersion)` 屬性，以使用與方案中其他專案不同的 ToolsVersion 值來建置它們。

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>使用 MSBuild 工作的 ToolsVersion 參數覆寫 ToolsVersion 設定

 MSBuild 工作是讓某個專案建置另一個專案的主要方式。 為了讓 MSBuild 工作使用與專案中所指定的不同 ToolsVersion 來建置專案，它會提供名為 `ToolsVersion` 的選擇性工作參數。 下列範例示範如何使用這個參數：

1. 建立一個名為 *projectA.proj* 並包含下列程式碼的檔案：

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    ToolsVersion="12.0">

        <Target Name="go" >
            <Message Text="projectA.proj" />
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />

            <MSBuild Projects="projectB.proj"
                ToolsVersion="2.0"
                Targets="go" />
        </Target>
    </Project>
    ```

2. 建立另一個名為 *projectB.proj* 並包含下列程式碼的檔案：

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    ToolsVersion="12.0">

        <Target Name="go">
            <Message Text="projectB.proj" />
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />
        </Target>
    </Project>
    ```

3. 在命令提示字元中，輸入下列命令：

    ```cmd
    msbuild projectA.proj -t:go -toolsversion:3.5
    ```

4. 即會出現下列輸出。 針對 `projectA`，命令列上的 `-toolsversion:3.5` 設定會覆寫 `Project` 標記中的 `ToolsVersion=12.0` 設定。

     `projectA` 中的工作會呼叫 `ProjectB`。 這項工作具有 `ToolsVersion=2.0`，可覆寫 `projectB` 的其他 `ToolsVersion` 設定。

    ```
    Output:
      projectA.proj
      MSBuildToolsVersion: 3.5
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5

      projectB.proj
      MSBuildToolsVersion: 2.0
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727
    ```

## <a name="order-of-precedence"></a>優先順序

 用來判斷 `ToolsVersion` 的優先順序從最高到最低為：

1. MSBuild 工作上用來建置專案的 `ToolsVersion` 屬性 (如果有的話)。

2. msbuild.exe 命令中使用的 `-toolsversion` (或 `-tv`) 切換參數 (如果有的話)。

3. 如果設定環境變數 `MSBUILDTREATALLTOOLSVERSIONSASCURRENT`，則會使用目前的 `ToolsVersion`。

4. 如果設定環境變數 `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT`，而且專案檔中所定義的 `ToolsVersion` 大於目前的 `ToolsVersion`，則請使用目前的 `ToolsVersion`。

5. 如果設定環境變數 `MSBUILDLEGACYDEFAULTTOOLSVERSION`，或未設定 `ToolsVersion`，則會使用下列步驟︰

    1. 專案檔中 [Project](../msbuild/project-element-msbuild.md) 項目的 `ToolsVersion` 屬性。 如果這個屬性不存在，則會假設為最新版本。

    2. *MSBuild.exe.config* 檔案中的預設工具版本。

    3. 登錄中的預設工具版本。 如需詳細資訊，請參閱 [標準和自訂工具](../msbuild/standard-and-custom-toolset-configurations.md)組設定。

6. 如果未設定環境變數 `MSBUILDLEGACYDEFAULTTOOLSVERSION`，則會使用下列步驟︰

    1. 如果環境變數 `MSBUILDDEFAULTTOOLSVERSION` 設定為現有的 `ToolsVersion`，請使用它。

    2. 如果在 *MSBuild.exe.config* 中設定 `DefaultOverrideToolsVersion`，請使用它。

    3. 如果在登錄中設定 `DefaultOverrideToolsVersion`，請使用它。

    4. 否則，請使用目前的 `ToolsVersion`。

## <a name="see-also"></a>另請參閱

- [多目標](../msbuild/msbuild-multitargeting-overview.md)
- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [標準和自訂工具組設定](../msbuild/standard-and-custom-toolset-configurations.md)
