---
title: GenerateTemporaryTargetAssembly 工作 | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69333b87720513244e90c131f052d11099b62e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634041"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly 工作

如果<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>專案中至少有一個 XAML 頁引用在該專案中本地聲明的類型，則任務將生成程式集。 建置流程完成之後，或如果建置流程失敗，都會將產生的組件移除。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
|--------------------------| - |
| `AssemblyName` | 必要的 **String** 參數。<br /><br /> 指定為專案所產生之組件的簡短名稱，它也是暫時產生之目標組件的名稱。 例如，如果專案生成名稱為*WinExeAssembly.exe*的 Windows 可執行檔，**則程式集名稱**參數的值為**WinExeAssembly**。 |
| `CompileTargetName` | 必要的 **String** 參數。<br /><br /> 指定用於從原始程式碼檔生成程式集的 MSBuild 目標的名稱。 一般的 **CompileTargetName** 值為 **CoreCompile**。 |
| `CompileTypeName` | 必要的 **String** 參數。<br /><br /> 指定由 **CompileTargetName** 參數所指定目標來執行的編譯型別。 對於 **CoreCompile** 目標，此值是 **Compile**。 |
| `CurrentProject` | 必要的 **String** 參數。<br /><br /> 指定需要臨時目的程式集的專案的 MSBuild 專案檔案的完整路徑。 |
| `GeneratedCodeFiles` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) 工作產生的語言特定 Managed 程式碼檔的清單。 |
| `IntermediateOutputPath` | 必要的 **String** 參數。<br /><br /> 指定要在其中產生暫存目標組件的目錄。 |
| `MSBuildBinPath` | 必要的 **String** 參數。<br /><br /> 指定編譯暫存目標組件時所需的 *MSBuild.exe* 位置。 |
| `ReferencePath` | 可選**的 ITaskItem]** 參數。<br /><br /> 依照路徑與檔案名稱，指定編譯為暫存目標組件的型別所參考的組件清單。 |
| `ReferencePathTypeName` | 必要的 **String** 參數。<br /><br /> 指定可指定組件參考 (**ReferencePath**) 清單的編譯目標 (**CompileTargetName**) 參數所使用的參數。 適當值為 **ReferencePath**。 |

## <a name="remarks"></a>備註

第一個標記編譯傳遞，由[標記編譯Pass1](../msbuild/markupcompilepass1-task.md)運行，將XAML檔編譯為二進位格式。 因此，編譯器需要包含 XAML 檔使用的類型的引用程式集的清單。 但是，如果 XAML 檔使用在同一專案中定義的類型，則在生成專案之前不會為該專案創建相應的程式集。 因此，在第一個標記編譯階段期間，無法提供組件參考。

相反 **，MarkupCompilePass1**將包含對同一專案中類型的引用的 XAML 檔的轉換推遲到第二個標記編譯傳遞，該傳遞由[標記編譯Pass2](../msbuild/markupcompilepass2-task.md)執行。 在執行 **MarkupCompilePass2** 之前，會產生暫存組件。 此程式集包含 XAML 檔使用的類型，其標記編譯傳遞已延遲。 運行生成程式集時，向**MarkupCompilePass2**提供了對生成的程式集的引用，以允許將延遲編譯 XAML 檔轉換為二進位格式。

## <a name="example"></a>範例

下列範例會產生暫存組件，因為 Page1.xaml** 包含相同專案中類型的參考。

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
- [任務引用](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 瀏覽器應用程式概觀](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
