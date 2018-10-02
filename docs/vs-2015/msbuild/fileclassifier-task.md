---
title: FileClassifier 工作 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06decaf5a2a59b4efb2e4f30f41298ebd3e5d533
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499918"
---
# <a name="fileclassifier-task"></a>FileClassifier 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[FileClassifier 工作](https://docs.microsoft.com/visualstudio/msbuild/fileclassifier-task)。  
  
  
<xref:Microsoft.Build.Tasks.Windows.FileClassifier> 工作會將一組來源資源分類為將內嵌至組件的來源資源。 如果無法將資源當地語系化，即會將它內嵌至主應用程式組件；否則，會將它內嵌至附屬組件。  
  
## <a name="task-parameters"></a>工作參數  
  
|參數|描述|  
|---------------|-----------------|  
|`CLREmbeddedResource`|未使用。|  
|`CLRResourceFiles`|未使用。|  
|`CLRSatelliteEmbeddedResource`|未使用。|  
|`Culture`|選擇性的 **String** 參數。<br /><br /> 指定組建的文化特性。 如果組建為不可當地語系化，則此值可以是 **null**。 如果是 **null**，預設值即為 **CultureInfo.InvariantCulture** 所傳回的小寫值。|  
|`MainEmbeddedFiles`|選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 指定內嵌於主組件的不可當地語系化資源。|  
|`OutputType`|必要的 **String** 參數。<br /><br /> 指定要內嵌所指定原始程式檔的檔案類型。 有效值為 **exe**、**winexe** 或 **library**。|  
|`SatelliteEmbeddedFiles`|選擇性的 **ITaskItem[]** 輸出參數。<br /><br /> 針對 **Culture** 參數所指定的文化特性，指定要內嵌到附屬組件的可當地語系化檔案。|  
|`SourceFiles`|必要的 **ITaskItem[]** 參數。<br /><br /> 指定要分類的檔案清單。|  
  
## <a name="remarks"></a>備註  
 如果未設定 **Culture** 參數，使用 **SourceFiles** 參數指定的所有資源都是不可當地語系化的；除非它們與設為 **false** 的 **Localizable** 屬性相關聯，否則，它們是可當地語系化的。  
  
## <a name="example"></a>範例  
 下列範例會將單一來源檔案分類為資源，然後將它內嵌於加拿大法文 (fr-CA) 文化特性的附屬組件中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另請參閱  
 [WPF MSBuild 參考](../msbuild/wpf-msbuild-reference.md)   
 [工作參考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [建置 WPF 應用程式 (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



