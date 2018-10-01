---
title: -Project (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ffef1cdcc0b192e2e950e02b28dff2682936d87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497265"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[-專案 (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/project-devenv-exe)。  
  
  
識別所指定方案組態內要建置、清除、重建或部署的單一專案。  
  
## <a name="syntax"></a>語法  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
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
  
-   必須是 `devenv /build`、/`clean`、`/rebuild` 或 `/deploy` 命令的已使用部分。  
  
-   請以雙引號括住包含空格的字串。  
  
-   組建的摘要資訊 (包括錯誤) 可顯示在 [命令] 視窗中，或使用 `/out` 參數指定的任何記錄檔中。  
  
## <a name="example"></a>範例  
 此範例使用 `MySolution` 的 `Debug` 方案組態中的 `Debug` 專案組建組態，來建置專案 `CSharpConsoleApp`。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>另請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



