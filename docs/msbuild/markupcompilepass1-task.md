---
title: MarkupCompilePass1 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a847f096edf5e42623cb2cb32cf4fd871a89aad7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633508"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 工作

任務<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>將不可當地語系化的 XAML 專案檔案轉換為編譯的二進位格式。

## <a name="task-parameters"></a>工作參數

| 參數 | 描述 |
| - | - |
| `AllGeneratedFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作產生的完整檔案清單。 |
| `AlwaysCompileMarkupFilesInSeparateDomain` | 可選**布林參數**。<br /><br /> 指定是否在不同的 <xref:System.AppDomain> 中執行工作。 如果此參數返回**false，** 則任務與 MSBuild 運行相同<xref:System.AppDomain>，並且運行得更快。 如果參數返回**true，** 則任務在與 MSBuild 隔離並運行較慢的第二秒<xref:System.AppDomain>內運行。 |
| `ApplicationMarkup` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定應用程式定義 XAML 檔的名稱。 |
| `AssembliesGeneratedDuringBuild` | 可選**字串*** 參數。<br /><br /> 指定對在建置程序中變更之組件的參考。 例如，Visual Studio 解決方案可能包含一個專案，此專案參考另一個專案的已編譯輸出。 在此情況下，可以將第二個專案的已編譯輸出新增到 **AssembliesGeneratedDuringBuild** 參數。<br /><br /> 注意：**AssembliesGeneratedDuringBuild** 參數必須包含對組建方案所產生之一組完整組件的參考。 |
| `AssemblyName` | 所需的**字串**參數。<br /><br /> 指定為專案產生之組件的簡短名稱。 例如，如果專案正在生成名稱為*WinExeAssembly.exe*的 Windows 可執行檔，**則程式集名稱**參數的值為**WinExeAssembly**。 |
| `AssemblyPublicKeyToken` | 可選**字串**參數。<br /><br /> 指定組件的公開金鑰語彙基元。 |
| `AssemblyVersion` | 可選**字串**參數。<br /><br /> 指定組件的版本號碼。 |
| `ContentFiles` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定鬆散內容檔案的清單。 |
| `DefineConstants` | 可選**字串**參數。<br /><br /> 指定保留目前的 **DefineConstants** 值。 影響目的程式集生成;如果更改此參數，則目的程式集中的公共 API 可能會更改，並且引用本地類型的 XAML 檔的編譯可能會受到影響。 |
| `ExtraBuildControlFiles` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定可控制當 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作返回時是否要觸發重建的檔案清單；如果這些檔案其中一個發生變更，就會觸發重建。 |
| `GeneratedBamlFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 以 XAML 二進位格式包含生成的檔案清單。 |
| `GeneratedCodeFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含已產生的 Managed 程式碼檔案清單。 |
| `GeneratedLocalizationFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含為每個可當地語系化的 XAML 檔生成的當地語系化檔的清單。 |
| `HostInBrowser` | 可選**字串**參數。<br /><br /> 指定生成的程式集是否為 XAML 瀏覽器應用程式 （XBAP）。 有效的選項為 **true** 和 **false**。 如果為 **true**，就會產生程式碼來支援瀏覽器裝載。 |
| `KnownReferencePaths` | 可選**字串*** 參數。<br /><br /> 指定對在建置程序中不會變更之組件的參考。 包括位於全域組件快取 （GAC）、 .NET 安裝目錄中的程式集，等等。 |
| `Language` | 必要的 **String** 參數。<br /><br /> 指定編譯器支援的 Managed 語言。 有效的選項為 **C#**、**VB**、**JScript** 及 **C++**。 |
| `LanguageSourceExtension` | 可選**字串**參數。<br /><br /> 指定附加至所產生的 Managed 程式碼檔案之副檔名的副檔名：<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> 如果未使用特定值設置**語言源擴展**參數，則使用語言的預設原始檔案名副檔名 *：.vb*表示視覺化基本 *，.csharp*表示 C#。 |
| `LocalizationDirectivesToLocFile` | 可選**字串**參數。<br /><br /> 指定如何為每個源 XAML 檔生成當地語系化資訊。 有效的選項為 **None**、**CommentsOnly** 及 **All**。 |
| `OutputPath` | 必要的 **String** 參數。<br /><br /> 指定生成託管代碼檔和 XAML 二進位格式檔的目錄。 |
| `OutputType` | 必要的 **String** 參數。<br /><br /> 指定專案所產生之組件的類型。 有效的選項為 **winexe**、**exe**、**library** 及 **netmodule**。 |
| `PageMarkup` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定要處理的 XAML 檔的清單。 |
| `References` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定從檔到包含 XAML 檔中使用的類型的程式集的引用清單。 |
| `RequirePass2ForMainAssembly` | 選擇性的 **Boolean** 輸出參數。<br /><br /> 指示專案是否包含引用嵌入到主程式集中的本地類型的不可當地語系化的 XAML 檔。 |
| `RequirePass2ForSatelliteAssembly` | 選擇性的 **Boolean** 輸出參數。<br /><br /> 指示專案是否包含引用嵌入在主程式集中的本地類型的可當地語系化 XAML 檔。 |
| `RootNamespace` | 可選**字串**參數。<br /><br /> 指定專案內類別的根命名空間。 當相應的 XAML 檔不包含`x:Class`該屬性時 **，RootNamespace**也用作生成的託管代碼檔的預設命名空間。 |
| `SourceCodeFiles` | 可選**的 ITaskItem]** 參數。<br /><br /> 指定目前專案的程式碼檔案清單。 此清單不包括已產生的語言特定 Managed 程式碼檔案。 |
| `UICulture` | 可選**字串**參數。<br /><br /> 指定嵌入生成的 XAML 二進位格式檔的 UI 區域性的附屬程式集。 如果未設置**UI 文化**，則生成的 XAML 二進位格式檔將嵌入到主程式集中。 |
| `XAMLDebuggingInformation` | 可選**布林參數**。<br /><br /> **如果為 true，** 則生成診斷資訊並將其包含在編譯的 XAML 中，以説明調試。 |

## <a name="remarks"></a>備註

該<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>任務通常將 XAML 編譯為二進位格式並生成代碼檔。 如果 XAML 檔包含對同一專案中定義的類型的引用，則其編譯為二進位格式將由**MarkupCompilePass1**延遲到第二個標記編譯傳遞 **（MarkupCompilePass2**）。 這類檔案的編譯必須延後，因為它們必須等待所參考的本機定義類型編譯完成。 但是，如果 XAML 檔具有`x:Class`屬性，<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>請為其生成特定于語言的代碼檔。

如果 XAML 檔包含使用該屬性的元素，則 XAML 檔是可當地語系化的`x:Uid`：

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

XAML 檔在聲明使用`clr-namespace`該值引用當前專案中的命名空間的 XML 命名空間時引用本地定義的類型：

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

如果任何 XAML 檔是可當地語系化的，或者引用本地定義的類型，則需要第二次標記編譯傳遞，這需要運行[生成臨時目的程式集](../msbuild/generatetemporarytargetassembly-task.md)，然後運行[標記編譯Pass2](../msbuild/markupcompilepass2-task.md)。

## <a name="example"></a>範例

下面的示例演示如何將三*個頁面*XAML 檔轉換為二進位格式檔。 *Page1* 包含對類型 `Class1` (位於專案的根命名空間中) 的參考，因此無法在此標記編譯階段中轉換成二進位格式檔案。 取而代之的是，會執行 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)，接著執行 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
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