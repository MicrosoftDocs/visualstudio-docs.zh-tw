---
title: RemoveDuplicates 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac8198d32db511aa908f5fa11618d449012715d3
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54798134"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
從指定的項目集合中移除重複項目。  
  
## <a name="parameters"></a>參數  
 下表說明 `RemoveDuplicates` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`Filtered`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已移除所有重複項目的項目集合。|  
|`Inputs`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要從中移除重複項目的項目集合。|  
  
## <a name="remarks"></a>備註  
 此工作不區分大小寫，而且在判斷重複項目時不會比較項目中繼資料。  
  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例使用 `RemoveDuplicates` 工作，以從 `MyItems` 項目集合中移除重複項目。 工作完成時，`FilteredItems` 項目集合會包含一個項目。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [工作](../msbuild/msbuild-tasks.md)
