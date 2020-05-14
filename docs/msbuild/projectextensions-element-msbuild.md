---
title: ProjectExtensions 項目 (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94f2d88aa19bf01ebe6f25c7d80772c812abcc59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632962"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions 元素 (MSBuild)

允許 MSBuild 專案檔案包含非 MSBuild 資訊。 MSBuild 將`ProjectExtensions`忽略元素內部的任何內容。

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>語法

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

 None

### <a name="child-elements"></a>子元素

 None

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔案所需的根項目。 |

## <a name="remarks"></a>備註

 在`ProjectExtensions`MSBuild 專案中只能使用一個元素。

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

- [專案檔案架構引用](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
