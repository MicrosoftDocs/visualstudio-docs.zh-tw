---
title: 使用 AspNetCompiler 工作來先行編譯 ASP.NET
description: 使用 MSBuild AspNetCompiler 工作包裝 aspnet_compiler.exe，這是先行編譯 ASP.NET 應用程式的公用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: e77316628f2251fd44d27edaec4c91354fd81a4b
ms.sourcegitcommit: 02445b684e69c1a665a7e06e9b46072d3fcd7ba6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96516089"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler 工作

此工作會 `AspNetCompiler` 包裝 *aspnet_compiler.exe*，這是先行編譯 ASP.NET 應用程式的公用程式。

## <a name="task-parameters"></a>工作參數

下表說明 `AspNetCompiler` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，強式名稱的組件將允許部分信任的呼叫端。|
|`Clean`|選擇性的 `Boolean` 參數<br /><br /> 如果此參數為 `true`，將全新建置先行編譯的應用程式。 任何先前已編譯的元件都將重新編譯。 預設值為 `false`。 此參數會對應至 *aspnet_compiler.exe* 上的 **-c** 參數。|
|`Debug`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，就會在編譯期間發出偵錯資訊 (.PDB 檔案)。 預設值為 `false`。 此參數會對應至 *aspnet_compiler.exe* 上的 **-d** 參數。|
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，就不會在建立時完整簽署組件。|
|`FixedNames`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，就會為編譯的組件指定固定的名稱。|
|`Force`|選擇性的 `Boolean` 參數<br /><br /> 如果此參數為 `true`，工作將會覆寫目標目錄 (如果已經存在)。 現有的內容都會遺失。 預設值為 `false`。 此參數會對應至 *aspnet_compiler.exe* 上的 **-f** 參數。|
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定強式名稱金鑰容器。|
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定強式名稱金鑰檔的實體路徑。|
|`MetabasePath`|選擇性的 `String` 參數。<br /><br /> 指定應用程式的完整 IIS Metabase 路徑。 此參數無法與 `VirtualPath` 或 `PhysicalPath` 參數相結合。 此參數會對應至 *aspnet_compiler.exe* 上的 **-m** 參數。|
|`PhysicalPath`|選擇性的 `String` 參數。<br /><br /> 指定要編譯之應用程式的實體路徑。 如果此參數遺失，可以使用 IIS Metabase 來尋找應用程式。 此參數會對應至 *aspnet_compiler.exe* 上的 **-p** 參數。|
|`TargetFrameworkMoniker`|選擇性的 `String` 參數。<br /><br /> 指定 TargetFrameworkMoniker，指出應該使用哪一個 .NET Framework 版本的 *aspnet_compiler.exe* 。 只接受 .NET Framework Moniker。|
|`TargetPath`|選擇性的 `String` 參數。<br /><br /> 指定編譯應用程式的實體路徑。 如果未指定，則會就地先行編譯應用程式。|
|`Updateable`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，將可更新先行編譯的應用程式。  預設值為 `false`。 此參數會對應至 *aspnet_compiler.exe* 上的 **-u** 參數。|
|`VirtualPath`|選擇性的 `String` 參數。<br /><br /> 要編譯之應用程式的虛擬路徑。 如果指定了 `PhysicalPath`，就能使用實體路徑來尋找應用程式。 否則，會使用 IIS metabase，而且假設應用程式位於預設網站中。 此參數會對應至 *aspnet_compiler.exe* 上的 **-v** 參數。|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>範例

下列程式碼範例會使用此工作 `AspNetCompiler` 來先行編譯 ASP.NET 應用程式。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>請參閱

* [工作](../msbuild/msbuild-tasks.md)
* [工作參考](../msbuild/msbuild-task-reference.md)
* [ASP.NET 編譯工具 ( # A0) ](/previous-versions/ms229863(v=vs.100))
