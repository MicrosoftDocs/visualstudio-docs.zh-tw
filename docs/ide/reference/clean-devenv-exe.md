---
title: -Clean (devenv.exe)
description: 瞭解如何使用 Clean devenv 命令列參數來清除所有的媒介檔案和輸出目錄。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6023df4e0f8721f18a82950c0ea507406fd48e02
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041045"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

清除所有中繼檔案和輸出目錄。

## <a name="syntax"></a>語法

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>引數

- *SolutionName*

  必要。 方案檔的完整路徑和名稱。

- *Config*

  選擇性。 針對 *SolutionName* 中指定的方案清除中繼檔的組態 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果未指定這個引數或其為空字串 (`""`)，則工具會使用方案的作用中組態。

- `/Project` *專案名稱*

  選擇性。 方案中專案檔的路徑和名稱。 您可以輸入專案的顯示名稱或從 *SolutionName* 資料夾到專案檔的相對路徑。 您也可以輸入專案檔的完整路徑和名稱。

- `/ProjectConfig` *ProjConfigName*

  選擇性。 清除指定的 `/Project` 時要使用的專案組建組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果指定這個參數，則會覆寫 *SolnConfigName* 引數。

- `/Out`*OutputFilename*

  選擇性。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

這個參數會執行與 IDE 中 [清除方案] 功能表命令相同的函式。

請以雙引號括住包含空格的字串。

清除和建置時的摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 [/Out](out-devenv-exe.md) 參數指定的任何記錄檔中。

如果未指定 `/Project` 參數，就會對方案中的所有專案完成清除動作，即使已將 *FileName* 指定為專案檔也一樣。

## <a name="example"></a>範例

第一個範例會使用方案檔中指定的預設組態來清除 `MySolution` 方案。

第二個範例會使用 `MySolution` 內的 `Debug` 專案組建組態來清除專案 `CSharpWinApp`。

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Build ( # A0) ](../../ide/reference/build-devenv-exe.md)
- [/Rebuild ( # A0) ](../../ide/reference/rebuild-devenv-exe.md)
- [/Out ( # A0) ](../../ide/reference/out-devenv-exe.md)
