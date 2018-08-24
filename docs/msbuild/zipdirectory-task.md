---
title: ZipDirectory 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0dbd45d32e2268a687d09c48527acb1a6df0bff5
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468360"
---
# <a name="zipdirectory-task"></a>ZipDirectory 工作
從目錄的內容建立 *.zip* 封存。

>[!NOTE]
>`ZipDirectory` 工作僅適用於 MSBuild 15.8 和更新版本。
  
## <a name="parameters"></a>參數  
 下表說明 `ZipDirectory` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`DestinationFile`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數<br /><br /> 要建立之 *.zip* 檔案的完整路徑。|
|`Overwrite`|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，會覆寫存在的目的地檔案。 預設值為 `false`。|
|`SourceDirectory`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要從其中建立 *.zip* 封存的目錄。|
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會在建置專案後，從輸出目錄建立 *.zip* 封存。
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip">
        />
    </Target>

</Project>
```
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
