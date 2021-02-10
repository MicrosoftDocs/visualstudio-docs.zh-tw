---
title: 使用多個處理器來建置專案 | Microsoft Docs
description: 藉由為每個可用的處理器建立個別的組建進程，瞭解 MSBuild 如何利用具有多個處理器或核心的系統。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1560b40fe94af8dae5223981dd8e0c790320085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946367"
---
# <a name="use-multiple-processors-to-build-projects"></a>使用多個處理器來建置專案

MSBuild 可運用有多個處理器或多核心處理器的系統。 針對每個可用的處理器會建立個別的建置流程。 例如，如果系統具備四個處理器，則會建立四個建置流程。 MSBuild 可以同時處理這些組建，因此會降低整體組建時間。 不過，平行建置會對建置處理序的發生方式帶來一些改變。 本主題將討論這些變更。

## <a name="project-to-project-references"></a>專案對專案參考

 當 Microsoft Build Engine 在使用平行組建來建立專案時，遇到專案對專案 (P2P) 參考，它只會建立參考一次。 如果兩個專案都具有相同的 P2P 參考，則不會針對每個專案重建參考。 相反地，建置引擎會將相同的 P2P 參考傳回到相依於它的兩個專案。 工作階段中相同目標的未來要求會提供相同的 P2P 參考。

## <a name="cycle-detection"></a>循環偵測

 迴圈偵測的運作方式與在 MSBuild 2.0 中相同，不同之處在于現在 MSBuild 可以在不同時間或在組建中報告迴圈的偵測。

## <a name="errors-and-exceptions-during-parallel-builds"></a>平行建置期間的錯誤和例外狀況

 在平行建置中，錯誤和例外狀況可以發生在與它們在非平行建置中不一樣的時間，且當其中一個專案無法建置時，另一個專案會繼續建置。 MSBuild 不會停止與失敗的專案建立平行建立的任何專案組建。 其他專案仍會繼續建置，直到它們成功或失敗為止。 不過，如果已啟用 <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>，則即使發生錯誤，還是不會停止任何建置。

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C + + 專案 (. .vcxproj) 和方案 ( .sln) 檔案

 C + + 專案 (*.vcxproj*) 和方案 (*.sln*) 檔案都可以傳遞給 [MSBuild](../msbuild/msbuild-task.md)工作。 針對 c + + 專案，會呼叫 VCWrapperProject，然後建立內部 MSBuild 專案。 針對 c + + 方案，會建立 SolutionWrapperProject，然後建立內部 MSBuild 專案。 在這兩種情況下，產生的專案都會被視為與任何其他 MSBuild 專案相同。

## <a name="multi-process-execution"></a>多處理序執行

 幾乎所有建置相關活動都需要目前的目錄在整個建置流程期間維持一致，以避免路徑相關錯誤。 因此，專案無法在 MSBuild 中的不同執行緒上執行，因為它們會導致建立多個目錄。

 為了避免這個問題，但仍啟用多處理器組建，MSBuild 會使用「進程隔離」。 藉由使用進程隔離，MSBuild 可以建立最多 `n` 進程，其中 `n` 等於系統上可用的處理器數目。 例如，如果 MSBuild 在具有兩個處理器的系統上建立方案，則只會建立兩個組建處理常式。 這些處理序會重複使用來建置方案中的所有專案。

## <a name="see-also"></a>另請參閱

- [平行建立多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [工作](../msbuild/msbuild-tasks.md)
