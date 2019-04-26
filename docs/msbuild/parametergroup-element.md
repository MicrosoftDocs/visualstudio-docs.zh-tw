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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d10b2e08b6e3f3c94c0a1f0cc1c24d239675c53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999781"
---
# <a name="parametergroup-element"></a>ParameterGroup 元素
包含選擇性參數清單，將出現在 `UsingTask` `TaskFactory` 所產生的工作中。 如需詳細資訊，請參閱 [UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)。

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

|元素|說明|
|-------------|-----------------|
|[Parameter](../msbuild/parameter-element.md)|包含 `UsingTask` `TaskFactory` 所產生之工作的特定參數相關資訊。 元素的名稱是參數的名稱。|

### <a name="parent-elements"></a>父元素

| 元素 | 說明 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | 提供一種方式，在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中登錄工作。 專案中可能有零或多個 `UsingTask` 項目。 |

## <a name="example"></a>範例
 下列範例示範如何使用 `ParameterGroup` 元素。

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>另請參閱
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
