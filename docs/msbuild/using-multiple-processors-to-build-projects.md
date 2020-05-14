---
title: 使用多個處理器來建置專案 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631298"
---
# <a name="use-multiple-processors-to-build-projects"></a>使用多個處理器來建置專案

MSBuild 可運用有多個處理器或多核心處理器的系統。 針對每個可用的處理器會建立個別的建置流程。 例如，如果系統具備四個處理器，則會建立四個建置流程。 MSBuild 可以同時處理這些生成，因此減少了總體生成時間。 不過，平行建置會對建置處理序的發生方式帶來一些改變。 本主題將討論這些變更。

## <a name="project-to-project-references"></a>專案對專案參考

 當 Microsoft 生成引擎在使用並行生成生成專案時遇到專案到專案 （P2P） 引用時，它僅生成一次引用。 如果兩個專案都具有相同的 P2P 參考，則不會針對每個專案重建參考。 相反地，建置引擎會將相同的 P2P 參考傳回到相依於它的兩個專案。 工作階段中相同目標的未來要求會提供相同的 P2P 參考。

## <a name="cycle-detection"></a>循環偵測

 迴圈檢測的功能與 MSBuild 2.0 中的功能相同，只不過現在 MSBuild 可以報告在不同時間或生成中檢測到迴圈。

## <a name="errors-and-exceptions-during-parallel-builds"></a>平行建置期間的錯誤和例外狀況

 在平行建置中，錯誤和例外狀況可以發生在與它們在非平行建置中不一樣的時間，且當其中一個專案無法建置時，另一個專案會繼續建置。 MSBuild 不會停止與失敗專案並行構建的任何專案生成。 其他專案仍會繼續建置，直到它們成功或失敗為止。 不過，如果已啟用 <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>，則即使發生錯誤，還是不會停止任何建置。

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++專案 （.vcxproj） 和解決方案 （.sln） 檔

 C++專案 *（.vcxproj*） 和解決方案 *（.sln*） 檔都可以傳遞到[MSBuild 任務](../msbuild/msbuild-task.md)。 對於C++專案，稱為 VCWrapperProject，然後創建內部 MSBuild 專案。 對於C++解決方案，將創建解決方案包裝專案，然後創建內部 MSBuild 專案。 在這兩種情況下，生成的專案都被視為與任何其他 MSBuild 專案相同的。

## <a name="multi-process-execution"></a>多處理序執行

 幾乎所有建置相關活動都需要目前的目錄在整個建置流程期間維持一致，以避免路徑相關錯誤。 因此，專案不能在 MSBuild 中的不同執行緒上運行，因為它們會導致創建多個目錄。

 為了避免此問題，但仍啟用多處理器生成，MSBuild 使用"進程隔離"。 通過使用進程隔離，MSBuild 可以創建最大`n`進程，其中`n`等於系統上可用的處理器數。 例如，如果 MSBuild 在具有兩個處理器的系統上生成解決方案，則只創建兩個生成進程。 這些處理序會重複使用來建置方案中的所有專案。

## <a name="see-also"></a>另請參閱

- [並行生成多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [工作](../msbuild/msbuild-tasks.md)
