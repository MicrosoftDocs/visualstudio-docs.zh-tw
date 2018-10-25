---
title: Parameter 元素 | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4778923bf6c9e521a7ee26546510466fcfefc83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894250"
---
# <a name="parameter-element"></a>Parameter 元素
包含 `UsingTask` `TaskFactory` 所產生之工作的特定參數相關資訊。  元素的名稱是參數的名稱。  如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  

## <a name="syntax"></a>語法  

```xml  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`ParameterType`|選擇性屬性。<br /><br /> 參數的 .NET 型別，例如 `System.String`。|  
|`Output`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，則此參數是工作的輸出參數。 預設值為 `false`。|  
|`Required`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，則此參數是工作的必要參數。 預設值為 `false`。|  

### <a name="child-elements"></a>子元素  
 無。  

### <a name="parent-elements"></a>父元素  

|元素|描述|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|包含選擇性參數清單，將出現在 `UsingTask` `TaskFactory` 所產生的工作中。|  

## <a name="example"></a>範例  
 下列範例示範如何使用 `Parameter` 元素。  

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

## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
