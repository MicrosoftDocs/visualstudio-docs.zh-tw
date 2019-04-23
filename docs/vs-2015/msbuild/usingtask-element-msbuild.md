---
title: UsingTask 元素 (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 95e0d070bb69bd6918025298f865236a382d16e0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669038"
---
# <a name="usingtask-element-msbuild"></a>UsingTask 項目 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將 [Task](../msbuild/task-element-msbuild.md) 元素中參考的工作對應至包含工作實作的組件。  
  
 \<Project>  
 \<UsingTask>  
  
## <a name="syntax"></a>語法  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`AssemblyName`|需要 `AssemblyName` 屬性或 `AssemblyFile` 屬性。<br /><br /> 要載入之組件的名稱。 `AssemblyName` 屬性接受強式名稱組件，雖然不需要強式名稱。 使用這個屬性就相當於使用 .NET 中的 <xref:System.Reflection.Assembly.Load%2A> 方法載入組件。<br /><br /> 如果使用 `AssemblyFile` 屬性，則您無法使用這個屬性。|  
|`AssemblyFile`|需要 `AssemblyName` 或 `AssemblyFile` 屬性。<br /><br /> 組件的檔案路徑。 此屬性接受完整路徑或相對路徑。 相對路徑相對於專案檔案或目標檔案的目錄位置，其中會宣告 `UsingTask` 項目。 使用這個屬性就相當於使用 .NET 中的 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法載入組件。<br /><br /> 如果使用 `AssemblyName` 屬性，則您無法使用這個屬性。|  
|`TaskFactory`|選擇性屬性。<br /><br /> 指定組件中的類別，該組件負責產生指定 `Task` 名稱的執行個體。  使用者也可以指定 `TaskBody` 做為子項目，工作 Factory 會接收並用來產生工作。 `TaskBody` 的內容專屬於工作 Factory。|  
|`TaskName`|必要屬性。<br /><br /> 從組件參考之工作的名稱。 如果可能會有模稜兩可的情況，這個屬性應該一律指定完整的命名空間。 如果有模稜兩可的情況，MSBuild 會選擇任意的相符項目，這樣可能會產生非預期的結果。|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|說明|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|在指定的 `TaskFactory` 產生之工作上顯示的參數集。|  
|[Task](../msbuild/task-element-msbuild.md)|傳遞至 `TaskFactory` 以產生工作之執行個體的資料。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|說明|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 專案檔案的必要根項目。|  
  
## <a name="remarks"></a>備註  
 如果明確或透過匯入的專案檔案出現在專案檔案中，則可以在 `UsingTask` 項目的任何位置參考環境變數、命令列屬性和專案層級屬性。 如需詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。  
  
> [!NOTE]
>  如果 `UsingTask` 項目來自全域註冊 MSBuild 引擎的其中一個 .tasks 檔案，則專案層級屬性沒有任何意義。 專案層級屬性對於 MSBuild 而言不是全域的。  
  
 在 MSBuild 4.0 中，可以從 .overridetask 檔案載入使用的工作。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用具有 `AssemblyName` 屬性的 `UsingTask` 項目。  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用具有 `AssemblyFile` 屬性的 `UsingTask` 項目。  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
