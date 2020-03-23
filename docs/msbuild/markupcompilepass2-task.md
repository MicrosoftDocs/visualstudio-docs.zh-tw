---
title: MarkupCompilePass2 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d18bc3638454e2a6b034cd2e35c3a158361a033e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633521"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 工作

該<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>任務對引用同一專案中類型的 XAML 檔執行二次標記編譯。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | 可選**布林參數**。<br /><br /> 指定是否在不同的 <xref:System.AppDomain> 中執行工作。 如果此參數返回**false，** 則任務與 MSBuild 相同<xref:System.AppDomain>運行，並且運行得更快。 如果參數返回**true，** 則任務在與 MSBuild 隔離並運行較慢的第二秒<xref:System.AppDomain>內運行。 |
| `AssembliesGeneratedDuringBuild` | 可選**字串*** 參數。<br /><br /> 指定對在建置程序中變更之組件的參考。 例如，Visual Studio 解決方案可能包含一個專案，此專案參考另一個專案的已編譯輸出。 在此情況下，可以將第二個專案的已編譯輸出新增到 **AssembliesGeneratedDuringBuild**。<br /><br /> 注意：**AssembliesGeneratedDuringBuild** 必須包含對組建方案所產生之一組完整組件的參考。 |
| `AssemblyName` | 必要的 **String** 參數。<br /><br /> 指定為專案產生之組件的簡短名稱。 例如，如果專案正在生成名稱為*WinExeAssembly.exe*的可執行檔，**則程式集名稱**參數的值為**WinExeAssembly**。 |
| `GeneratedBaml` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 以 XAML 二進位格式包含生成的檔案清單。 |
| `KnownReferencePaths` | 可選**字串*** 參數。<br /><br /> 指定對在建置程序中永不變更之組件的參考。 包括位於全域組件快取 （GAC）、 .NET 安裝目錄中的程式集，等等。 |
| `Language` | 必要的 **String** 參數。<br /><br /> 指定編譯器支援的 Managed 語言。 有效的選項為 **C#**、**VB**、**JScript** 及 **C++**。 |
| `LocalizationDirectivesToLocFile` | 可選**字串**參數。<br /><br /> 指定如何為每個源 XAML 檔生成當地語系化資訊。 有效的選項為 **None**、**CommentsOnly** 及 **All**。 |
| `OutputPath` | 必要的 **String** 參數。<br /><br /> 指定生成生成的 XAML 二進位格式檔的目錄。 |
| `OutputType` | 必要的 **String** 參數。<br /><br /> 指定專案所產生之組件的類型。 有效的選項為 **winexe**、**exe**、**library** 及 **netmodule**。 |
| `References` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定從檔到包含 XAML 檔中使用的類型的程式集的引用清單。 一個參考 <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> 工作產生的組件，必須在 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作之前執行。 |
| `RootNamespace` | 可選**字串**參數。<br /><br /> 指定專案內類別的根命名空間。 當相應的 XAML 檔不包含`x:Class`該屬性時 **，RootNamespace**也用作生成的託管代碼檔的預設命名空間。 |
| `XAMLDebuggingInformation` | 可選**布林參數**。<br /><br /> **如果為 true，** 則生成診斷資訊並將其包含在編譯的 XAML 中，以説明調試。 |

## <a name="remarks"></a>備註

在運行**MarkupCompilePass2**之前，必須生成一個臨時程式集，其中包含其標記編譯傳遞延遲的 XAML 檔使用的類型。 您可以執行 **GenerateTemporaryTargetAssembly** 工作來產生暫時組件。

運行時提供了<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>對生成的臨時程式集的引用，允許在第一個標記編譯中延遲編譯的 XAML 檔現在編譯為二進位格式。

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

## <a name="see-also"></a>另請參閱

- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild 任務引用](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild 任務引用](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 瀏覽器應用程式概觀](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
