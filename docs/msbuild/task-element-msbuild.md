---
title: 目標 (MSBuild) 的 Task 元素 |Microsoft Docs
description: 瞭解 MSBuild 目標的工作專案，它會建立並執行 MSBuild 工作的實例。
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
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4b8e3cb3acccc2e7ae4c6c2d93353bec79a3690
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966041"
---
# <a name="task-element-of-target-msbuild"></a>目標 (MSBuild) 的 Task 元素

建立並執行 MSBuild 工作的實例。 元素名稱取決於所建立之工作的名稱。

 \<Project> \<Target>

## <a name="syntax"></a>Syntax

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Condition`|選擇性屬性。 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|
|`ContinueOnError`|選擇性屬性。 可包含一或多個下列值：<br /><br /> -   **WarnAndContinue** 或 **true**。 當工作失敗時， [目標](../msbuild/target-element-msbuild.md) 專案和組建中的後續工作會繼續執行，並將工作中的所有錯誤視為警告。<br />-   **ErrorAndContinue**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。<br />-   **ErrorAndStop** 或 **false** (預設) 。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。<br /><br /> 只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../msbuild/how-to-ignore-errors-in-tasks.md)。|
|`Parameter`|如果工作類別包含一或多個使用 `[Required]` 屬性 (Attribute) 標記的屬性 (Property)，則為必要項目。<br /><br /> 使用者定義的工作參數，其中包含參數值當作它的值。 `Task` 元素中可以有任意數量的參數，而每個屬性 (Attribute) 會對應到工作類別的 .NET 屬性 (Property)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[輸出](../msbuild/output-element-msbuild.md)|在專案檔中儲存工作的輸出。 工作中可能有零或多個 `Output` 元素。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [Target](../msbuild/target-element-msbuild.md) | MSBuild 工作的容器元素。 |

## <a name="remarks"></a>備註

 `Task`MSBuild 專案檔中的專案會建立工作的實例、設定它的屬性，然後執行它。 `Output` 元素會在專案檔中其他地方會使用的屬性或項目中儲存輸出參數。

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

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
