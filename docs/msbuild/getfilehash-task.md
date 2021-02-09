---
title: GetFileHash 工作 | Microsoft Docs
description: 瞭解如何使用 MSBuild GetFileHash 工作來計算檔案或一組檔案內容的總和檢查碼。
ms.custom: SEO-VS-2020
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 163fbfd9c2bf0ca56b5b9b6bc11dc48420cfc270
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914703"
---
# <a name="getfilehash-task"></a>GetFileHash 工作

計算檔案或一組檔案內容的總和檢查碼。

這個工作已在 15.8 中新增，但是需要[因應措施](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272)以用於 16.0 以下的 MSBuild 版本。

## <a name="task-parameters"></a>工作參數

 下表說明 `GetFileHash` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Files`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br />要進行雜湊的檔案。|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br />`Files` 輸入含設定至檔案雜湊的其他中繼資料。|
|`Hash`|`String` 輸出參數。<br /><br />檔案的雜湊。 只有一個傳入項目時，才會設定此輸出。|
|`Algorithm`|選擇性的 `String` 參數。<br /><br />演算法。 允許值：`SHA256`、`SHA384`、`SHA512`。 預設值 = `SHA256`。|
|`MetadataName`|選擇性的 `String` 參數。<br /><br />中繼資料名稱，雜湊儲存在每個項目。 預設值為 `FileHash`。|
|`HashEncoding`|選擇性的 `String` 參數。<br /><br />要用於產生雜湊的編碼。 預設值為 `hex`。 允許值：`hex`、`base64`。|

## <a name="example"></a>範例

下列範例會使用 `GetFileHash` 工作來判斷及列印 `FilesToHash` 項目的總和檢查碼。

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)

- [工作參考](../msbuild/msbuild-task-reference.md)