---
title: ParameterGroup 項目 | Microsoft Docs
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
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f4faa9038a5931dec376903f166301f27f00b37
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656228"
---
# <a name="parametergroup-element"></a>ParameterGroup 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含選擇性參數清單，將出現在 `UsingTask``TaskFactory` 所產生的工作中。 如需詳細資訊，請參閱 [UsingTask 項目 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
  
## <a name="syntax"></a>語法  
  
```  
<ParameterGroup />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|說明|  
|-------------|-----------------|  
|[Parameter](../msbuild/parameter-element.md)|包含 `UsingTask``TaskFactory` 所產生之工作的特定參數相關資訊。 項目的名稱是參數的名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|提供一種方式，在 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 中登錄工作。 專案中可能有零或多個 `UsingTask` 項目。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `ParameterGroup` 元素。  
  
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
