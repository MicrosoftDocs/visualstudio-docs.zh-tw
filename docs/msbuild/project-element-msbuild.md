---
title: Project 項目 (MSBuild) | Microsoft Docs
description: 深入瞭解 MSBuild 專案檔的必要根項目，這是 msbuild 專案檔的必要元素。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4aa00df0a1a0b622040a3f808515b9a62fc8f66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918831"
---
# <a name="project-element-msbuild"></a>Project 元素 (MSBuild)

MSBuild 專案檔的必要根項目。

## <a name="syntax"></a>Syntax

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

| 屬性 | 描述 |
|------------------------| - |
| `DefaultTargets` | 選擇性屬性。<br /><br /> 如果未指定任何目標，則為一或多個做為組建進入點的預設目標。 請以分號 (;) 來分隔多個目標。<br /><br /> 如果未在 `DefaultTargets` 屬性或 MSBuild 命令列中指定預設目標，則引擎會在評估匯 [入](../msbuild/import-element-msbuild.md) 元素之後，執行專案檔中的第一個目標。 |
| `InitialTargets` | 選擇性屬性。<br /><br /> 要在 `DefaultTargets` 屬性中或命令列上指定目標之前執行的一或多個初始目標。 請以分號 (`;`) 來分隔多個目標。 如果多個匯入的檔案定義 `InitialTargets`，則提到的所有目標都會按照進行匯入的順序執行。 |
| `Sdk` | 選擇性屬性。 <br /><br /> 要用來建立隱含 Import 陳述式 (會將它新增至 .proj 檔案) 的 SDK 名稱和選擇性版本。 如果未指定版本，MSBuild 會嘗試解析預設版本。  例如，`<Project Sdk="Microsoft.NET.Sdk" />` 或 `<Project Sdk="My.Custom.Sdk/1.0.0" />`。 |
| `ToolsVersion` | 選擇性屬性。<br /><br /> MSBuild 用來判斷 $(MSBuildBinPath) 和 $(MSBuildToolsPath) 之值的工具組版本。 |
| `TreatAsLocalProperty` | 選擇性屬性。<br /><br /> 將不會被視為全域的屬性名稱。 這個屬性可防止特定的命令列屬性覆寫專案檔或目標檔案及所有後續匯入中設定的屬性值。 請以分號 (;) 來分隔多個屬性。<br /><br /> 一般來說，全域屬性值會覆寫專案檔或目標檔案中所設定的屬性值。 如果此屬性列於 `TreatAsLocalProperty` 值中，則全域屬性值不會覆寫該檔案及任何後續匯入中所設定的屬性值。 如需詳細資訊，請參閱[如何：使用不同選項來建置相同的原始程式檔](../msbuild/how-to-build-the-same-source-files-with-different-options.md)。 **注意︰** 您可以使用 **-property** (或 **-p**) 參數，在命令提示字元中設定全域屬性。 您也可以使用 MSBuild 工作的 `Properties` 屬性，針對多專案組建中的子專案設定或修改全域屬性。 如需詳細資訊，請參閱 [MSBuild](../msbuild/msbuild-task.md)工作。 |
| `xmlns` | 選擇性屬性。<br /><br /> 指定時，`xmlns` 屬性的值必須為 `http://schemas.microsoft.com/developer/msbuild/2003`。 |

### <a name="child-elements"></a>子元素

| 元素 | 描述 |
| - | - |
| [選擇](../msbuild/choose-element-msbuild.md) | 選擇性項目。<br /><br /> 評估子項目，以選取一組要評估的 `ItemGroup` 項目和/或 `PropertyGroup` 項目。 |
| [匯入](../msbuild/import-element-msbuild.md) | 選擇性項目。<br /><br /> 可讓專案檔案匯入另一個專案檔。 專案中可能有零或多個 `Import` 項目。 |
| [ImportGroup](../msbuild/importgroup-element.md) | 選擇性項目。<br /><br /> 包含群組在選擇性條件下方的 `Import` 元素集合。 |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | 選擇性項目。<br /><br /> 個別項目 (Item) 的群組項目 (Element)。 使用 [Item](../msbuild/item-element-msbuild.md) 項目 (Element) 來指定項目 (Item)。 專案中可能有零或多個 `ItemGroup` 項目。 |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | 選擇性項目。<br /><br /> 可讓您定義一組項目定義，這些項目定義預設為套用至專案中所有項目的中繼資料值。 ItemDefinitionGroup 可取代使用 `CreateItem` 工作和 `CreateProperty` 工作的需求。 |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | 選擇性項目。<br /><br /> 提供在 MSBuild 專案檔中保存非 MSBuild 資訊的方式。 專案中可能有零或一個 `ProjectExtensions` 項目。 |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | 選擇性項目。<br /><br /> 個別屬性的群組項目。 使用 [Property](../msbuild/property-element-msbuild.md) 項目來指定屬性。 專案中可能有零或多個 `PropertyGroup` 項目。 |
| [Sdk](../msbuild/sdk-element-msbuild.md) | 選擇性項目。<br /><br /> 參考 MSBuild 專案 SDK。  此元素可用來當做 Sdk 屬性的替代方案。 |
| [Target](../msbuild/target-element-msbuild.md) | 選擇性項目。<br /><br /> 包含 MSBuild 依序執行的一組工作。 使用 [Item](../msbuild/task-element-msbuild.md) 項目來指定工作。 專案中可能有零或多個 `Target` 項目。 |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | 選擇性項目。<br /><br /> 提供在 MSBuild 中註冊工作的方式。 專案中可能有零或多個 `UsingTask` 項目。 |

### <a name="parent-elements"></a>父元素

 無。

## <a name="see-also"></a>另請參閱

- [如何：指定要先建立的目標](../msbuild/how-to-specify-which-target-to-build-first.md)
- [命令列參考](../msbuild/msbuild-command-line-reference.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
