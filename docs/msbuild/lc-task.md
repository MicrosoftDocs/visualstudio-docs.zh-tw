---
title: "LC 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: "15"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 6ff07f282d13d5520dc83935bd68667465dcea20
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="lc-task"></a>LC 工作
包裝 LC.exe (會從 .licx 檔案產生 .license 檔案)。 如需有關 LC.exe 的詳細資訊，請參閱 [Lc.exe (授權編譯器)](/dotnet/framework/tools/lc-exe-license-compiler)。  
  
## <a name="parameters"></a>參數  
 下表說明 `LC` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`LicenseTarget`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要產生 .licenses 檔案的可執行檔。|  
|`NoLogo`|選擇性的 `Boolean` 參數。<br /><br /> 隱藏 Microsoft 程式啟始資訊顯示。|  
|`OutputDirectory`|選擇性的 `String` 參數。<br /><br /> 指定要在其中放置輸出 .licenses 檔案的目錄。|  
|`OutputLicense`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定 .licenses 檔案的名稱。 如果未指定名稱，就會使用 .licx 檔案的名稱，並將 .licenses 檔案放在包含 .licx 檔案的目錄中。|  
|`ReferencedAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定產生 .license 檔案時所要載入的參考元件。|  
|`SdkToolsPath`|選擇性的 `String` 參數。<br /><br /> 指定 SDK 工具 (例如 resgen.exe) 的路徑。|  
|`Sources`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定含有 .licenses 檔案所要包含之授權元件的項目。 如需詳細資訊，請參閱 [Lc.exe (授權編譯器)](/dotnet/framework/tools/lc-exe-license-compiler) 中 `/complist` 參數的記載說明。|  
  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 如需這些其他參數的清單及其說明，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `LC` 工作來編譯授權。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)