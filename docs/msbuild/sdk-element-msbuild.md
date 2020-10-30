---
title: Sdk 元素 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuild Sdk 元素（參考 MSBuild 專案 SDK）的語法、屬性和元素。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b348cf2af76c439a28bbb58c0050cc3d458d5457
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048364"
---
# <a name="sdk-element-msbuild"></a>Sdk 元素 (MSBuild)

參考 MSBuild 專案 SDK。

 \<Project> \<Sdk>

## <a name="syntax"></a>Syntax

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
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔的必要根項目。 |

## <a name="see-also"></a>請參閱

- [如何：參考 MSBuild 專案 SDK](../msbuild/how-to-use-project-sdk.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
