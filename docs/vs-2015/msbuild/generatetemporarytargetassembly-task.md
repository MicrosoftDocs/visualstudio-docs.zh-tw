---
title: GenerateTemporaryTargetAssembly 工作 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 397bb367207646e110243e050c271815b6258ff5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668609"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果專案中有至少一個 [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] 網頁參考該專案中本機宣告的類型，<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> 工作會產生組件。 建置流程完成之後，或如果建置流程失敗，都會將產生的組件移除。  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|說明|  
|---------------|-----------------|  
|`AssemblyName`|必要的 **String** 參數。<br /><br /> 指定為專案所產生之組件的簡短名稱，它也是暫時產生之目標組件的名稱。 例如，如果專案產生名稱為 **WinExeAssembly.exe** 的 [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] 可執行檔，**AssemblyName** 參數的值會是 **WinExeAssembly**。|  
|`CompileTargetName`|必要的 **String** 參數。<br /><br /> 指定用來從原始程式碼檔產生組件的 [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] 目標名稱。 一般的 **CompileTargetName** 值為 **CoreCompile**。|  
|`CompileTypeName`|必要的 **String** 參數。<br /><br /> 指定由 **CompileTargetName** 參數所指定目標來執行的編譯型別。 對於 **CoreCompile** 目標，此值是 **Compile**。|  
|`CurrentProject`|必要的 **String** 參數。<br /><br /> 指定 [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] 專案檔的完整路徑，以供需要暫存目標組件的專案使用。|  
|`GeneratedCodeFiles`|選擇性的 **ITaskItem[]** 參數。<br /><br /> 指定 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) 工作產生的語言特定 Managed 程式碼檔的清單。|  
|`IntermediateOutputPath`|必要的 **String** 參數。<br /><br /> 指定要在其中產生暫存目標組件的目錄。|  
|`MSBuildBinPath`|必要的 **String** 參數。<br /><br /> 指定編譯暫存目標組件時所需的 **MSBuild.exe** 位置。|  
|`ReferencePath`|選擇性的 **ITaskItem[]** 參數。<br /><br /> 依照路徑與檔案名稱，指定編譯為暫存目標組件的型別所參考的組件清單。|  
|`ReferencePathTypeName`|必要的 **String** 參數。<br /><br /> 指定可指定組件參考 (**ReferencePath**) 清單的編譯目標 (**CompileTargetName**) 參數所使用的參數。 適當值為 **ReferencePath**。|  
  
## <a name="remarks"></a>備註  
 第一個標記編譯階段 (由 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) 所執行) 會將 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 檔案編譯為二進位格式。 因此，編譯器需要包含 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 檔案所使用型別的參考組件清單。 不過，如果 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 檔案使用相同專案中定義的型別，在建置專案之前，都不會建立該專案的對應組件。 因此，在第一個標記編譯階段期間，無法提供組件參考。  
  
 **MarkupCompilePass1** 會改為將含有相同專案中型別參考的 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 檔案轉換，延後至第二個標記編譯階段 (由 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) 所執行) 執行。 在執行 **MarkupCompilePass2** 之前，會產生暫存組件。 此組件包含延後其標記編譯階段的 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 檔案所使用的型別。 當 **MarkupCompilePass2** 執行以允許將延後編譯的 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 檔案轉換為二進位格式時，會將所產生組件的參考提供給它。  
  
## <a name="example"></a>範例  
 下列範例會產生暫存組件，因為 `Page1.xaml` 包含相同專案中型別的參考。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML 瀏覽器應用程式概觀](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
