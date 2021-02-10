---
title: UsingTask 元素 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuild UsingTask 元素，此專案會將工作專案中參考的工作對應至包含工作執行的元件。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3adc3d648e73fc1f3596cc7a5c2cb2148a8f611b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960334"
---
# <a name="usingtask-element-msbuild"></a>UsingTask 元素 (MSBuild)

將 [Task](../msbuild/task-element-msbuild.md) 元素中參考的工作對應至包含工作實作的組件。

 \<Project> \<UsingTask>

## <a name="syntax"></a>Syntax

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> 與屬性和專案不同，  `UsingTask` 將會使用套用至的第一個專案 `TaskName` ; 若要覆寫工作，您必須在現有的專案之前定義新的 `UsingTask`  。

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Architecture`|選擇性屬性。<br /><br /> 指定工作必須在指定位數的進程中執行。 如果目前的進程不符合需求，則工作將會在執行的工作主機進程中執行。<br /><br /> 支援的值為 `x86` (32 位) 、 `x64` (64 位) 、 `CurrentArchitecture` 和 `*` (任何架構) 。|  
|`AssemblyName`|需要 `AssemblyName` 屬性或 `AssemblyFile` 屬性。<br /><br /> 要載入之組件的名稱。 `AssemblyName` 屬性接受強式名稱組件，雖然不需要強式名稱。 使用這個屬性就相當於使用 .NET 中的 <xref:System.Reflection.Assembly.Load%2A> 方法載入組件。<br /><br /> 如果使用 `AssemblyFile` 屬性，則您無法使用這個屬性。|
|`AssemblyFile`|需要 `AssemblyName` 或 `AssemblyFile` 屬性。<br /><br /> 組件的檔案路徑。 此屬性接受完整路徑或相對路徑。 相對路徑相對於專案檔案或目標檔案的目錄位置，其中會宣告 `UsingTask` 項目。 使用這個屬性就相當於使用 .NET 中的 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法載入組件。<br /><br /> 如果使用 `AssemblyName` 屬性，則您無法使用這個屬性。|
|`Runtime`|選擇性屬性。<br /><br /> 指定工作必須在指定版本的 .NET Framework 執行時間中執行。 如果目前的進程不符合需求，則工作將會在執行的工作主機進程中執行。 不支援 .NET Core MSBuild。<br /><br /> 支援的值為 `CLR2` ( .NET Framework 3.5) 、 `CLR4` ( .NET Framework 4.7.2 或更高版本) 、 `CurrentRuntime` 和 `*` (任何執行時間) 。|  
|`TaskFactory`|選擇性屬性。<br /><br /> 指定組件中的類別，該組件負責產生指定 `Task` 名稱的執行個體。  使用者也可以指定 `Task` 做為子項目，工作 Factory 會接收並用來產生工作。 `Task` 的內容專屬於工作 Factory。|
|`TaskName`|必要屬性。<br /><br /> 從組件參考之工作的名稱。 如果可能會有模稜兩可的情況，這個屬性應該一律指定完整的命名空間。 如果有模稜兩可的情況，MSBuild 會選擇任意的相符項目，這樣可能會產生非預期的結果。|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|在指定的 `TaskFactory` 產生之工作上顯示的參數集。|
|[Task](../msbuild/task-element-msbuild.md)|傳遞至 `TaskFactory` 以產生工作之執行個體的資料。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔的必要根項目。 |

## <a name="remarks"></a>備註

 您可以在專案檔所包含 (直接包含或透過匯入的專案檔來包含) 的 `UsingTask` 元素中，參考環境變數、命令列屬性、專案層級屬性及專案層級項目。 如需詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。

> [!NOTE]
> 專案層級屬性和專案沒有任何意義，亦 `UsingTask` 即，如果元素來自全域向 MSBuild 引擎註冊的其中一個工作 *檔案。* 專案層級值對 MSBuild 而言不是全域的。

 在 MSBuild 4.0 中，使用工作可以從 *.overridetask* 檔案載入。

第一次使用時，會載入包含自訂工作的元件 `Task` 。

## <a name="example-1"></a>範例 1

 下列範例示範如何使用具有 `AssemblyName` 屬性的 `UsingTask` 項目。

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example-2"></a>範例 2

 下列範例示範如何使用具有 `AssemblyFile` 屬性的 `UsingTask` 項目。

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [如何：設定目標和工作](../msbuild/how-to-configure-targets-and-tasks.md)   
- [工作參考](../msbuild/msbuild-task-reference.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
