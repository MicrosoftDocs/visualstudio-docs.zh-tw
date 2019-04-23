---
title: Touch 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf68bf5dada310a23136e431fdaecad3e738d4bc
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655539"
---
# <a name="touch-task"></a>Touch 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

設定檔案的存取和修改時間。  
  
## <a name="parameters"></a>參數  
 下表說明 `Touch` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`AlwaysCreate`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，工作會建立任何不存在的檔案。|  
|`Files`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要碰觸的檔案集合。|  
|`ForceTouch`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，工作會強制碰觸檔案，即使檔案是唯讀也一樣。|  
|`Time`|選擇性的 `String` 參數。<br /><br /> 指定目前時間以外的時間。 格式必須是 <xref:System.DateTime.Parse%2A> 方法可接受的格式。|  
|`TouchedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已順利碰觸的項目集合。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例使用 `Touch` 工作來變更 `Files` 項目集合中指定之檔案的存取和修改時間，並將順利碰觸的檔案清單放入 `FilesTouched` 項目集合。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
