---
title: Unzip 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a46f2a079cc35e6c1add9e53abdcbdd283ddb9e
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059397"
---
# <a name="unzip-task"></a>Unzip 工作
將 `.zip` 封存解壓縮至指定的位置。

**注意︰**`Unzip` 工作僅適用於 MSBuild 15.8 和更新版本。
  
## <a name="parameters"></a>參數  
 下表說明 `Unzip` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`DestinationFolder`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數<br /><br /> 指定要將檔案解壓縮檔到的目的地資料夾。|
|`OverwriteReadOnlyFiles`|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，則會覆寫唯讀檔案。 預設值為 `false`。|
|`SkipUnchangedFiles`|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，則會略過解壓縮未變更的檔案。 預設值為 `true`。 如果檔案具有相同的大小和相同的上次修改時間，`Unzip` 工作即會將檔案視為未變更。|
|`SourceFiles`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個檔案以便解壓縮。 指定多個檔案時，它們會依序解壓縮到相同的資料夾。|
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會解壓縮封存，並覆寫任何唯讀檔案。
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
