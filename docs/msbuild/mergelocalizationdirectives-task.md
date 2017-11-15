---
title: "MergeLocalizationDirectives 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: c6071782251761563a2a279ced2926e68d441aec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives 工作
<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> 工作會將一或多個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的當地語系化屬性和註解合併到適用於整個組件的單一檔案。  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|描述|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|必要的 **ITaskItem[]** 參數。<br /><br /> 針對個別的 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案指定當地語系化指示詞檔案清單。|  
|`OutputFile`|必要的 **String** 輸出參數。<br /><br /> 指定編譯的當地語系化指示詞組件的輸出路徑。|  
  
## <a name="remarks"></a>備註  
 您可以將當地語系化屬性和註解加入至 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 內容中。 透過 [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] 當地語系化支援，您可以取出當地語系化屬性和註解，然後將它們放入有別於產生組件的 .loc 檔案中。 您可以使用 **LocalizationPropertyStorage** 屬性來執行此動作。 如需當地語系化屬性和註解，以及 **LocalizationPropertyStorage** 的詳細資訊，請參閱[當地語系化屬性和註解](/dotnet/framework/wpf/advanced/localization-attributes-and-comments)。  
  
## <a name="example"></a>範例  
 下列範例會將數個 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二進位格式檔案的當地語系化註解合併到單一 .loc 檔案。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)