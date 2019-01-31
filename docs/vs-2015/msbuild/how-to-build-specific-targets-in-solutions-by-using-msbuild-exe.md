---
title: HOW TO：使用 MSBuild.exe 在方案中建置特定目標 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e1670d5e67581ee61ec5517bedc4e8cfce1755
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766242"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>HOW TO：使用 MSBuild.exe 在方案中建置特定目標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您可以使用 MSBuild.exe，在方案中建置特定專案的特定目標。  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>在方案中建置特定專案的特定目標  
  
1.  在命令列中，輸入 `MSBuild.exe <SolutionName>.sln`，其中 `<SolutionName>` 會對應至包含您想要執行之目標的方案檔案名稱。  
  
2.  以 *ProjectName*:*TargetName* 格式，在 **/t** 參數之後指定目標。  
  
## <a name="example"></a>範例  
 下列範例會執行 `NotInSlnFolder` 專案的 `Rebuild` 目標，然後執行 `InSolutionFolder` 專案的 `Clean` 目標，其位於 `NewFolder` 方案資料夾中。  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>請參閱  
 [命令列參考](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [ MSBuild](msbuild.md)  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)
