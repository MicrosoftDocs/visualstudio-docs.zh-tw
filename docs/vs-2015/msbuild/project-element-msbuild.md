---
title: Project 項目 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a150e7eba1cc3e432c68154e6167ea88f50e906
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227281"
---
# <a name="project-element-msbuild"></a>Project 項目 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔案的必要根項目。  
  
## <a name="syntax"></a>語法  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`DefaultTargets`|選擇性屬性。<br /><br /> 如果未指定任何目標，則為一或多個做為組建進入點的預設目標。 請以分號 (;) 來分隔多個目標。<br /><br /> 如果未在 `DefaultTargets` 屬性或 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 命令列中指定任何預設目標，則引擎會在已評估 [Import](../msbuild/import-element-msbuild.md) 項目之後執行專案中的第一個目標。|  
|`InitialTargets`|選擇性屬性。<br /><br /> 要在 `DefaultTargets` 屬性中或命令列上指定目標之前執行的一或多個初始目標。 請以分號 (;) 來分隔多個目標。|  
|`ToolsVersion`|選擇性屬性。<br /><br /> MSBuild 用來判斷 $(MSBuildBinPath) 和 $(MSBuildToolsPath) 之值的工具組版本。|  
|`TreatAsLocalProperty`|選擇性屬性。<br /><br /> 將不會被視為全域的屬性名稱。 這個屬性可防止特定的命令列屬性覆寫專案檔或目標檔案及所有後續匯入中設定的屬性值。 請以分號 (;) 來分隔多個屬性。<br /><br /> 一般來說，全域屬性值會覆寫專案檔或目標檔案中所設定的屬性值。 如果此屬性列於 `TreatAsLocalProperty` 值中，則全域屬性值不會覆寫該檔案及任何後續匯入中所設定的屬性值。 如需詳細資訊，請參閱[如何：使用不同選項來建置相同的原始程式檔](../msbuild/how-to-build-the-same-source-files-with-different-options.md)。 **注意︰** 您可以使用 **/property** (或 **/p**) 參數，在命令提示字元中設定全域屬性。 您也可以使用 MSBuild 工作的 `Properties` 屬性，針對多專案組建中的子專案設定或修改全域屬性。 如需詳細資訊，請參閱 [MSBuild 工作](../msbuild/msbuild-task.md)。|  
|`Xmlns`|必要屬性。<br /><br /> `xmlns`屬性的值必須 「 http://schemas.microsoft.com/developer/msbuild/2003"。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|選擇性項目。<br /><br /> 評估子項目，以選取一組要評估的 `ItemGroup` 項目和/或 `PropertyGroup` 項目。|  
|[Import](../msbuild/import-element-msbuild.md)|選擇性項目。<br /><br /> 可讓專案檔案匯入另一個專案檔。 專案中可能有零或多個 `Import` 項目。|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|選擇性項目。<br /><br /> 個別項目 (Item) 的群組項目 (Element)。 使用 [Item](../msbuild/item-element-msbuild.md) 項目 (Element) 來指定項目 (Item)。 專案中可能有零或多個 `ItemGroup` 項目。|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|選擇性項目。<br /><br /> 提供一種方式，在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔保存非 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 的資訊。 專案中可能有零或一個 `ProjectExtensions` 項目。|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|選擇性項目。<br /><br /> 個別屬性的群組項目。 使用 [Property](../msbuild/property-element-msbuild.md) 項目來指定屬性。 專案中可能有零或多個 `PropertyGroup` 項目。|  
|[Target](../msbuild/target-element-msbuild.md)|選擇性項目。<br /><br /> 包含一組可循序執行的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 工作。 使用 [Item](../msbuild/task-element-msbuild.md) 項目來指定工作。 專案中可能有零或多個 `Target` 項目。|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|選擇性項目。<br /><br /> 提供一種方式，在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 中登錄工作。 專案中可能有零或多個 `UsingTask` 項目。|  
  
### <a name="parent-elements"></a>父項目  
 無。  
  
## <a name="see-also"></a>另請參閱  
 [如何：指定要優先建置的目標](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [命令列參考](../msbuild/msbuild-command-line-reference.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)


