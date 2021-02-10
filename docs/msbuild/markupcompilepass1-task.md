---
title: MarkupCompilePass1 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 MarkupCompilePass1 工作將不可當地語系化的 XAML 專案檔案轉換為編譯的二進位格式。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89d67c083c9e40710e79568c12684ab54653a5be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966197"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 工作

此工作會 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 將不可當地語系化的 XAML 專案檔案轉換為編譯的二進位格式。

## <a name="task-parameters"></a>工作參數

| 參數 | Description |
| - | - |
| `AllGeneratedFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作產生的完整檔案清單。 |
| `AlwaysCompileMarkupFilesInSeparateDomain` | 選擇性的 **布林值** 參數。<br /><br /> 指定是否在不同的 <xref:System.AppDomain> 中執行工作。 如果此參數傳回 **false**，則工作會在與 MSBuild 相同的情況下執行， <xref:System.AppDomain> 且執行速度會更快。 如果參數傳回 **true**，則工作會在第二個與 MSBuild 隔離的情況下執行， <xref:System.AppDomain> 並以較慢的速度執行。 |
| `ApplicationMarkup` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定應用程式定義 XAML 檔案的名稱。 |
| `AssembliesGeneratedDuringBuild` | 選擇性的 **String []** 參數。<br /><br /> 指定對在建置程序中變更之組件的參考。 例如，Visual Studio 解決方案可能包含一個專案，此專案參考另一個專案的已編譯輸出。 在此情況下，可以將第二個專案的已編譯輸出新增到 **AssembliesGeneratedDuringBuild** 參數。<br /><br /> 注意：**AssembliesGeneratedDuringBuild** 參數必須包含對組建方案所產生之一組完整組件的參考。 |
| `AssemblyName` | 必要的 **字串** 參數。<br /><br /> 指定為專案產生之組件的簡短名稱。 例如，如果專案產生的 Windows 可執行檔的名稱為 *WinExeAssembly.exe*， **AssemblyName** 參數的值會是 **>winexeassembly**。 |
| `AssemblyPublicKeyToken` | 選擇性的 **字串** 參數。<br /><br /> 指定組件的公開金鑰語彙基元。 |
| `AssemblyVersion` | 選擇性的 **字串** 參數。<br /><br /> 指定組件的版本號碼。 |
| `ContentFiles` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定鬆散內容檔案的清單。 |
| `DefineConstants` | 選擇性的 **字串** 參數。<br /><br /> 指定保留目前的 **DefineConstants** 值。 這會影響產生的目標群組件;如果變更此參數，則可能會變更目標群組件中的公用 API，而且可能會影響參考本機類型之 XAML 檔案的編譯。 |
| `ExtraBuildControlFiles` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定可控制當 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 工作返回時是否要觸發重建的檔案清單；如果這些檔案其中一個發生變更，就會觸發重建。 |
| `GeneratedBamlFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含以 XAML 二進位格式產生的檔案清單。 |
| `GeneratedCodeFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含已產生的 Managed 程式碼檔案清單。 |
| `GeneratedLocalizationFiles` | 選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 包含針對每個可當地語系化的 XAML 檔案所產生的當地語系化檔案清單。 |
| `HostInBrowser` | 選擇性的 **字串** 參數。<br /><br /> 指定產生的元件是否為 (XBAP) 的 XAML 瀏覽器應用程式。 有效的選項為 **true** 和 **false**。 如果為 **true**，就會產生程式碼來支援瀏覽器裝載。 |
| `KnownReferencePaths` | 選擇性的 **String []** 參數。<br /><br /> 指定對在建置程序中不會變更之組件的參考。 包含位於全域組件快取 (GAC) 、.NET 安裝目錄等等的元件。 |
| `Language` | 必要的 **String** 參數。<br /><br /> 指定編譯器支援的 Managed 語言。 有效的選項為 **C#**、**VB**、**JScript** 及 **C++**。 |
| `LanguageSourceExtension` | 選擇性的 **字串** 參數。<br /><br /> 指定附加至所產生的 Managed 程式碼檔案之副檔名的副檔名：<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> 如果 **LanguageSourceExtension** 參數未以特定值設定，則會使用語言的預設原始程式檔名稱副檔名： *.vb* （適用于 Visual Basic，Csharp 適用于 c #） *。* |
| `LocalizationDirectivesToLocFile` | 選擇性的 **字串** 參數。<br /><br /> 指定如何為每個來源 XAML 檔案產生當地語系化資訊。 有效的選項為 **None**、**CommentsOnly** 及 **All**。 |
| `OutputPath` | 必要的 **String** 參數。<br /><br /> 指定產生的 managed 程式碼檔案和 XAML 二進位格式檔案產生所在的目錄。 |
| `OutputType` | 必要的 **String** 參數。<br /><br /> 指定專案所產生之組件的類型。 有效的選項為 **winexe**、**exe**、**library** 及 **netmodule**。 |
| `PageMarkup` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定要處理的 XAML 檔案清單。 |
| `References` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定從檔案至元件的參考清單，這些元件包含 XAML 檔案中使用的類型。 |
| `RequirePass2ForMainAssembly` | 選擇性的 **Boolean** 輸出參數。<br /><br /> 指出專案是否包含參考內嵌至主要元件之區欄位型別的不可當地語系化 XAML 檔案。 |
| `RequirePass2ForSatelliteAssembly` | 選擇性的 **Boolean** 輸出參數。<br /><br /> 指出專案是否包含可當地語系化的 XAML 檔案，這些檔案會參考內嵌于主要元件中的區欄位型別。 |
| `RootNamespace` | 選擇性的 **字串** 參數。<br /><br /> 指定專案內類別的根命名空間。 當對應的 XAML 檔案不包含屬性時， **RootNamespace** 也會當做產生之 managed 程式碼檔案的預設命名空間使用 `x:Class` 。 |
| `SourceCodeFiles` | 選擇性的 **ITaskItem []** 參數。<br /><br /> 指定目前專案的程式碼檔案清單。 此清單不包括已產生的語言特定 Managed 程式碼檔案。 |
| `UICulture` | 選擇性的 **字串** 參數。<br /><br /> 指定內嵌產生的 XAML 二進位格式檔案之 UI 文化特性的附屬元件。 如果未設定 **UICulture** ，則產生的 XAML 二進位格式檔案會內嵌于主要元件中。 |
| `XAMLDebuggingInformation` | 選擇性的 **布林值** 參數。<br /><br /> 若為 **true**，則會產生診斷資訊，並將其包含在已編譯的 XAML 中，以便協助進行偵錯工具。 |

## <a name="remarks"></a>備註

工作 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 通常會將 XAML 編譯成二進位格式並產生程式碼檔案。 如果 XAML 檔案包含在相同專案中定義之類型的參考，則 **MarkupCompilePass1** 至第二個標記編譯通過 (**MarkupCompilePass2**) ，會延後編譯成二進位格式。 這類檔案的編譯必須延後，因為它們必須等待所參考的本機定義類型編譯完成。 但是，如果 XAML 檔案有 `x:Class` 屬性， <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> 就會產生它的語言特定程式碼檔案。

如果 XAML 檔案包含使用該屬性的專案，則可以當地語系化 `x:Uid` ：

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

當 XAML 檔案宣告的 XML 命名空間使用 `clr-namespace` 值來參考目前專案中的命名空間時，會參考本機定義的類型：

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

如果有可當地語系化的 XAML 檔案，或參考本機定義的類型，則需要第二個標記編譯階段，這需要執行 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) 和 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)。

## <a name="example"></a>範例

下列範例顯示如何將三個 *頁面* XAML 檔案轉換成二進位格式檔案。 *Page1* 包含對類型 `Class1` (位於專案的根命名空間中) 的參考，因此無法在此標記編譯階段中轉換成二進位格式檔案。 取而代之的是，會執行 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)，接著執行 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)。

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
- [WPF MSBuild 工作參考](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [MSBuild 工作參考](../msbuild/msbuild-task-reference.md)
- [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML 瀏覽器應用程式總覽](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)