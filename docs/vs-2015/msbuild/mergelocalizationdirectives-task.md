---
title: MergeLocalizationDirectives 工作 | Microsoft Docs
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d6c2aa6cea687119e69b565da5468e8fa723641
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703401"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> 工作會將一或多個 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 二進位格式檔案的當地語系化屬性和註解合併到適用於整個組件的單一檔案。  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|說明|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|必要的 **ITaskItem[]** 參數。<br /><br /> 針對個別的 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 二進位格式檔案指定當地語系化指示詞檔案清單。|  
|`OutputFile`|必要的 **String** 輸出參數。<br /><br /> 指定編譯的當地語系化指示詞組件的輸出路徑。|  
  
## <a name="remarks"></a>備註  
 您可以將當地語系化屬性和註解加入至 [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] 內容中。 透過 [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)] 當地語系化支援，您可以取出當地語系化屬性和註解，然後將它們放入有別於產生組件的 .loc 檔案中。 您可以使用 **LocalizationPropertyStorage** 屬性來執行此動作。 如需當地語系化屬性和註解，以及 **LocalizationPropertyStorage** 的詳細資訊，請參閱[當地語系化屬性和註解](https://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f)。  
  
## <a name="example"></a>範例  
 下列範例會將數個 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 二進位格式檔案的當地語系化註解合併到單一 .loc 檔案。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
