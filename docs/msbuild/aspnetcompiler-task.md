---
title: 使用 AspNetCompiler 工作先行編譯 ASP.NET 應用程式 | Microsoft Docs
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
ms.openlocfilehash: a6535dbec7c09f0888d0fb29a2e6b801632da22f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593456"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler 工作
`AspNetCompiler` 工作會包裝 aspnet_compiler.exe，此為先行編譯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式的公用程式。

## <a name="task-parameters"></a>工作參數
下表說明 `AspNetCompiler` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，強式名稱的組件將允許部分信任的呼叫端。|
|`Clean`|選擇性的 `Boolean` 參數<br /><br /> 如果此參數為 `true`，將全新建置先行編譯的應用程式。 任何先前已編譯的元件都將重新編譯。 預設值為 `false`。 此參數 (Parameter) 對應到 aspnet_compiler.exe 上的 **-c** 參數 (Switch)。|
|`Debug`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，就會在編譯期間發出偵錯資訊 (.PDB 檔案)。 預設值為 `false`。 此參數 (Parameter) 對應到 aspnet_compiler.exe 上的 **-d** 參數 (Switch)。|
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，就不會在建立時完整簽署組件。|
|`FixedNames`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，就會為編譯的組件指定固定的名稱。|
|`Force`|選擇性的 `Boolean` 參數<br /><br /> 如果此參數為 `true`，工作將會覆寫目標目錄 (如果已經存在)。 現有的內容都會遺失。 預設值為 `false`。 此參數 (Parameter) 對應到 aspnet_compiler.exe 上的 **-f** 參數 (Switch)。|
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定強式名稱金鑰容器。|
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定強式名稱金鑰檔的實體路徑。|
|`MetabasePath`|選擇性的 `String` 參數。<br /><br /> 指定應用程式的完整 IIS Metabase 路徑。 此參數無法與 `VirtualPath` 或 `PhysicalPath` 參數相結合。 此參數 (Parameter) 對應到 aspnet_compiler.exe 上的 **-m** 參數 (Switch)。|
|`PhysicalPath`|選擇性的 `String` 參數。<br /><br /> 指定要編譯之應用程式的實體路徑。 如果此參數遺失，可以使用 IIS Metabase 來尋找應用程式。 此參數 (Parameter) 對應到 aspnet_compiler.exe 上的 **-p** 參數 (Switch)。|
|`TargetFrameworkMoniker`|選擇性的 `String` 參數。<br /><br /> 指定 TargetFrameworkMoniker，指示應該使用 aspnet_compiler.exe 的哪一個 .NET Framework 版本。 只接受 .NET Framework Moniker。|
|`TargetPath`|選擇性的 `String` 參數。<br /><br /> 指定編譯應用程式的實體路徑。 如果未指定，則會就地先行編譯應用程式。|
|`Updateable`|選擇性的 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，將可更新先行編譯的應用程式。  預設值為 `false`。 此參數 (Parameter) 對應到 aspnet_compiler.exe 上的 **-u** 參數 (Switch)。|
|`VirtualPath`|選擇性的 `String` 參數。<br /><br /> 要編譯之應用程式的虛擬路徑。 如果指定了 `PhysicalPath`，就能使用實體路徑來尋找應用程式。 否則，會使用 IIS metabase，而且假設應用程式位於預設網站中。 此參數 (Parameter) 對應到 aspnet_compiler.exe 上的 **-v** 參數 (Switch)。|

## <a name="remarks"></a>備註
除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 如需這些其他參數的清單及其描述，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。

## <a name="example"></a>範例
下列程式碼範例使用 `AspNetCompiler` 工作來先行編譯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式。

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
