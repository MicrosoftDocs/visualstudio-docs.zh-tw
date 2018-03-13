---
title: "MarkupCompilePass2 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b74c60c5a9b34baef83d7cd71a9a8edf6211b4cb
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 工作

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作會在參考相同專案中類型的 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 檔案上執行第二階段標記編譯。

## <a name="task-parameters"></a>工作參數

|參數|描述|
|---------------|-----------------|
|`AlwaysCompileMarkupFilesInSeparateDomain`|選擇性的 **Boolean** 參數。<br /><br /> 指定是否在不同的 <xref:System.AppDomain> 中執行工作。 如果此參數傳回 **false**，工作就會在與 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] 相同的 <xref:System.AppDomain> 中執行，且執行速度會較快。 如果此參數傳回 **true**，工作就會在與 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] 隔離的第二個 <xref:System.AppDomain> 中執行，且執行速度會較慢。|
|`AssembliesGeneratedDuringBuild`|選擇性的 **String[]** 參數。<br /><br /> 指定對在建置程序中變更之組件的參考。 例如，Visual Studio 解決方案可能包含一個專案，此專案參考另一個專案的已編譯輸出。 在此情況下，可以將第二個專案的已編譯輸出新增到 **AssembliesGeneratedDuringBuild**。<br /><br /> 注意：**AssembliesGeneratedDuringBuild** 必須包含對組建方案所產生之一組完整組件的參考。|
|`AssemblyName`|必要的 **String** 參數。<br /><br /> 指定為專案產生之組件的簡短名稱。 例如，如果專案要產生名稱為 **WinExeAssembly.exe** 的 [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] 可執行檔，則 **AssemblyName** 參數的值會是 **WinExeAssembly**。|
|`GeneratedBaml`|選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含採用 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式的已產生檔案清單。|
|`KnownReferencePaths`|選擇性的 **String[]** 參數。<br /><br /> 指定對在建置程序中永不變更之組件的參考。 包括位於 [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]、位於 [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] 安裝目錄等位置中的組件。|
|`Language`|必要的 **String** 參數。<br /><br /> 指定編譯器支援的 Managed 語言。 有效的選項為 **C#**、**VB**、**JScript** 及 **C++**。|
|`LocalizationDirectivesToLocFile`|選擇性的 **String** 參數。<br /><br /> 指定如何產生每個來源 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案的當地語系化資訊。 有效的選項為 **None**、**CommentsOnly** 及 **All**。|
|`OutputPath`|必要的 **String** 參數。<br /><br /> 指定要在其中產生所產生之 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的目錄。|
|`OutputType`|必要的 **String** 參數。<br /><br /> 指定專案所產生之組件的類型。 有效的選項為 **winexe**、**exe**、**library** 及 **netmodule**。|
|`References`|選擇性的 **ITaskItem[]** 參數。<br /><br /> 指定從檔案到包含 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案中所使用類型之組件的參考清單。 一個參考 <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> 工作產生的組件，必須在 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作之前執行。|
|`RootNamespace`|選擇性的 **String** 參數。<br /><br /> 指定專案內類別的根命名空間。 當對應的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案未包含 `x:Class` 屬性時，**RootNamespace** 也用來作為所產生 Managed 程式碼檔案的預設命名空間。|
|`XAMLDebuggingInformation`|選擇性的 **Boolean** 參數。<br /><br /> 值為 **true** 時，會產生診斷資訊並包含在已編譯的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 中，以協助偵錯。|

## <a name="remarks"></a>備註

執行 **MarkupCompilePass2** 之前，您必須先產生一個暫時組件，此組件包含標記編譯階段已被延後之 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案所使用的類型。 您可以執行 **GenerateTemporaryTargetAssembly** 工作來產生暫時組件。

當 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 執行時，系統會將對所產生之暫時組件的參考提供給它，以允許現在將在第一個標記編譯階段中被延後編譯的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 檔案，編譯成二進位格式。

## <a name="example"></a>範例

下例示範如何使用 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作執行第二階段的編譯。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask 
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2" 
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2 
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>請參閱

[WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)  
[工作參考](../msbuild/wpf-msbuild-task-reference.md)  
[MSBuild 參考](../msbuild/msbuild-reference.md)  
[工作參考](../msbuild/msbuild-task-reference.md)  
[建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[WPF XAML 瀏覽器應用程式概觀](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)