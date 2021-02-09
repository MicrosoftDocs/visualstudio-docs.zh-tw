---
title: SignFile 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 SignFile 工作，利用指定的憑證來簽署指定的檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eef76a3757d9a2ff8ece5da5c18968097bd7618
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878158"
---
# <a name="signfile-task"></a>SignFile 工作

使用指定的憑證簽署指定的檔案。

## <a name="parameters"></a>參數

 下表說明 `SignFile` 工作的參數。

 請注意 SHA-256 憑證只在具有 .NET 4.5 及更高版本的電腦上才允許。

> [!WARNING]
> 從 Visual Studio 2013 Update 3 開始，這個工作有新的簽章，可讓您指定檔案的目標架構版本。 我們鼓勵您儘可能地使用新的簽章，因為只有當目標架構是 .NET 4.5 或更高版本時，MSBuild 程序才會使用 SHA-256 雜湊。 如果目標架構是 .NET 4.0 或更低版本，將不會使用 SHA-256 雜湊。

|參數|Description|
|---------------|-----------------|
|`CertificateThumbprint`|必要的 `String` 參數。<br /><br /> 指定簽署要使用的憑證。 此憑證必須位於目前使用者的個人存放區。|
|`SigningTarget`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要使用憑證簽署的檔案，其類型為 .exe 或 .dll。|
|`TimestampUrl`|選擇性的 `String` 參數。<br /><br /> 指定時間戳記伺服器的 URL。|
|`TargetFrameworkVersion`|對目標使用的 .NET Framework 版本。|

## <a name="remarks"></a>備註

 除了上述所列的參數，這項工作也會從 <xref:Microsoft.Build.Utilities.Task> 類別繼承參數。 如需這些額外參數及其說明的清單，請參閱 [Task 基底類別](../msbuild/task-base-class.md)。

## <a name="example"></a>範例

 下列範例使用 `SignFile` 工作來簽署 `FilesToSign` 項目集合中指定的檔案，並使用 `CertificateThumbprint` 屬性所指定的憑證。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> 憑證指紋是憑證的 SHA-1 雜湊。 如需詳細資訊，請參閱[取得受信任的根 CA 憑證的 SHA-1 雜湊](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\))。 如果您從憑證詳細資料複製並貼上指紋，請確定您未包含額外的 (3F) 不可見字元，這可能會導致 `SignFile` 找不到憑證。

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)