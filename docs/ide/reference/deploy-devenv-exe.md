---
title: -Deploy (devenv.exe)
description: 瞭解如何使用部署 devenv 命令列參數，在組建或重建之後部署方案。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23064842d89ffb1e7fb5e521afe80caea5ffae56
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040704"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

在建置或重建之後部署方案。 只適用於 受控碼專案。

## <a name="syntax"></a>語法

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>引數

- *SolutionName*

  必要。 方案檔的完整路徑和名稱。

- *SolnConfigName*

  選擇性。 用來建置 *SolutionName* 中所指定方案的方案組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果未指定這個引數或其為空字串 (`""`)，則工具會使用方案的作用中組態。

- `/Project` *專案名稱*

  選擇性。 方案中專案檔的路徑和名稱。 您可以輸入專案的顯示名稱或從 *SolutionName* 資料夾到專案檔的相對路徑。 您也可以輸入專案檔的完整路徑和名稱。

- `/ProjectConfig` *ProjConfigName*

  選擇性。 在建置指定的 `/Project` 時要使用的專案組建組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果指定這個參數，則會覆寫 *SolnConfigName* 引數。

- `/Out`*OutputFilename*

  選擇性。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

指定的專案必須是部署專案。 如果指定的專案不是部署專案，則在傳遞已建置的專案以進行部署時，它會失敗並發生錯誤。

請以雙引號括住包含空格的字串。

組建的摘要資訊（包括錯誤）可顯示在 **命令** 視窗中，或使用 [/out](out-devenv-exe.md) 參數指定的任何記錄檔中。

## <a name="example"></a>範例

此範例會使用 `MySolution` 內的 `Release` 專案組建組態來部署專案 `CSharpWinApp`。

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Project ( # A0) ](../../ide/reference/project-devenv-exe.md)
- [/Build ( # A0) ](../../ide/reference/build-devenv-exe.md)
- [/Clean ( # A0) ](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild ( # A0) ](../../ide/reference/rebuild-devenv-exe.md)
- [/Out ( # A0) ](../../ide/reference/out-devenv-exe.md)
