---
title: -ProjectConfig (devenv.exe)
description: 瞭解如何使用 ProjectConfig devenv 命令列參數來指定建立、清除、重建或部署專案時要套用的專案組建設定。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba1f6f0de7e7b716853ec58aa27a34fe11010da4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969590"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

指定要在建置、清除、重建或部署 `/Project` 引數中所指定的專案時套用的專案建置組態。

## <a name="syntax"></a>語法

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>引數

- *SolutionName*

  必要。 方案檔的完整路徑和名稱。

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  必要。 [建置](build-devenv-exe.md)、[清除](clean-devenv-exe.md)、[部署](deploy-devenv-exe.md)或[重建](rebuild-devenv-exe.md)專案。

- *SolnConfigName*

  選擇性。 要套用至 *SolutionName* 中所指定方案的方案組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果未指定這個引數或其為空字串 (`""`)，則工具會使用方案的作用中組態。

- `/Project` *專案名稱*

  選擇性。 方案中專案檔的路徑和名稱。 您可以輸入專案的顯示名稱或從 *SolutionName* 資料夾到專案檔的相對路徑。 您也可以輸入專案檔的完整路徑和名稱。

- `/ProjectConfig` *ProjConfigName*

  選擇性。 要套用至所指定 `/Project` 的專案組建組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。

- `/Out`*OutputFilename*

  選擇性。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

`/ProjectConfig` 參數必須與 `/Project` 參數搭配使用，以作為 `/Build`、/`Clean`、`/Deploy` 或 `/Rebuild` 命令的一部分。

請以雙引號括住包含空格的字串。

建置的摘要資訊 (包括錯誤) 可顯示在命令視窗中，或使用 `/Out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例

下列命令會使用 `MySolution` 內的 `Debug` 專案組建組態來建置專案 `CSharpWinApp`：

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Project ( # A0) ](../../ide/reference/project-devenv-exe.md)
- [/Build ( # A0) ](../../ide/reference/build-devenv-exe.md)
- [/Clean ( # A0) ](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild ( # A0) ](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy ( # A0) ](../../ide/reference/deploy-devenv-exe.md)
- [/Out ( # A0) ](../../ide/reference/out-devenv-exe.md)
