---
title: -Build (devenv.exe)
description: 瞭解組建 devenv 命令列參數，以及如何使用它來建立具有指定之方案設定檔的方案或專案。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32e7f14647729f167b4dc816519d398a00467547
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836433"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

使用指定的方案組態檔來建置方案或專案。

## <a name="syntax"></a>語法

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>引數

- *SolutionName*

  必要。 方案檔的完整路徑和名稱。

- *SolnConfigName*

  選擇性。 用來建置 *SolutionName* 中所指定方案的方案組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果未指定這個引數或其為空字串 (`""`)，則工具會使用方案的作用中組態。

- `/Project` *專案名稱*

  選擇性。 方案中專案檔的路徑和名稱。 您可以輸入從 *SolutionName* 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。

- `/ProjectConfig` *ProjConfigName*

  選擇性。 在建置指定的專案時要使用的專案組建組態名稱 (例如 `Debug` 或 `Release`)。 如果有多個方案平台可供使用，您也必須指定平台 (例如 `Debug|Win32`)。 如果指定這個參數，則會覆寫 *SolnConfigName* 引數。

- `/Out`*OutputFilename*

  選擇性。 您要將工具的輸出傳送到其中的檔案名稱。 如果檔案已經存在，工具就會將輸出附加至檔案結尾。

## <a name="remarks"></a>備註

- `/Build` 參數會執行與整合式開發環境內之 [建置方案] 功能表命令相同的函式。

- 請以雙引號括住包含空格的字串。

- 建置的摘要資訊 (包括錯誤) 可顯示在命令視窗中，或使用 `/Out` 參數指定的任何記錄檔中。

- `/Build` 參數只會建置自上次建置後已變更的專案。 若要建置方案中所有的專案，請改為使用 [/rebuild](../../ide/reference/rebuild-devenv-exe.md)。

- 如果您收到錯誤訊息，指出 **專案組態無效**，請確定您已指定方案平台或專案平台 (例如 `Debug|Win32`)。

## <a name="example"></a>範例

下列命令會使用 `MySolution` 內的 `Debug` 專案組建組態來建置專案 `CSharpWinApp`。

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>另請參閱

- [建置與清除專案和方案](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild ( # A0) ](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean ( # A0) ](../../ide/reference/clean-devenv-exe.md)
- [/Out ( # A0) ](../../ide/reference/out-devenv-exe.md)
