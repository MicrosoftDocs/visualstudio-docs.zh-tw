---
title: "Project 項目 (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Project
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
caps.latest.revision: "31"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 013b8d0f23ad91eb6202f1ca72c36e486b0f53e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="project-element-msbuild"></a>Project 項目 (MSBuild)
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。  

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
 下列章節說明屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`DefaultTargets`|選擇性屬性。<br /><br /> 如果未指定任何目標，則為一或多個做為組建進入點的預設目標。 請以分號 (;) 來分隔多個目標。<br /><br /> 如果未在 `DefaultTargets` 屬性或 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 命令列中指定任何預設目標，則引擎會在已評估 [Import](../msbuild/import-element-msbuild.md) 項目之後執行專案中的第一個目標。|  
|`InitialTargets`|選擇性屬性。<br /><br /> 要在 `DefaultTargets` 屬性中或命令列上指定目標之前執行的一或多個初始目標。 請以分號 (;) 來分隔多個目標。|  
|`SDK`|選擇性屬性。 (僅適用於 Visual Studio 2017 或更新版本的 .NET Core 專案)。<br /><br /> 要用來建立隱含 Import 陳述式 (其會新增至 .proj 檔案) 的 SDK 版本。 例如，`<Project Sdk="Microsoft.NET.Sdk/1.0.0-RC" />`。|  
|`ToolsVersion`|選擇性屬性。<br /><br /> MSBuild 用來判斷 $(MSBuildBinPath) 和 $(MSBuildToolsPath) 之值的工具組版本。|  
|`TreatAsLocalProperty`|選擇性屬性。<br /><br /> 將不會被視為全域的屬性名稱。 這個屬性可防止特定的命令列屬性覆寫專案檔或目標檔案及所有後續匯入中設定的屬性值。 請以分號 (;) 來分隔多個屬性。<br /><br /> 一般來說，全域屬性值會覆寫專案檔或目標檔案中所設定的屬性值。 如果此屬性列於 `TreatAsLocalProperty` 值中，則全域屬性值不會覆寫該檔案及任何後續匯入中所設定的屬性值。 如需詳細資訊，請參閱[如何：使用不同選項來建置相同的原始程式檔](../msbuild/how-to-build-the-same-source-files-with-different-options.md)。 **注意︰**您可以使用 **/property** (或 **/p**) 參數，在命令提示字元中設定全域屬性。 您也可以使用 MSBuild 工作的 `Properties` 屬性，針對多專案組建中的子專案設定或修改全域屬性。 如需詳細資訊，請參閱 [MSBuild 工作](../msbuild/msbuild-task.md)。|  
|`Xmlns`|選擇性屬性。<br /><br /> 若有指定，`xmlns` 屬性的值必須為 "http://schemas.microsoft.com/developer/msbuild/2003"。|  

### <a name="child-elements"></a>子項目  

|項目|說明|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|選擇性項目。<br /><br /> 評估子項目，以選取一組要評估的 `ItemGroup` 項目和/或 `PropertyGroup` 項目。|  
|[Import](../msbuild/import-element-msbuild.md)|選擇性項目。<br /><br /> 可讓專案檔案匯入另一個專案檔。 專案中可能有零或多個 `Import` 項目。|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|選擇性項目。<br /><br /> 個別項目 (Item) 的群組項目 (Element)。 使用 [Item](../msbuild/item-element-msbuild.md) 項目 (Element) 來指定項目 (Item)。 專案中可能有零或多個 `ItemGroup` 項目。|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|選擇性項目。<br /><br /> 提供一種方式，在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔保存非 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的資訊。 專案中可能有零或一個 `ProjectExtensions` 項目。|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|選擇性項目。<br /><br /> 個別屬性的群組項目。 使用 [Property](../msbuild/property-element-msbuild.md) 項目來指定屬性。 專案中可能有零或多個 `PropertyGroup` 項目。|  
|[Target](../msbuild/target-element-msbuild.md)|選擇性項目。<br /><br /> 包含一組可循序執行的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作。 使用 [Item](../msbuild/task-element-msbuild.md) 項目來指定工作。 專案中可能有零或多個 `Target` 項目。|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|選擇性項目。<br /><br /> 提供一種方式，在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中登錄工作。 專案中可能有零或多個 `UsingTask` 項目。|  

### <a name="parent-elements"></a>父項目  
 無。  

## <a name="see-also"></a>另請參閱  
 [如何：指定要優先建置的目標](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [命令列參考](../msbuild/msbuild-command-line-reference.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
