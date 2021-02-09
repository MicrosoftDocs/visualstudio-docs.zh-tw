---
title: MSBuild 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何在建立程式期間使用工作，或執行不可部分完成之組建作業的可執行程式碼單位。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b3bb4c1a17cd5d1481be2fa942686bce3861bb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918922"
---
# <a name="msbuild-tasks"></a>MSBuild 工作

組建平台必須能夠在建置程序期間執行任意數目的動作。 MSBuild 會 *使用工作* 來執行這些動作。 工作是 MSBuild 用來執行不可部分完成之組建作業的可執行程式碼單位。

## <a name="task-logic"></a>工作邏輯

 MSBuild XML 專案檔案格式無法完全獨立執行組建作業，因此工作邏輯必須在專案檔之外執行。

 工作的執行邏輯會實作為 .NET 類別，此類別會實作 <xref:Microsoft.Build.Framework> 命名空間中所定義的 <xref:Microsoft.Build.Framework.ITask> 介面。

 工作類別也會定義可供專案檔中的工作使用的輸入和輸出參數。 藉由 [在工作專案](../msbuild/task-element-msbuild.md) 上放置具有相同名稱的對應屬性，並設定其值（如本文稍後的範例所示），可以在專案檔中提供工作類別所公開的所有公用可設定非靜態非抽象屬性值。

 若要撰寫自己的工作，請編寫可實作 <xref:Microsoft.Build.Framework.ITask> 介面的 Managed 類別。 如需詳細資訊，請參閱工作 [撰寫](../msbuild/task-writing.md)。

## <a name="execute-a-task-from-a-project-file"></a>從專案檔執行工作

 在執行專案檔中的工作之前，您必須先使用 [UsingTask](../msbuild/usingtask-element-msbuild.md) 項目，將實作工作之組件中的類型對應到工作名稱。 這可讓 MSBuild 知道當您在專案檔中找到工作的執行邏輯時，該在哪裡尋找。

 若要在 MSBuild 專案檔中執行工作，請使用工作名稱做為專案的子系來建立元素 `Target` 。 如果工作接受參數，則會傳遞這些參數以做為項目的屬性。

 MSBuild 專案清單和屬性可以當做參數使用。 例如，下列程式碼會呼叫工作 `MakeDir` ，並將物件的屬性值設定為 `Directories` `MakeDir` 等於屬性的值 `BuildDir` ：

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

 MSBuild 隨附許多工作，例如 [複製](../msbuild/copy-task.md)，這會複製檔案、 [MakeDir](../msbuild/makedir-task.md)、建立目錄和 [Csc](../msbuild/csc-task.md)，以編譯 c # 原始程式碼檔。 如需可用工作和使用方式資訊的完整清單，請參閱工作 [參考](../msbuild/msbuild-task-reference.md)。

## <a name="overridden-tasks"></a>覆寫的工作

 MSBuild 會在數個位置中尋找工作。 第一個位置是在副檔名為的檔案中 *。* 儲存在 .NET Framework 目錄中的 OverrideTasks。 這些檔案中的工作會覆寫任何其他具有相同名稱的工作，包括專案檔中的工作。 第二個位置是在副檔名為的檔案中 *。.NET Framework 目錄中的* 工作。 如果在這兩個位置中找不到工作，就會使用專案檔中的工作。

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [工作撰寫](../msbuild/task-writing.md)
- [內嵌工作](../msbuild/msbuild-inline-tasks.md)
