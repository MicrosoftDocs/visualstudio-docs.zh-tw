---
title: 使用 MSBuild 同時建置多個專案 | Microsoft Docs
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
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23e92e9ae2814ccfc74ce641f110a34fd956d3bd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491110"
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>使用 MSBuild 同時建置多個專案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用 MSBuild 同時建置多個專案](https://docs.microsoft.com/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)。  
  
  
您可以使用 MSBuild 透過讓專案平行執行的方式，加快建置多個專案的速度。 若要平行執行組建，您可以使用多核心或多處理器電腦上的下列設定：  
  
-   命令提示字元中的 `/maxcpucount` 參數。  
  
-   MSBuild 工作上的 <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> 工作參數。  
  
> [!NOTE]
>  命令列中的 **/verbosity** (**/v**) 參數也會影響建置效能。 如果組建記錄檔資訊的詳細程度設為詳細或診斷 (用於疑難排解)，建置效能就可能會降低。 如需詳細資訊，請參閱[取得建置記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)和[命令列參考](../msbuild/msbuild-command-line-reference.md)。  
  
## <a name="maxcpucount-switch"></a>/maxcpucount 參數  
 如果您使用 `/maxcpucount` 參數 (簡寫為 `/m`)，MSBuild 就可建立可平行執行的指定 MSBuild.exe 處理序數目。 這些處理序也稱為「背景工作處理序」。 每個背景工作處理序會使用個別的核心或處理器 (如果有的話)，在其他可用處理器可能正在建置其他專案的同時建置專案。 例如，將此參數設為值 "4" 時，MSBuild 會建立四個背景工作處理序來建置專案。  
  
 如果您引入 `/maxcpucount` 參數但未指定值，MSBuild 會使用電腦上的處理器最大數目。  
  
 如需此參數 (在 MSBuild 3.5 中所引進) 的詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)。  
  
 下列範例會指示 MSBuild 使用三個背景工作處理序。 如果您使用此組態，MSBuild 就可以同時建立三個專案。  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>BuildInParallel 工作參數  
 `BuildInParallel` 是 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 工作上的選擇性 Boolean 參數。 將 `BuildInParallel` 設為`true` (預設值) 時，會產生多個背景工作處理序，盡可能同時建置最多個專案。 若要使其能正常運作，必須將 `/maxcpucount` 參數設為大於 1 的值，而且系統必須至少是雙核心或具有兩或多個處理器。  
  
 以下範例取自 microsoft.common.targets，說明如何設定 `BuildInParallel` 參數。  
  
```  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用多個處理器來建置專案](../msbuild/using-multiple-processors-to-build-projects.md)   
 [撰寫能夠辨識多處理器的記錄器](../msbuild/writing-multi-processor-aware-loggers.md)   
 [調整 C++ 組建平行處理原則部落格 (英文)](http://go.microsoft.com/fwlink/?LinkId=251457)



