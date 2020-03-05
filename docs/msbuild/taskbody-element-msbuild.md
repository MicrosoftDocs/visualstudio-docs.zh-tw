---
title: UsingTask 的 Task 元素（MSBuild） |Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263184"
---
# <a name="task-element-of-usingtask-msbuild"></a>UsingTask 的 Task 元素（MSBuild）

包含傳遞至 `UsingTask` `TaskFactory`的資料。 如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。

 \<專案 > \<UsingTask > \<工作 >

## <a name="syntax"></a>語法

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Evaluate`|選擇性的布林值屬性。<br /><br /> 如果為 `true`，當具現化工作時，MSBuild 會評估所有內部元素，並且展開項目和屬性，然後才將資訊傳遞給 `TaskFactory`。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|資料|`Task` 標籤之間的文字會逐字傳送給 `TaskFactory`。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | 提供在 MSBuild 中註冊工作的方式。 專案中可能有零或多個 `UsingTask` 項目。 |

## <a name="example"></a>範例

 下列範例示範如何使用具有 `Task` 屬性的 `Evaluate` 項目。

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
