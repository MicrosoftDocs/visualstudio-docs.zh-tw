---
title: "WriteLinesToFile 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1c284fefa1ed296e08049bd5bb7ea5df757107ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="writelinestofile-task"></a>WriteLinesToFile 工作
將所指定項目的路徑寫入至指定的文字檔。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `WriteLinestoFile` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`File`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要寫入項目的檔案。|  
|`Lines`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要寫入至檔案的項目。|  
|`Overwrite`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`，則工作會覆寫檔案中的任何現有內容。|  
|`Encoding`|選擇性的 `String` 參數。<br /><br /> 選取字元編碼 (例如，"Unicode")。  請參閱<xref:System.Text.Encoding>。|  
  
## <a name="remarks"></a>備註  
 如果 `Overwrite` 是 `true`，會建立新檔案，並將內容寫入至檔案，然後關閉檔案。 如果檔案已經存在，則會覆寫該檔案。 如果 `Overwrite` 是 `false`，會將內容附加至檔案，如果目標檔案不存在，則會建立該檔案。  
  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `WriteLinesToFile` 工作將 `MyItems` 項目集合中的項目路徑寫入至 `MyTextFile` 項目集合所指定的檔案。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)