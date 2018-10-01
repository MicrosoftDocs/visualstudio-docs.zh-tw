---
title: MSBuild 專案檔案結構描述參考 | Microsoft Docs
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
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134a66a38886201a9f53ed5d15dda009b095d72f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486226"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild 專案檔案結構描述參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[MSBuild 專案檔案結構描述參考](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference)。  
  
  
提供表格來說明所有的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] XML 結構描述項目及其可用屬性和子項目。  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 會使用專案檔，來指示建置引擎要建置哪些內容以及如何建置。 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔是符合 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] XML 結構描述的 XML 檔案。 本節說明適用於 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 的 XML 結構描述定義 (.xsd) 檔。  
  
## <a name="msbuild-xml-schema-elements"></a>MSBuild XML 結構描述項目  
 下表列出所有的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] XML 結構描述項目及其子項目和屬性。  
  
|元素|子元素|屬性|  
|-------------|--------------------|----------------|  
|[Choose 項目 (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|  
|[Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)|--|條件<br /><br /> 專案|  
|[ImportGroup 項目](../msbuild/importgroup-element.md)|匯入|條件|  
|[Item 項目 (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|條件<br /><br /> 排除<br /><br /> 包含<br /><br /> 移除|  
|[ItemDefinitionGroup 項目 (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|條件|  
|[ItemGroup 項目 (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|條件|  
|[ItemMetadata 項目 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|條件|  
|[OnError 項目 (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|條件<br /><br /> ExecuteTargets|  
|[Otherwise 項目 (MSBuild)](../msbuild/otherwise-element-msbuild.md)|選擇<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output 項目 (MSBuild)](../msbuild/output-element-msbuild.md)|--|條件<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Parameter 項目](../msbuild/parameter-element.md)|--|輸出<br /><br /> ParameterType<br /><br /> 必要|  
|[ParameterGroup 項目](../msbuild/parametergroup-element.md)|*Parameter*|--|  
|[Project 項目 (MSBuild)](../msbuild/project-element-msbuild.md)|選擇<br /><br /> 匯入<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> 目標<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[ProjectExtensions 項目 (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property 項目 (MSBuild)](../msbuild/property-element-msbuild.md)|--|條件|  
|[PropertyGroup 項目 (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|條件|  
|[Target 項目 (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> 條件<br /><br /> DependsOnTargets<br /><br /> 輸入<br /><br /> KeepDuplicateOutputs<br /><br /> 名稱<br /><br /> 輸出<br /><br /> Returns|  
|[Task 項目 (MSBuild)](../msbuild/task-element-msbuild.md)|輸出|條件<br /><br /> ContinueOnError<br /><br /> *Parameter*|  
|[TaskBody 項目 (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|評估|  
|[UsingTask 項目 (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> 條件<br /><br /> TaskFactory<br /><br /> TaskName|  
|[When 項目 (MSBuild)](../msbuild/when-element-msbuild.md)|選擇<br /><br /> ItemGroup<br /><br /> PropertyGroup|條件|  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [條件](../msbuild/msbuild-conditions.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)  
 [ MSBuild](msbuild.md)


