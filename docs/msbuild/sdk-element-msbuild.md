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
ms.openlocfilehash: 8c65bafd9183c97efa7595c10d7bdb3641c5f75f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595133"
---
# <a name="sdk-element-msbuild"></a>Sdk 元素 (MSBuild)
參考 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案 SDK。

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

| 項目 | 描述 |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。 |

## <a name="see-also"></a>請參閱
- [如何：參考 MSBuild 專案 SDK](../msbuild/how-to-use-project-sdk.md)
- [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)
- [ MSBuild](../msbuild/msbuild.md)
