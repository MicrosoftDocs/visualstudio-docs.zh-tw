---
title: -Build (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 419716d750771908a43318d051cb0b4681d35149
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660989"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用指定的方案組態檔建置方案。

## <a name="syntax"></a>語法

```
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>引數
 需要 `SolutionName`。 方案檔的完整路徑和名稱。

 需要 `SolnConfigName`。 將用來建置在 `SolutionName` 中命名之方案的方案組態名稱。

 /project `ProjName` 選擇項。 方案中專案檔的路徑和名稱。 您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。

 /projectconfig `ProjConfigName` 選擇項。 建置具名 `/project` 時所要使用的專案組建組態名稱。

## <a name="remarks"></a>備註
 此參數會執行與整合式開發環境內之 [建置方案]**** 功能表命令相同的功能。

 請以雙引號括住包含空格的字串。

 組建的摘要資訊 (包括錯誤) 可顯示在 [命令]**** 視窗中，或使用 `/out` 參數指定的任何記錄檔中。

 此命令只會建置自上次建置後已變更的專案。 若要建置方案中所有的專案，請使用 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)。

## <a name="example"></a>範例
 此範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案組建組態，來建置專案 `CSharpConsoleApp`。

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>另請參閱
 在 Visual Studio [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)[中建立和清除專案和方案](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [/Rebuild ( # A0) ](../../ide/reference/rebuild-devenv-exe.md) [/Clean ( # A1) ](../../ide/reference/clean-devenv-exe.md) [/out ( # A2) ](../../ide/reference/out-devenv-exe.md)
