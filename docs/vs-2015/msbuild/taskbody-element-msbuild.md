---
title: TaskBody 元素 (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7918844915d32893491f69b4e7f58a5867c3613c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660576"
---
# <a name="taskbody-element-msbuild"></a>TaskBody 項目 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含傳遞至 `UsingTask``TaskFactory` 的資料。 如需詳細資訊，請參閱 [UsingTask 項目 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。  
  
 \<Project>  
 \<UsingTask>  
 \<TaskBody>  
  
## <a name="syntax"></a>語法  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`Evaluate`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，當具現化工作時，MSBuild 會評估所有內部元素，並且展開項目和屬性，然後才將資訊傳遞給 `TaskFactory`。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|說明|  
|-------------|-----------------|  
|資料|`TaskBody` 標籤之間的文字會逐字傳送給 `TaskFactory`。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|提供一種方式，在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 中登錄工作。 專案中可能有零或多個 `UsingTask` 項目。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用具有 `Evaluate` 屬性的 `TaskBody` 項目。  
  
```  
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
