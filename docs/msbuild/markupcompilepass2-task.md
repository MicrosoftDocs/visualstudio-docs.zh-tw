---
title: MarkupCompilePass2 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 MarkupCompilePass2 工作，在參考相同專案中類型的 XAML 檔案上執行第二階段標記編譯。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7425e0342974c3b000486f57227f768aac47b9ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966171"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 工作

此工作 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 會在參考相同專案中類型的 XAML 檔案上執行第二階段標記編譯。

## <a name="task-parameters"></a>工作參數

| 參數 | Description |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | 選擇性的 **布林值** 參數。<br /><br /> 指定是否在不同的 <xref:System.AppDomain> 中執行工作。 如果此參數傳回 **false**，則工作會在與 MSBuild 相同的情況 <xref:System.AppDomain> 下執行，且執行速度會更快。 如果參數傳回 **true**，則工作會在第二個與 MSBuild 隔離的情況下執行， <xref:System.AppDomain> 並以較慢的速度執行。 |
| `AssembliesGeneratedDuringBuild` | 選擇性的 **String []** 參數。<br /><br /> 指定對在建置程序中變更之組件的參考。 例如，Visual Studio 解決方案可能包含一個專案，此專案參考另一個專案的已編譯輸出。 在此情況下，可以將第二個專案的已編譯輸出新增到 **AssembliesGeneratedDuringBuild**。<br /><br /> 注意：**AssembliesGeneratedDuringBuild** 必須包含對組建方案所產生之一組完整組件的參考。 |
| `AssemblyName` | 必要的 **String** 參數。<br /><br /> 指定為專案產生之組件的簡短名稱。 例如，如果專案產生的可執行檔的名稱為 *WinExeAssembly.exe*， **AssemblyName** 參數的值會是 **>winexeassembly**。 |
| `GeneratedBaml` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含以 XAML 二進位格式產生的檔案清單。 |
| `KnownReferencePaths` | 選擇性的 **String []** 參數。<br /><br /> 指定對在建置程序中永不變更之組件的參考。 包含位於全域組件快取 (GAC) 、.NET 安裝目錄等等的元件。 |
| `Language` | 必要的 **String** 參數。<br /><br /> 指定編譯器支援的 Managed 語言。 有效的選項為 **C#**、**VB**、**JScript** 及 **C++**。 |
| `LocalizationDirectivesToLocFile` | 選擇性的 **字串** 參數。<br /><br /> 指定如何為每個來源 XAML 檔案產生當地語系化資訊。 有效的選項為 **None**、**CommentsOnly** 及 **All**。 |
| `OutputPath` | 必要的 **String** 參數。<br /><br /> 指定產生的 XAML 二進位格式檔案所產生的目錄。 |
| `OutputType` | 必要的 **String** 參數。<br /><br /> 指定專案所產生之組件的類型。 有效的選項為 **winexe**、**exe**、**library** 及 **netmodule**。 |
| `References` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定從檔案至元件的參考清單，這些元件包含 XAML 檔案中使用的類型。 一個參考 <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> 工作產生的組件，必須在 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 工作之前執行。 |
| `RootNamespace` | 選擇性的 **字串** 參數。<br /><br /> 指定專案內類別的根命名空間。 當對應的 XAML 檔案不包含屬性時， **RootNamespace** 也會當做產生之 managed 程式碼檔案的預設命名空間使用 `x:Class` 。 |
| `XAMLDebuggingInformation` | 選擇性的 **布林值** 參數。<br /><br /> 若為 **true**，則會產生診斷資訊，並將其包含在已編譯的 XAML 中，以便協助進行偵錯工具。 |

## <a name="remarks"></a>備註

在您執行 **MarkupCompilePass2** 之前，您必須產生暫存元件，其中包含已延後標記編譯階段之 XAML 檔案所使用的類型。 您可以執行 **GenerateTemporaryTargetAssembly** 工作來產生暫時組件。

在執行時，會提供所產生之暫存元件的參考，以便在 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> 第一個標記編譯階段中延遲編譯的 XAML 檔案現在會編譯成二進位格式。

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
- [WPF MSBuild 工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild 工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 瀏覽器應用程式總覽](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
