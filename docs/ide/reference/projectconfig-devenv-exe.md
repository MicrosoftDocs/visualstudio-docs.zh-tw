---
title: -ProjectConfig (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fda8ce7103f069dc9cbc22f7c922e6f358fe72b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
指定要在建置、清除、重建或部署 `/project` 引數中所指定的專案時套用的專案建置組態。

## <a name="syntax"></a>語法

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>引數
 /build

 建置 `/project` `ProjName` 所指定的專案。

 /clean

 清除在建置期間建立的所有中繼檔案和輸出目錄。

 /rebuild

 清除後建置 `/project` `ProjName` 所指定的專案。

 /deploy

 指定在建置或重建之後部署專案。

 `SolnConfigName`

 必要。 將套用至 `SolutionName` 中所指定方案的方案組態名稱。

 `SolutionName`

 必要。 方案檔的完整路徑和名稱。

 /project `ProjName`

 選擇性。 方案中專案檔的路徑和名稱。 您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。

 /projectconfig `ProjConfigName`

 選擇性。 要套用至所指定 `/project` 的專案組建組態名稱。

## <a name="remarks"></a>備註

-   必須與 `/project` 參數搭配使用，作為 `devenv /build`、/`clean`、`/rebuild` 或 `/deploy` 命令的一部分。

-   請以雙引號括住包含空格的字串。

-   組建的摘要資訊 (包括錯誤) 可顯示在 [命令] 視窗中，或使用 `/out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例
 此範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案組建組態，來建置專案 `CSharpConsoleApp`。

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)