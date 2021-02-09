---
title: ZipDirectory 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 ZipDirectory 工作，從目錄的內容建立 .zip 封存。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6b897a33dacdbd52beaabdd9289a010df92a85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847878"
---
# <a name="zipdirectory-task"></a>ZipDirectory 工作

從目錄的內容建立 *.zip* 封存。

>[!NOTE]
>`ZipDirectory` 工作僅適用於 MSBuild 15.8 和更新版本。

## <a name="parameters"></a>參數

 下表說明 `ZipDirectory` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`DestinationFile`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數<br /><br /> 要建立之 *.zip* 檔案的完整路徑。|
|`Overwrite`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true` ，則會覆寫目的地檔案（如果存在的話）。 預設值為 `false`。|
|`SourceDirectory`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要從其中建立 *.zip* 封存的目錄。|

## <a name="remarks"></a>備註

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

 下列範例 (（如果當做匯入的 *.targets* 檔案使用）) 會在建立專案之後，從輸出目錄建立 *.zip 封存。* `$(OutputPath)`屬性通常會在 MSBuild 專案檔中定義，因此匯入下列檔案的專案檔會產生 zip 封存 `output.zip` ：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
