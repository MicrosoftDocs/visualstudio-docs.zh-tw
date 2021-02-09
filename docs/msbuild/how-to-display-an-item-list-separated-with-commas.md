---
title: 如何：顯示以逗號分隔的項目清單 | Microsoft Docs
description: 瞭解如何使用 MSBuild 來顯示以逗號分隔的專案清單，或為專案清單指定其他分隔字串。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ac0295b2d6f4300fa29c893d61616977ad44b87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914418"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>如何：顯示以逗號分隔的項目清單

當您使用 Microsoft Build Engine (MSBuild) 中的專案清單時，以易於閱讀的方式來顯示這些專案清單的內容，有時會很有用。 否則，您可能必須進行以特殊分隔符號字串分隔項目清單的工作。 在這兩種情況下，您都可以為項目清單指定分隔符號字串。

## <a name="separate-items-in-a-list-with-commas"></a>以逗號分隔清單中的項目

根據預設，MSBuild 會使用分號來分隔清單中的專案。 例如，假設是含有下列值的 `Message` 項目：

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

當 `@(TXTFile)` 專案清單包含 *App1.txt*、 *App2.txt* 和 *App3.txt* 的專案時，訊息為：

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

如果您想要變更預設行為，可以指定自己的分隔符號。 指定項目清單分隔符號的語法是：

`@(ItemListName, '<separator>')`

分隔符號可以是單一字元或字串，且必須括在單引號中。

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>若要在項目之間插入逗號和空格

- 使用類似下列的項目標記法：

    `@(TXTFile, ', ')`

## <a name="example"></a>範例

在此範例中， [Exec](../msbuild/exec-task.md) 工作會執行 findstr 工具，以在檔案中尋找指定的文字字串， *Phrases.txt*。 在 findstr 命令中，常值搜尋字串會以 **-c：** switch 表示，因此專案分隔符號 `-c:` 會插入專案清單中的專案之間 `@(Phrase)` 。

此範例中，對等的命令列命令是：

`findstr /i /c:hello /c:world /c:msbuild phrases.txt`

```xml
<Project DefaultTargets = "Find"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <Phrase Include="hello"/>
        <Phrase Include="world"/>
        <Phrase Include="msbuild"/>
    </ItemGroup>

    <Target Name = "Find">
        <!-- Find some strings in a file -->
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [項目](../msbuild/msbuild-items.md)
