---
title: Unzip 工作 | Microsoft Docs
description: 瞭解 MSBuild 解壓縮工作的參數和使用方式，此工作會將 .zip 封存會解壓縮至指定的位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 213d37108e37b9002b2241e6c0806d6d7db7caf6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902487"
---
# <a name="unzip-task"></a>Unzip 工作

將 *.zip* 封存解壓縮至指定的位置。

>[!NOTE]
>`Unzip` 工作僅適用於 MSBuild 15.8 和更新版本。

## <a name="parameters"></a>參數

 下表說明 `Unzip` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`DestinationFolder`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數<br /><br /> 指定要將檔案解壓縮檔到的目的地資料夾。|
|`OverwriteReadOnlyFiles`|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，則會覆寫唯讀檔案。 預設值為 `false`。|
|`SkipUnchangedFiles`|選擇性的 `Boolean` 參數。<br /><br /> 若為 `true`，則會略過解壓縮未變更的檔案。 預設值為 `true`。 如果檔案具有相同的大小和相同的上次修改時間，`Unzip` 工作即會將檔案視為未變更。|
|`SourceFiles`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定一或多個檔案以便解壓縮。 指定多個檔案時，它們會依序解壓縮到相同的資料夾。|

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

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

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
