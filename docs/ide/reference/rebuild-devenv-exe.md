---
title: -Rebuild (devenv.exe)
description: 瞭解如何使用 Rebuild devenv 命令列參數來清除然後建立指定的方案設定。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8086e5ffb2ebdd154e95eda18e04ed5b64cd3dd2
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040039"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

清除然後建置指定的解決方案設定。

## <a name="syntax"></a>語法

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>引數

- *SolutionName*

  必要。 方案檔的完整路徑和名稱。

- *SolnConfigName*

  選擇性。 用來重建 *SolutionName* 中所指定方案的方案組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果未指定這個引數或其為空字串 (`""`)，則工具會使用方案的作用中組態。

- `/Project` *專案名稱*

  選擇性。 方案中專案檔的路徑和名稱。 您可以輸入專案的顯示名稱或從 *SolutionName* 資料夾到專案檔的相對路徑。 您也可以輸入專案檔的完整路徑和名稱。

- `/ProjectConfig` *ProjConfigName*

  選擇性。 重建指定的 `/Project` 時要使用的專案組建組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果指定這個參數，則會覆寫 *SolnConfigName* 引數。

- `/Out`*OutputFilename*

  選擇性。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

- 這個參數會執行與 IDE 中 [重建方案] 功能表命令相同的動作。

- 請以雙引號括住包含空格的字串。

- 清除和建置的摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 [/Out](out-devenv-exe.md) 參數指定的任何記錄檔中。

## <a name="example"></a>範例

此範例會使用 `MySolution` 內的 `Debug` 專案組建組態來清除和重建專案 `CSharpWinApp`。

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Build ( # A0) ](../../ide/reference/build-devenv-exe.md)
- [/Clean ( # A0) ](../../ide/reference/clean-devenv-exe.md)
- [/Out ( # A0) ](../../ide/reference/out-devenv-exe.md)
