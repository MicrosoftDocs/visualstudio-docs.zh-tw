---
title: 如何：使用 MSBuild.exe 在方案中建置特定目標 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bdc5d824d802916c38ef0267dae0de85e8814e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484991"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>如何：使用 MSBuild.exe 在方案中建置特定目標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 在方案所使用 MSBuild.exe 建置特定目標](https://docs.microsoft.com/visualstudio/msbuild/how-to-build-specific-targets-in-solutions-by-using-msbuild-exe)。  
  
  
您可以使用 MSBuild.exe，在方案中建置特定專案的特定目標。  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>在方案中建置特定專案的特定目標  
  
1.  在命令列中，輸入 `MSBuild.exe <SolutionName>.sln`，其中 `<SolutionName>` 會對應至包含您想要執行之目標的方案檔案名稱。  
  
2.  以 *ProjectName*:*TargetName* 格式，在 **/t** 參數之後指定目標。  
  
## <a name="example"></a>範例  
 下列範例會執行 `NotInSlnFolder` 專案的 `Rebuild` 目標，然後執行 `InSolutionFolder` 專案的 `Clean` 目標，其位於 `NewFolder` 方案資料夾中。  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>另請參閱  
 [命令列參考](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [ MSBuild](msbuild.md)  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)


