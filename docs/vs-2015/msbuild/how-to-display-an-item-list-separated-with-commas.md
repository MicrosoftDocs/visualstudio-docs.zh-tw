---
title: 如何：顯示以逗號分隔的項目清單 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93451d6d49082621df48c734de951e6a4bc7e281
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156635"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>如何：顯示以逗號分隔的項目清單
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在使用 [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) 中列出的項目時，建議您以易於閱讀的方式顯示這些項目清單中的內容。 否則，您可能必須進行以特殊分隔符號字串分隔項目清單的工作。 在這兩種情況下，您都可以為項目清單指定分隔符號字串。  
  
## <a name="separating-items-in-a-list-with-commas"></a>以逗號分隔清單中的項目  
 根據預設，[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 會使用分號來分隔清單中的項目。 例如，假設是含有下列值的 `Message` 項目：  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 當 `@(TXTFile)` 項目清單包含 App1.txt、App2.txt 和 App3.txt 項目時，訊息為：  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 如果您想要變更預設行為，可以指定自己的分隔符號。 指定項目清單分隔符號的語法是：  
  
 `@(ItemListName, '<separator>')`  
  
 分隔符號可以是單一字元或字串，且必須括在單引號中。  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>若要在項目之間插入逗號和空格  
  
- 使用類似下列的項目標記法：  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>範例  
 在此範例中，[Exec](../msbuild/exec-task.md) 工作會執行 findstr 工具，以在 Phrases.txt 檔案中尋找指定的文字字串。 在 findstr 命令中，字串常值搜尋是以 **/c:** 參數指定，因此 `@(Phrase)` 項目清單中的項目之間會差入 `/c:` 項目分隔符號。  
  
 此範例中，對等的命令列命令是：  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
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
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [項目](../msbuild/msbuild-items.md)
