---
title: ProjectExtensions 項目 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuildProjectExtensions 元素，這可讓 MSBuild 專案檔包含非 MSBuild 資訊。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7b186fa1d7a5ecb8297045d4b0bbb111d136d1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905291"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions 元素 (MSBuild)

允許 MSBuild 專案檔包含非 MSBuild 資訊。 `ProjectExtensions`MSBuild 會忽略元素內的任何專案。

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Syntax

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

 無

### <a name="child-elements"></a>子元素

 無

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔的必要根項目。 |

## <a name="remarks"></a>備註

 `ProjectExtensions`MSBuild 專案中只能使用一個元素。

## <a name="example"></a>範例

 下列程式碼範例會顯示來自整合式開發環境中且儲存於 `ProjectExtensions` 項目內的資訊。

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>另請參閱

- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
