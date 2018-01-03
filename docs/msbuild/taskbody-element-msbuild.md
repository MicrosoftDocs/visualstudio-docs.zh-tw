---
title: "TaskBody 元素 (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
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
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5263de3b583d39294ca5011922df441aee892d4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="taskbody-element-msbuild"></a>TaskBody 項目 (MSBuild)
包含傳遞至 `UsingTask``TaskFactory` 的資料。 如需詳細資訊，請參閱 [UsingTask 項目 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。  

 \<Project>  
 \<UsingTask>  
 \<TaskBody>  

## <a name="syntax"></a>語法  

```  
<TaskBody Evaluate="true/false" />  
```  

## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`Evaluate`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，當具現化工作時，MSBuild 會評估所有內部元素，並且展開項目和屬性，然後才將資訊傳遞給 `TaskFactory`。|  

### <a name="child-elements"></a>子元素  

|項目|描述|  
|-------------|-----------------|  
|資料|`TaskBody` 標籤之間的文字會逐字傳送給 `TaskFactory`。|  

### <a name="parent-elements"></a>父項目  

|項目|描述|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|提供一種方式，在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中登錄工作。 專案中可能有零或多個 `UsingTask` 項目。|  

## <a name="example"></a>範例  
 下列範例示範如何使用具有 `Evaluate` 屬性的 `TaskBody` 項目。  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
