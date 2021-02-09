---
title: OnError 元素 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuild 如何使用 OnError 元素，讓一個或多個目標執行（如果失敗工作的 ContinueOnError 屬性為 false）。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 574f49b65f47b4a22240ca68b4d74c90ee580a15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905336"
---
# <a name="onerror-element-msbuild"></a>OnError 元素 (MSBuild)

如果失敗工作的 `ContinueOnError` 屬性是 `false`，則會執行一或多個目標。

 \<Project> \<Target>
 \<OnError>

## <a name="syntax"></a>Syntax

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|
|`ExecuteTargets`|必要屬性。<br /><br /> 工作失敗時要執行的目標。 以分號分隔多個目標。 多個目標會以指定的順序執行。|

### <a name="child-elements"></a>子元素

 無。

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [Target](../msbuild/target-element-msbuild.md) | MSBuild 工作的容器元素。 |

## <a name="remarks"></a>備註

 如果專案的 `OnError` 其中一個 `Target` 工作因為 `ContinueOnError` 屬性設定為 `ErrorAndStop` (或) 而失敗 `false` ，則 MSBuild 會執行元素。 工作失敗時，便會執行 `ExecuteTargets` 屬性指定的目標。 如果目標中有多個 `OnError` 元素，則工作失敗時會依序執行 `OnError` 元素。

 如需 `ContinueOnError` 屬性的相關資訊，請參閱 [Task 元素 (MSBuild)](../msbuild/task-element-msbuild.md)。 如需目標的詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。

## <a name="example"></a>範例

 下列程式碼會執行 `TaskOne` 和 `TaskTwo` 工作。 如果 `TaskOne` 失敗，MSBuild 會評估 `OnError` 元素並執行 `OtherTarget` 目標。

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>另請參閱

- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
- [目標](../msbuild/msbuild-targets.md)
