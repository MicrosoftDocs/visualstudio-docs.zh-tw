---
title: Parameter 元素 | Microsoft Docs
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
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c53528159d2950378c56e1da22d81393235f716
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803378"
---
# <a name="parameter-element"></a>Parameter 元素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
包含 `UsingTask``TaskFactory` 所產生之工作的特定參數相關資訊。  元素的名稱是參數的名稱。  如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  
  
## <a name="syntax"></a>語法  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`ParameterType`|選擇性屬性。<br /><br /> 參數的 .NET 型別，例如 "System.String"。|  
|`Output`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，則此參數是工作的輸出參數。 預設值為 `false`。|  
|`Required`|選擇性的布林值屬性。<br /><br /> 如果為 `true`，則此參數是工作的必要參數。 根據預設，該值為 `false`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|包含選擇性參數清單，將出現在 `UsingTask``TaskFactory` 所產生的工作中。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `Parameter` 元素。  
  
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
