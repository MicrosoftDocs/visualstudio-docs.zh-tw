---
title: ResourcesGenerator 工作 | Microsoft Docs
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
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82a9df8d7d3fae774e27e29e659d02aec35c7593
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662149"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> 工作會將一或多種資源 (.jpg、.ico、.bmp、二進位格式的 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 以及其他副檔名類型) 內嵌到 .resources 檔案。  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|說明|  
|---------------|-----------------|  
|`OutputPath`|必要的 **String** 參數。<br /><br /> 指定輸出目錄的路徑。 如果路徑不是絕對路徑，會將它視為相對於專案根目錄的路徑。|  
|`OutputResourcesFile`|必要的 **ITaskItem[]** 輸出參數。<br /><br /> 指定所產生 .resources 檔案的路徑和名稱。 如果路徑不是絕對路徑，會相對於專案根目錄產生 .resources 檔案。|  
|`ResourcesFiles`|必要的 **ITaskItem[]** 參數。<br /><br /> 指定要內嵌到所產生 .resources 檔案的一或多種資源。|  
  
## <a name="example"></a>範例  
 下列範例會產生使用單一 .bmp 資源的 .resources 檔案。 在相對於專案根目錄的目錄中產生 .bmp 資源。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
