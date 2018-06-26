---
title: DevEnv Build 參數
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 777347ba36cf3443a509d1d6c8c44c23a86901e0
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764965"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

使用指定的方案組態檔建置方案。

## <a name="syntax"></a>語法

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>引數

|||
|-|-|
|*SolutionName*|必要。 方案檔的完整路徑和名稱。|
|*SolnConfigName*|必要。 將用來建置 *SolutionName* 中所指定之方案的方案組態名稱。 如果有多個方案平台，您也必須指定平台，例如 **"Debug\|Win32"**。|
|/project *ProjName*|選擇性。 方案中專案檔的路徑和名稱。 您可以輸入從 *SolutionName* 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。|
|/projectconfig *ProjConfigName*|選擇性。 建置具名專案時所要使用的專案組建組態名稱。 如果有多個專案平台，您也必須指定平台，例如 **"Debug\|Win32"**。|

## <a name="remarks"></a>備註

- 此 **/build** 參數會執行與整合式開發環境 (IDE) 內之 [建置方案] 功能表命令相同的功能。

- 請以雙引號括住包含空格的字串。

- 組建的摘要資訊 (包括錯誤) 可顯示在命令視窗中，或使用 **/out** 參數指定的任何記錄檔中。

- **/build** 參數只會建置自上次建置後已變更的專案。 若要建置方案中所有的專案，請改為使用 [/rebuild](../../ide/reference/rebuild-devenv-exe.md)。

- 如果您收到錯誤訊息，指出**專案組態無效**，請確定您已指定方案平台或專案平台，例如 **"Debug\|Win32"**。

## <a name="example"></a>範例

下列命令會在 "MySolution" 的 "Debug" 方案組態內使用 "Debug" 專案組建組態來建置專案 "CSharpConsoleApp"。

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>另請參閱

- [建置與清除專案和方案](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)