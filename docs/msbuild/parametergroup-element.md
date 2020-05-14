---
title: ParameterGroup 項目 | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c06b9c530d3fff0fdfa429df633daaa4dde8c52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263069"
---
# <a name="parametergroup-element"></a>ParameterGroup 元素

包含將在 由`UsingTask``TaskFactory`生成的任務上存在的參數的可選清單。 如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。

 \<Project> \<UsingTask> \<ParameterGroup>

## <a name="syntax"></a>語法

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[參數](../msbuild/parameter-element.md)|包含有關 由 生成的`UsingTask``TaskFactory`任務的特定參數的資訊。 項目的名稱是參數的名稱。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | 提供了一種在 MSBuild 中註冊任務的方法。 專案中可能有零或多個 `UsingTask` 項目。 |

## <a name="example"></a>範例

 下列範例示範如何使用 `ParameterGroup` 元素。

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
- [任務引用](../msbuild/msbuild-task-reference.md)
- [專案檔案架構引用](../msbuild/msbuild-project-file-schema-reference.md)
