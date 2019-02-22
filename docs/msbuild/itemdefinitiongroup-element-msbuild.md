---
title: ItemDefinitionGroup 元素 (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d88c8197cc93a2c898ecbf19d52127061b73604
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936573"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup 元素 (MSBuild)
`ItemDefinitionGroup` 元素可讓您定義一組項目定義，這些項目定義預設為套用至專案中所有項目的中繼資料值。 ItemDefinitionGroup 可取代使用 [CreateItem 工作](../msbuild/createitem-task.md)和 [CreateProperty 工作](../msbuild/createproperty-task.md)的需求。 如需詳細資訊，請參閱[項目定義](../msbuild/item-definitions.md)。

\<Project>  
\<ItemDefinitionGroup>

## <a name="syntax"></a>語法

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>屬性和元素
下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Condition`|選擇性屬性。 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|定義建置程序的輸入。 `ItemDefinitionGroup` 中可能有零或多個 `Item` 項目。|

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。 |

## <a name="example"></a>範例
下列程式碼範例會定義 ItemDefinitionGroup 中的兩個中繼資料項目，m 和 n。 在此範例中，預設中繼資料 "m" 會套用至項目 "i"，因為項目 "i" 未明確定義中繼資料 "m"。 不過，預設中繼資料 "n" 不會套用至項目 "i"，因為項目 "i" 已經定義中繼資料 "n"。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>另請參閱
[專案檔結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
[項目](../msbuild/msbuild-items.md)
