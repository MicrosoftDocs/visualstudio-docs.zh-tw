---
title: UsingTask (MSBuild) 的 Task 元素 |Microsoft Docs
description: 瞭解 MSBuild UsingTask 的 Task 元素，其中包含傳遞至 UsingTask TaskFactory 的資料。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 29259d71a610a4d83740c139c1309db477288004
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965989"
---
# <a name="task-element-of-usingtask-msbuild"></a>UsingTask (MSBuild) 的 Task 元素

包含傳遞至 `UsingTask` `TaskFactory` 的資料。 如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。

 \<Project> \<UsingTask>
 \<Task>

## <a name="syntax"></a>Syntax

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Evaluate`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，當具現化工作時，MSBuild 會評估所有內部元素，並且展開項目和屬性，然後才將資訊傳遞給 `TaskFactory`。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|資料|`Task` 標籤之間的文字會逐字傳送給 `TaskFactory`。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | 提供在 MSBuild 中註冊工作的方式。 專案中可能有零或多個 `UsingTask` 項目。 |

## <a name="example"></a>範例

 下列範例示範如何使用具有 `Evaluate` 屬性的 `Task` 項目。

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
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
