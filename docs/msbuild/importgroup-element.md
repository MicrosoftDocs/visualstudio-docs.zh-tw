---
title: ImportGroup 元素 | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56d3c301eb0e9b660a82b6552792a96aa5bd8596
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826584"
---
# <a name="importgroup-element"></a>ImportGroup 項目
  
包含群組在選擇性條件下方的 `Import` 元素集合。 如需詳細資訊，請參閱 [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)。

```xml
<Project>
  <ImportGroup>
```

## <a name="syntax"></a>語法

```xml
<ImportGroup Condition="'String A' == 'String B'">
    <Import ... />
    <Import ... />
</ImportGroup>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[Import](../msbuild/import-element-msbuild.md)|將某個專案檔的內容匯入至另一個專案檔。|

### <a name="parent-elements"></a>父元素

| 項目 | 描述 |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。 |

## <a name="example"></a>範例
 下列程式碼範例示範 `ImportGroup` 元素。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ImportGroup>
        <Import Project="$(Targets1.targets)" />
        <Import Project="$(Targets2.targets)" />
    </ImportGroup>
...
</Project>
```

## <a name="see-also"></a>請參閱

- [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
- [項目](../msbuild/msbuild-items.md)
