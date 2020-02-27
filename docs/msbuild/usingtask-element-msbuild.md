---
title: UsingTask 元素 (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc50379563a85ce9c76f3d45b9d70c1f784eaf5a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631246"
---
# <a name="usingtask-element-msbuild"></a>UsingTask 元素 (MSBuild)

將 [Task](../msbuild/task-element-msbuild.md) 元素中參考的工作對應至包含工作實作的組件。

 \<Project> \<UsingTask>

## <a name="syntax"></a>語法

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> 與屬性和專案不同的是，將會使用套用至 `TaskName` 的*第一個*`UsingTask` 元素。若要覆寫工作，您必須在現有的 `UsingTask`*之前*定義新的。

## <a name="attributes-and-elements"></a>屬性和元素

 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`AssemblyName`|需要 `AssemblyName` 屬性或 `AssemblyFile` 屬性。<br /><br /> 要載入之組件的名稱。 `AssemblyName` 屬性接受強式名稱組件，雖然不需要強式名稱。 使用這個屬性就相當於使用 .NET 中的 <xref:System.Reflection.Assembly.Load%2A> 方法載入組件。<br /><br /> 如果使用 `AssemblyFile` 屬性，則您無法使用這個屬性。|
|`AssemblyFile`|需要 `AssemblyName` 或 `AssemblyFile` 屬性。<br /><br /> 組件的檔案路徑。 此屬性接受完整路徑或相對路徑。 相對路徑相對於專案檔案或目標檔案的目錄位置，其中會宣告 `UsingTask` 項目。 使用這個屬性就相當於使用 .NET 中的 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法載入組件。<br /><br /> 如果使用 `AssemblyName` 屬性，則您無法使用這個屬性。|
|`TaskFactory`|選擇性屬性。<br /><br /> 指定組件中的類別，該組件負責產生指定 `Task` 名稱的執行個體。  使用者也可以指定 `TaskBody` 做為子項目，工作 Factory 會接收並用來產生工作。 `TaskBody` 的內容專屬於工作 Factory。|
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
> 如果 `UsingTask` 元素來自已經向 MSBuild 引擎全域註冊的其中一個 *.tasks* 檔案，則專案層級屬性和項目沒有任何意義。 專案層級值對 MSBuild 而言不是全域的。

 在 MSBuild 4.0 中，使用工作可以從 *.overridetask* 檔案載入。

## <a name="example"></a>範例

 下列範例示範如何使用具有 `UsingTask` 屬性的 `AssemblyName` 項目。

```xml
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

 下列範例示範如何使用具有 `UsingTask` 屬性的 `AssemblyFile` 項目。

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
