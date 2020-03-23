---
title: MSBuild 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633131"
---
# <a name="msbuild-tasks"></a>MSBuild 工作

組建平台必須能夠在建置程序期間執行任意數目的動作。 MSBuild 使用*任務*來執行這些操作。 任務是 MSBuild 用於執行原子生成操作的可執行代碼單元。

## <a name="task-logic"></a>工作邏輯

 MSBuild XML 專案檔案格式無法自行完全執行生成操作，因此任務邏輯必須在專案檔案外部實現。

 工作的執行邏輯會實作為 .NET 類別，此類別會實作 <xref:Microsoft.Build.Framework> 命名空間中所定義的 <xref:Microsoft.Build.Framework.ITask> 介面。

 工作類別也會定義可供專案檔中的工作使用的輸入和輸出參數。 通過在[任務](../msbuild/task-element-msbuild.md)元素上放置具有相同名稱的對應屬性，並設置其值（如本文後面的示例所示），可以在專案檔案中給出任務類公開的所有公共可設置的非靜態非抽象屬性。

 若要撰寫自己的工作，請編寫可實作 <xref:Microsoft.Build.Framework.ITask> 介面的 Managed 類別。 有關詳細資訊，請參閱[任務寫入](../msbuild/task-writing.md)。

## <a name="execute-a-task-from-a-project-file"></a>從專案檔執行工作

 在執行專案檔中的工作之前，您必須先使用 [UsingTask](../msbuild/usingtask-element-msbuild.md) 項目，將實作工作之組件中的類型對應到工作名稱。 這使 MSBuild 知道在專案檔案中找到任務的執行邏輯時，該邏輯的位置。

 要在 MSBuild 專案檔案中執行任務，請創建一個元素，該元素的名稱為`Target`元素的子級。 如果工作接受參數，則會傳遞這些參數以做為項目的屬性。

 MSBuild 項清單和屬性可用作參數。 `MakeDir`例如，以下代碼調用任務並設置`Directories``MakeDir`物件的屬性的值等於`BuildDir`屬性的值：

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 工作也可以將資訊傳回專案檔，資訊可儲存於項目或屬性中，以供稍後使用。 例如，下列程式碼會呼叫 `Copy` 工作，並將來自 `CopiedFiles` 輸出屬性的資訊儲存於 `SuccessfullyCopiedFiles` 項目清單中。

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>包含的工作

 MSBuild 附帶許多工，如[複製](../msbuild/copy-task.md)檔、[創建目錄的 MakeDir](../msbuild/makedir-task.md)和編譯 C# 原始程式碼檔的[Csc。](../msbuild/csc-task.md) 有關可用任務和使用資訊的完整清單，請參閱[任務參考](../msbuild/msbuild-task-reference.md)。

## <a name="overridden-tasks"></a>覆寫的工作

 MSBuild 查找多個位置的任務。 第一個位置位於具有副檔名的檔中 *。覆蓋*存儲在 .NET 框架目錄中的任務。 這些檔案中的工作會覆寫任何其他具有相同名稱的工作，包括專案檔中的工作。 第二個位置是在具有副檔名的檔中 *。*.NET 框架目錄中的任務。 如果在這兩個位置中找不到工作，就會使用專案檔中的工作。

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [任務編寫](../msbuild/task-writing.md)
- [內聯任務](../msbuild/msbuild-inline-tasks.md)
