---
title: 如何：顯示以逗號分隔的項目清單 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5493d3b95f7e9c0aa08ed3b06a99108e15697349
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633898"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>如何：顯示以逗號分隔的項目清單

當您在 Microsoft 生成引擎 （MSBuild） 中處理專案清單時，有時以易於閱讀的方式顯示這些專案清單的內容很有用。 否則，您可能必須進行以特殊分隔符號字串分隔項目清單的工作。 在這兩種情況下，您都可以為項目清單指定分隔符號字串。

## <a name="separate-items-in-a-list-with-commas"></a>以逗號分隔清單中的項目

預設情況下，MSBuild 使用分號來分隔清單中的專案。 例如，假設是含有下列值的 `Message` 項目：

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

當`@(TXTFile)`專案清單包含*App1.txt、App2.txt*和*App3.txt*項時，消息為： *App2.txt*

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

如果您想要變更預設行為，可以指定自己的分隔符號。 指定項目清單分隔符號的語法是：

`@(ItemListName, '<separator>')`

分隔符號可以是單一字元或字串，且必須括在單引號中。

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>若要在項目之間插入逗號和空格

- 使用類似下列的項目標記法：

    `@(TXTFile, ', ')`

## <a name="example"></a>範例

在此示例中[，Exec](../msbuild/exec-task.md)任務運行 findstr 工具來查找檔中指定的文本字串 *，短語.txt*。 在 findstr 命令中，文本搜索字串由 **-c：** 開關指示，因此項分隔符號`-c:`將插入`@(Phrase)`到項清單中的項之間。

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
