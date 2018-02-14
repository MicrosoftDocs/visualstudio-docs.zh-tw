---
title: "使用多個處理器來建置專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f8bf385b6ee34c532e70557c0f04754ba0c56bb9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="using-multiple-processors-to-build-projects"></a>使用多個處理器來建置專案
MSBuild 可運用有多個處理器或多核心處理器的系統。 針對每個可用的處理器會建立個別的建置流程。 例如，如果系統具備四個處理器，則會建立四個建置流程。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可同時處理這些建置，因此將縮短整體的建置時間。 不過，平行建置會對建置處理序的發生方式帶來一些改變。 本主題將討論這些變更。  
  
## <a name="project-to-project-references"></a>專案對專案參考  
 當 [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] 使用平行建置來建置專案遇到專案對專案 (P2P) 參考時，它只會建置一次參考。 如果兩個專案都具有相同的 P2P 參考，則不會針對每個專案重建參考。 相反地，建置引擎會將相同的 P2P 參考傳回到相依於它的兩個專案。 工作階段中相同目標的未來要求會提供相同的 P2P 參考。  
  
## <a name="cycle-detection"></a>循環偵測  
 循環偵測的運作方式會如同在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 中一樣，除了 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 現在可以在不同的時間或者在建置中回報循環偵測。  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>平行建置期間的錯誤和例外狀況  
 在平行建置中，錯誤和例外狀況可以發生在與它們在非平行建置中不一樣的時間，且當其中一個專案無法建置時，另一個專案會繼續建置。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 不會停止與失敗的專案平行建置的任何專案建置。 其他專案仍會繼續建置，直到它們成功或失敗為止。 不過，如果已啟用 <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>，則即使發生錯誤，還是不會停止任何建置。  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Visual C++ 專案 (.vcproj) 和方案 (.sln) 檔  
 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案 (.vcproj) 和方案 (.sln) 檔兩者可以傳遞至 [MSBuild 工作](../msbuild/msbuild-task.md)。 針對 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案，會呼叫 VCWrapperProject，並接著建立內部 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案。 針對 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 方案，會建立 SolutionWrapperProject，並接著建立內部 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案。 在這兩種情況下，產生的專案會視為與任何其他 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案相同。  
  
## <a name="multi-process-execution"></a>多處理序執行  
 幾乎所有建置相關活動都需要目前的目錄在整個建置流程期間維持一致，以避免路徑相關錯誤。 因此，專案無法在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中不同的執行緒上執行，因為它們可能會導致建立多個目錄。  
  
 若要避免此問題，但仍啟用多處理器建置，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會使用「處理序隔離」。 透過使用處理序隔離，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可以建立最多 `n` 個處理序，其中 `n` 等於系統上可用的處理器數目。 例如，如果 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在具備兩個處理器的系統上建置方案，則只會建立兩個建置流程。 這些處理序會重複使用來建置方案中的所有專案。  
  
## <a name="see-also"></a>請參閱  
 [以平行方式建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [工作](../msbuild/msbuild-tasks.md)