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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53819a642edcdf0419dd445ac32dbde8d14ffb22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579532"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash 工作

驗證檔案是否符合預期的檔案雜湊。 如果雜湊不匹配，則任務將失敗。

這個工作已在 15.8 中新增，但是需要[因應措施](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272)以用於 16.0 以下的 MSBuild 版本。

## <a name="task-parameters"></a>工作參數

 下表說明 `VerifyFileHash` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`File`|必要的 `String` 參數。<br /><br />要雜湊和驗證的檔。|
|`Hash`|必要的 `String` 參數。<br /><br />檔案的預期雜湊。|
|`Algorithm`|選擇性的 `String` 參數。<br /><br />演算法。 允許值：`SHA256`、`SHA384`、`SHA512`。 預設值 = `SHA256`。|
|`HashEncoding`|選擇性的 `String` 參數。<br /><br />要用於產生雜湊的編碼。 預設為 `hex`。 允許值：`hex`、`base64`。|

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

在 MSBuild 16.5 及更高版本中，如果不希望生成在雜湊不匹配時失敗（例如，如果將雜湊比較用作控制流的條件），則可以使用以下代碼將警告降級為消息：

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
