---
title: Output 元素 (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 327f65ef6639f444326d59d6db990e9c732a760f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790279"
---
# <a name="output-element-msbuild"></a>Output 元素 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
在項目或屬性中儲存工作輸出值。  
  
 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  
  
## <a name="syntax"></a>語法  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`TaskParameter`|必要屬性。<br /><br /> 工作的輸出參數名稱。|  
|`PropertyName`|需要 `PropertyName` 或 `ItemName` 屬性。<br /><br /> 接收工作輸出參數值的屬性。 然後您的專案即可用 `$(`*PropertyName*`)` 語法來參考該屬性。 此屬性名稱可以是新的屬性名稱，或是已經在專案中定義的名稱。<br /><br /> 如果同時也使用 `ItemName`，就不能使用這個屬性。|  
|`ItemName`|需要 `PropertyName` 或 `ItemName` 屬性。<br /><br /> 接收工作輸出參數值的項目。 然後您的專案即可用 `@(`*ItemName*`)` 語法來參考該項目。 項目名稱可以是新的項目名稱，或是已經在專案中定義的名稱。<br /><br /> 如果同時也使用 `PropertyName`，就不能使用這個屬性。|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|建立並執行 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 工作的執行個體。|  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，示範了在 `Target` 元素內執行的 `Csc` 工作。 傳遞至工作參數的項目和屬性，都在此範例範圍外宣告。 輸出參數 `OutputAssembly` 的值儲存在 `FinalAssemblyName` 項目中，而來自輸出參數 `BuildSucceeded` 的值則儲存在 `BuildWorked` 屬性中。 如需詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>請參閱  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)
