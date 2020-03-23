---
title: Sdk 元素 (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a704744032c5dea70246463a816ba8e1f5c84e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632468"
---
# <a name="sdk-element-msbuild"></a>Sdk 元素 (MSBuild)

引用 MSBuild 專案 SDK。

 \<Project> \<SDK>

## <a name="syntax"></a>語法

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Name`|必要屬性。<br /><br /> 專案 SDK 的名稱。|
|`Version`|選擇性屬性。<br /><br /> 專案 SDK 的版本|

### <a name="child-elements"></a>子元素

 無。

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔案所需的根項目。 |

## <a name="see-also"></a>另請參閱

- [如何：參考 MSBuild 專案 SDK](../msbuild/how-to-use-project-sdk.md)
- [專案檔案架構引用](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
