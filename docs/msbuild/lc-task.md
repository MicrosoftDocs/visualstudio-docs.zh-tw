---
title: LC 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865167b9182ca1f2264900a3e71ddeb4983e25ef
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167393"
---
# <a name="lc-task"></a>LC 工作

包裝*dism.exe*，它會從 *.licx*檔案產生*許可證*檔。 如需有關*dism.exe*的詳細資訊，請參閱[Dism.exe （授權編譯器）](/dotnet/framework/tools/lc-exe-license-compiler)。

## <a name="parameters"></a>參數

下表說明 `LC` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`LicenseTarget`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要為其產生*授權*檔案的可執行檔。|
|`NoLogo`|選擇性的 `Boolean` 參數。<br /><br /> 隱藏 Microsoft 程式啟始資訊顯示。|
|`OutputDirectory`|選擇性的 `String` 參數。<br /><br /> 指定要在其中放置輸出*許可證*檔的目錄。|
|`OutputLicense`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定*許可證*檔的名稱。 如果您未指定名稱，則會使用 *.licx*檔案的名稱，並將*授權*檔放在包含 *.licx*檔案的目錄中。|
|`ReferencedAssemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定在產生*許可證*檔時所要載入的參考元件。|
|`SdkToolsPath`|選擇性的 `String` 參數。<br /><br /> 指定 SDK 工具（例如*resgen.exe*）的路徑。|
|`Sources`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定包含授權元件的專案，以包含在*許可證*檔中。 如需詳細資訊，請參閱 [Lc.exe (授權編譯器)](/dotnet/framework/tools/lc-exe-license-compiler) 中 `/complist` 參數的記載說明。|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>範例

下列範例會使用 `LC` 工作來編譯授權。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
