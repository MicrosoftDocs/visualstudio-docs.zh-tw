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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58e48676cb8719cca5da1989342642669c6565cd
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54778480"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
使用指定的方案組態檔建置方案。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>引數  
 `SolutionName`  
 必要項。 方案檔的完整路徑和名稱。  
  
 `SolnConfigName`  
 必要項。 將用來建置在 `SolutionName` 中命名之方案的方案組態名稱。  
  
 /project `ProjName`  
 選擇性。 方案中專案檔的路徑和名稱。 您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。  
  
 /projectconfig `ProjConfigName`  
 選擇性。 建置具名 `/project` 時所要使用的專案組建組態名稱。  
  
## <a name="remarks"></a>備註  
 此參數會執行與整合式開發環境內之 [建置方案] 功能表命令相同的功能。  
  
 請以雙引號括住包含空格的字串。  
  
 組建的摘要資訊 (包括錯誤) 可顯示在 [命令] 視窗中，或使用 `/out` 參數指定的任何記錄檔中。  
  
 此命令只會建置自上次建置後已變更的專案。 若要建置方案中所有的專案，請使用 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)。  
  
## <a name="example"></a>範例  
 此範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案組建組態，來建置專案 `CSharpConsoleApp`。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中建置和清除專案與方案](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
