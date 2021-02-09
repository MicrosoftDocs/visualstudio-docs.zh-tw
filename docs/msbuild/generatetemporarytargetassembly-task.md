---
title: GenerateTemporaryTargetAssembly 工作 | Microsoft Docs
description: 如果專案參考在本機宣告的類型，請使用 MSBuild GenerateTemporaryTargetAssembly 工作來產生元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4a41a5cbecea69d4843cbd70479a604f91b2218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914746"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly 工作

<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>如果專案中至少有一個 XAML 頁面參考該專案中本機宣告的類型，此工作就會產生一個元件。 建置流程完成之後，或如果建置流程失敗，都會將產生的組件移除。

## <a name="task-parameters"></a>工作參數

| 參數 | Description |
|--------------------------| - |
| `AssemblyName` | 必要的 **String** 參數。<br /><br /> 指定為專案所產生之組件的簡短名稱，它也是暫時產生之目標組件的名稱。 例如，如果專案產生的 Windows 可執行檔的名稱為 *WinExeAssembly.exe*， **AssemblyName** 參數的值會是 **>winexeassembly**。 |
| `CompileTargetName` | 必要的 **String** 參數。<br /><br /> 指定用來從原始程式碼檔產生元件的 MSBuild 目標名稱。 一般的 **CompileTargetName** 值為 **CoreCompile**。 |
| `CompileTypeName` | 必要的 **String** 參數。<br /><br /> 指定由 **CompileTargetName** 參數所指定目標來執行的編譯型別。 對於 **CoreCompile** 目標，此值是 **Compile**。 |
| `CurrentProject` | 必要的 **String** 參數。<br /><br /> 針對需要暫存目標群組件的專案，指定 MSBuild 專案檔案的完整路徑。 |
| `GeneratedCodeFiles` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) 工作產生的語言特定 Managed 程式碼檔的清單。 |
| `IntermediateOutputPath` | 必要的 **String** 參數。<br /><br /> 指定要在其中產生暫存目標組件的目錄。 |
| `MSBuildBinPath` | 必要的 **String** 參數。<br /><br /> 指定編譯暫存目標組件時所需的 *MSBuild.exe* 位置。 |
| `ReferencePath` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 依照路徑與檔案名稱，指定編譯為暫存目標組件的型別所參考的組件清單。 |
| `ReferencePathTypeName` | 必要的 **String** 參數。<br /><br /> 指定可指定組件參考 (**ReferencePath**) 清單的編譯目標 (**CompileTargetName**) 參數所使用的參數。 適當值為 **ReferencePath**。 |

## <a name="remarks"></a>備註

第一個標記編譯階段（由 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)執行）會將 XAML 檔案編譯成二進位格式。 因此，編譯器需要參考的元件清單，其中包含 XAML 檔案所使用的類型。 但是，如果 XAML 檔案使用相同專案中所定義的類型，則在建立專案之前，不會建立該專案的對應元件。 因此，在第一個標記編譯階段期間，無法提供組件參考。

相反地， **MarkupCompilePass1** 會延遲將相同專案中類型的參考轉換成第二個標記編譯階段（由 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)執行）的 XAML 檔案轉換。 在執行 **MarkupCompilePass2** 之前，會產生暫存組件。 此元件包含已延後標記編譯階段之 XAML 檔案所使用的類型。 在執行時，會將所產生元件的參考提供給 **MarkupCompilePass2** ，以允許將延遲的編譯 XAML 檔案轉換成二進位格式。

## <a name="example"></a>範例

下列範例會產生暫存組件，因為 Page1.xaml 包含相同專案中類型的參考。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)
- [工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 瀏覽器應用程式總覽](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
