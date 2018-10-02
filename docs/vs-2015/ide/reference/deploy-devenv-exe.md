---
title: -Deploy (devenv.exe) | Microsoft Docs
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
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4bed834524c159d42b2193857c805fab7628fe0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485877"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[-部署 (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/deploy-devenv-exe)。  
  
  
在建置或重建之後部署方案。 只適用於 受控碼專案。  
  
## <a name="syntax"></a>語法  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## <a name="arguments"></a>引數  
 `SolnConfigName`  
 必要。 將用來建置在 `SolutionName` 中命名之方案的方案組態名稱。  
  
 `SolutionName`  
 必要。 方案檔的完整路徑和名稱。  
  
 /project `ProjName`  
 選擇性。 方案中專案檔的路徑和名稱。 您可以輸入從 `SolutionName` 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。  
  
 /projectconfig `ProjConfigName`  
 選擇性。 建置具名 `/project` 時所要使用的專案組建組態名稱。  
  
## <a name="remarks"></a>備註  
 指定的專案必須是部署專案。 如果指定的專案不是部署專案，則將已建置的專案傳遞給部署時，它會失敗並發生錯誤。  
  
 請以雙引號括住包含空格的字串。  
  
 組建的摘要資訊 (包括錯誤) 可顯示在 [命令] 視窗中，或使用 `/out` 參數指定的任何記錄檔中。  
  
## <a name="example"></a>範例  
 此範例使用 `MySolution` 之 `Release` 方案組態內的 `Release` 專案組建組態，來部署 `CSharpConsoleApp` 專案。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## <a name="see-also"></a>另請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



