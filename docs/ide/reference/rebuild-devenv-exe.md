---
title: -Rebuild (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e462e64df90a7672efa890897b48726a0e764e6c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
清除然後建置指定的解決方案設定。

## <a name="syntax"></a>語法

```cmd
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>引數
 `SolnConfigName`

 必要。 將用來重建在 `SolutionName` 中命名之解決方案的解決方案設定名稱。

 `SolutionName`

 必要。 方案檔的完整路徑和名稱。

 /project `ProjName`

 選擇性。 方案中專案檔的路徑和名稱。 您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。

 /projectconfig `ProjConfigName`

 選擇性。 重建具名 `/project` 時所要使用的專案組建設定名稱。

## <a name="remarks"></a>備註

-   此參數會執行與整合式開發環境內之 [重建解決方案] 功能表命令相同的功能。

-   請以雙引號括住包含空格的字串。

-   清除和組建的摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 `/out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例
 此範例使用 `MySolution` 的 `Debug` 解決方案設定中的 `Debug` 專案組建設定，來清除和重建專案 `CSharpWinApp`。

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)