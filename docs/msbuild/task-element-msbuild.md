---
title: Task 元素 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc67d881f48c99cd8e53de086f0c8b08c96d7844
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="task-element-msbuild"></a>Task 項目 (MSBuild)
建立並執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作的執行個體。 元素名稱取決於所建立之工作的名稱。  

 \<Project>  
 \<Target>  

## <a name="syntax"></a>語法  

```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  

## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`Condition`|選擇性屬性。 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
|`ContinueOnError`|選擇性屬性。 可包含一或多個下列值：<br /><br /> -   **WarnAndContinue** 或 **true**。 當工作失敗時，[Target](../msbuild/target-element-msbuild.md) 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為警告。<br />-   **ErrorAndContinue**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。<br />-   **ErrorAndStop** 或 **false** (預設值)。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。<br /><br /> 只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../msbuild/how-to-ignore-errors-in-tasks.md)。|  
|`Parameter`|如果工作類別包含一或多個使用 `[Required]` 屬性 (Attribute) 標記的屬性 (Property)，則為必要項目。<br /><br /> 使用者定義的工作參數，其中包含參數值當作它的值。 `Task` 元素中可以有任意數量的參數，而每個屬性 (Attribute) 會對應到工作類別的 .NET 屬性 (Property)。|  

### <a name="child-elements"></a>子元素  

|元素|描述|  
|-------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|在專案檔中儲存工作的輸出。 工作中可能有零或多個 `Output` 元素。|  

### <a name="parent-elements"></a>父項目  

|元素|描述|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作的容器元素。|  

## <a name="remarks"></a>備註  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔中的 `Task` 元素會建立工作的執行個體，設定屬性，然後執行它。 `Output` 元素會在專案檔中其他地方會使用的屬性或項目中儲存輸出參數。  

 如果工作的父 `Target` 元素中有任何 [OnError](../msbuild/onerror-element-msbuild.md) 元素，則當工作失敗且 `ContinueOnError` 的值為 `false` 時，仍然會評估那些元素。 如需工作的詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。  

## <a name="example"></a>範例  
 下列程式碼範例會建立 [Csc 工作](../msbuild/csc-task.md)類別的執行個體，設定其中六個屬性，然後執行工作。 執行之後，物件的 `OutputAssembly` 屬性值會放入名稱為 `FinalAssemblyName` 的項目清單。  

```xml  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
