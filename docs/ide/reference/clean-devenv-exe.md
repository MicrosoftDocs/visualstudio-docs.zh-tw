---
title: -Clean (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc621aaa8bac5fa191efd9602a47977d29fa1da2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
清除所有中繼檔案和輸出目錄。

## <a name="syntax"></a>語法

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>引數
 `FileName`

 必要。 方案檔或專案檔的完整路徑和名稱。

 /project `ProjName`

 選擇性。 方案中專案檔的路徑和名稱。 您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。

 /projectconfig `ProjConfigName`

 選擇性。 要在清除具名 `/project` 時使用的專案組建組態名稱。

## <a name="remarks"></a>備註
 此參數會執行與整合式開發環境 (IDE) 內之 [清除方案] 功能表命令相同的功能。

 請以雙引號括住包含空格的字串。

 清除和組建的摘要資訊 (包含錯誤) 可以顯示在 [命令] 視窗中，或使用 `/out` 參數指定的任何記錄檔中。

## <a name="example"></a>範例
 第一個範例會使用方案檔中指定的預設組態來清除 `MySolution` 方案。

 第二個範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案組建組態，來清除專案 `CSharpConsoleApp`。

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)