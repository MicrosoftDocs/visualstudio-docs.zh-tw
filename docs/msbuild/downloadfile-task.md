---
title: DownloadFile 工作 | Microsoft Docs
description: 瞭解 MSBuild DownloadFile 工作的參數，此工作會使用 HTTP 來下載指定的檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c68b468cac63d556e9757210c8ce2933d94cba6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877209"
---
# <a name="downloadfile-task"></a>DownloadFile 工作

使用超文字傳輸通訊協定 (HTTP)，下載指定的檔案。

>[!NOTE]
>DownloadFile 工作僅適用於 MSBuild 15.8 和更新版本。

## <a name="parameters"></a>參數

下表說明 `DownloadFile` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`DestinationFileName`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數<br /><br /> 要用於已下載檔案的名稱。  根據預設，檔案名稱衍生自 `SourceUrl` 或遠端伺服器。|
|`DestinationFolder`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定檔案下載的目的地資料夾。  如果資料夾不存在，則會予以建立。|
|`DownloadedFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定已下載的檔案。|
|`Retries`|選擇性的 `Int32` 參數。<br /><br /> 指定如果所有先前的嘗試均失敗，要嘗試下載多少次。 預設值為零。|
|`RetryDelayMilliseconds`|選擇性的 `Int32` 參數。<br /><br /> 指定任何必要重試之間的延遲 (毫秒)。 預設值為 5000。|
|`SkipUnchangedFiles`|選擇性的 `Boolean` 參數。<br /><br /> 如果 `true`，則會略過下載未變更的檔案。 預設值為 `true`。 如果檔案根據遠端伺服器而具有相同的大小和相同的上次修改時間，`DownloadFile` 工作即會將檔案視為未變更。 <br /><br />**注意：** 並非所有 HTTP 伺服器都指出檔案的上次修改日期會再次下載檔案。|
|`SourceUrl`|必要的 `String` 參數。<br /><br /> 指定要下載的 URL。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

下列範例會下載檔案，並在建置專案之前將它包含在 `Content` 項目中。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
