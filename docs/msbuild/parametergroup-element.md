---
title: ParameterGroup 項目 | Microsoft Docs
description: 瞭解 MSBuild ParameterGroup 元素，其中包含 UsingTask TaskFactory 所產生之工作上的選擇性參數清單。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56ff9c63de40f6a352c10f92b937a397c683fc65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905300"
---
# <a name="parametergroup-element"></a>ParameterGroup 元素

包含選擇性的參數清單，這些參數將會出現在由產生的工作上 `UsingTask` `TaskFactory` 。 如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。

 \<Project> \<UsingTask>
 \<ParameterGroup>

## <a name="syntax"></a>Syntax

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
|[參數](../msbuild/parameter-element.md)|包含所產生之工作的特定參數相關資訊 `UsingTask` `TaskFactory` 。 項目的名稱是參數的名稱。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | 提供在 MSBuild 中註冊工作的方式。 專案中可能有零或多個 `UsingTask` 項目。 |

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
- [工作參考](../msbuild/msbuild-task-reference.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
