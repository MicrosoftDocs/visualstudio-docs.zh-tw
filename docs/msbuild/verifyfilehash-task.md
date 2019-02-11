---
title: VerifyFileHash 工作 | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8122f1a3869efe32d7ae35ff05cdbb77ad84375
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55485036"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash 工作

驗證檔案是否符合預期的檔案雜湊。

這個工作已在 15.8 中新增，但是需要[因應措施](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272)以用於 16.0 以下的 MSBuild 版本。

## <a name="task-parameters"></a>工作參數

 下表說明 `VerifyFileHash` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`File`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br />要雜湊處理及驗證的檔案。|
|`Hash`|必要的 `String` 參數。<br /><br />檔案的預期雜湊。|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br />`Files` 輸入含設定至檔案雜湊的其他中繼資料。|
|`Algorithm`|選擇性的 `String` 參數。<br /><br />演算法。 允許值：`SHA256`、`SHA384`、`SHA512`。 預設值 = `SHA256`。|
|`HashEncoding`|選擇性的 `String` 參數。<br /><br />要用於產生雜湊的編碼。 預設值為 `hex`。 允許值：`hex`、`base64`。|

## <a name="example"></a>範例

下列範例會使用 `VerifyFileHash` 工作來驗證它自己的總和檢查碼。

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

[工作](../msbuild/msbuild-tasks.md)

[工作參考](../msbuild/msbuild-task-reference.md)