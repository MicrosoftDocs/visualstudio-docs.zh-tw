---
title: Parameter 元素 | Microsoft Docs
description: 瞭解 MSBuild Parameter 元素，其中包含 UsingTask TaskFactory 所產生之工作的特定參數相關資訊。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 728618a6d9ff174d4d4bf7cdc20516433d06036b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918869"
---
# <a name="parameter-element"></a>Parameter 元素

包含所產生之工作的特定參數相關資訊 `UsingTask` `TaskFactory` 。  項目的名稱是參數的名稱。  如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。

 \<Project> \<UsingTask>
 \<ParameterGroup>
 \<Parameter>

## <a name="syntax"></a>Syntax

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`ParameterType`|選擇性屬性。<br /><br /> 參數的 .NET 型別，例如 `System.String`。|
|`Output`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，則此參數是工作的輸出參數。 根據預設，此值是 `false`。|
|`Required`|選擇性的 Boolean 屬性。<br /><br /> 如果為 `true`，則此參數是工作的必要參數。 根據預設，此值是 `false`。|

### <a name="child-elements"></a>子元素

 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|包含選擇性的參數清單，這些參數將會出現在由產生的工作上 `UsingTask` `TaskFactory` 。|

## <a name="example"></a>範例

 下列範例示範如何使用 `Parameter` 元素。

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
