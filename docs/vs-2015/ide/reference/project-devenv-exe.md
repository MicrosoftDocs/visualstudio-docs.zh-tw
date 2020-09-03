---
title: -Project (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9c54691ed343493ef1e43798faf4d2ab6f60fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662115"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

識別所指定方案組態內要建置、清除、重建或部署的單一專案。

## <a name="syntax"></a>語法

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>引數
 /build 會建立所指定的專案 `/project` `ProjName` 。

 /clean 會清除組建期間建立的所有媒介檔案和輸出目錄。

 /rebuild 會清除，然後建立所指定的專案 `/project` `ProjName` 。

 /deploy 指定在組建或重建之後部署專案。

 需要 `SolnConfigName`。 將套用至 `SolutionName` 中所指定方案的方案組態名稱。

 需要 `SolutionName`。 方案檔的完整路徑和名稱。

 /project `ProjName` 選擇項。 方案中專案檔的路徑和名稱。 您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。

 /projectconfig `ProjConfigName` 選擇項。 要套用至所指定 `/project` 的專案組建組態名稱。

## <a name="remarks"></a>備註

- 必須是 `devenv /build`、/`clean`、`/rebuild` 或 `/deploy` 命令的已使用部分。

- 請以雙引號括住包含空格的字串。

- 組建的摘要資訊 (包括錯誤) 可顯示在 [命令]**** 視窗中，或使用 `/out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例
 此範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案組建組態，來建置專案 `CSharpConsoleApp`。

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>另請參閱
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md) [/ProjectConfig ( # A0) ](../../ide/reference/projectconfig-devenv-exe.md) [/Build ( # A1) ](../../ide/reference/build-devenv-exe.md) [/Clean ( # A2) ](../../ide/reference/clean-devenv-exe.md) [/Rebuild ( # A3) ](../../ide/reference/rebuild-devenv-exe.md) [/Deploy ( # A4) ](../../ide/reference/deploy-devenv-exe.md) [/out ( # A5) ](../../ide/reference/out-devenv-exe.md)
