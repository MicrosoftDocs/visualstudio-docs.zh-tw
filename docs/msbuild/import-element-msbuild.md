---
title: Import 元素 (MSBuild) | Microsoft Docs
description: 瞭解 MSBuild 如何使用匯入專案，將某個專案檔的內容匯入至另一個專案檔。
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3a0d22019a0c7722b135392c53c7f9bfbcaab69
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914103"
---
# <a name="import-element-msbuild"></a>Import 項目 (MSBuild)

將某個專案檔的內容匯入至另一個專案檔。

\<Project>
\<Import>

## <a name="syntax"></a>Syntax

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Project`|必要屬性。<br /><br /> 要匯入之專案檔的路徑。 路徑可以包含萬用字元。 相符的檔案會依排序的順序進行匯入。 使用這項功能，只要將程式碼檔案新增至目錄，就可以將程式碼新增至專案。|
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|
|`Sdk`| 選擇性屬性。<br /><br /> 參考專案 SDK。|

### <a name="child-elements"></a>子元素

 無

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| - | - |
| [專案](../msbuild/project-element-msbuild.md) | MSBuild 專案檔的必要根項目。 |
| [ImportGroup](../msbuild/importgroup-element.md) | 包含群組在選擇性條件下方的 `Import` 項目集合。 |

## <a name="remarks"></a>備註

 使用 `Import` 項目，您可以重複使用通用於許多專案檔的程式碼。 因為您對共用程式碼的更新都會傳播至匯入它的所有專案，所以這可讓您更輕鬆地維護程式碼。

 依照慣例，共用的匯入專案檔會儲存為 *.targets* 檔案，但它們是標準的 MSBuild 專案檔。 MSBuild 不會讓您匯入副檔名不同的專案，但是建議您使用 *.targets* 副檔名以保持一致性。

 匯入專案中的相對路徑會相對於匯入專案的目錄進行解讀 (有一些例外狀況稍後會在此段落中說明) 。 因此，如果將專案檔匯入至不同位置中的數個專案檔，則針對每個匯入的專案，會以不同的方式解譯匯入之專案檔中的相對路徑。 有兩個例外狀況。 其中一個例外狀況是，在 `Import` 專案中，路徑一律會相對於包含專案的專案進行解讀 `Import` 。 另一個例外狀況是， `UsingTask` 一律會解讀 `AssemblyFile` 屬性相對於包含元素之檔案的相對路徑 `UsingTask` 。

 所有與專案檔相關的 MSBuild 保留屬性（例如 `MSBuildProjectDirectory` 和 `MSBuildProjectFile` ）都會根據匯入的專案檔指派值。

 如果匯入的專案沒有 `DefaultTargets` 屬性，則會依匯入順序來檢查匯入的專案，並使用第一個探索到之 `DefaultTargets` 屬性的值。 例如，如果 ProjectA 以該順序匯入 ProjectB 和 ProjectC () ，而 ProjectB imports ProjectD，MSBuild 會先 `DefaultTargets` 在 ProjectA、ProjectB、ProjectD 和最後 ProjectC 上尋找指定的。

 匯入之專案的結構描述與標準專案的結構描述完全相同。 雖然 MSBuild 可能會建立匯入的專案，但不太可能，因為匯入的專案通常不包含要設定的屬性或執行目標的順序的相關資訊。 匯入的專案取決於匯入它以提供該資訊的專案。

## <a name="wildcards"></a>萬用字元

 在 .NET Framework 4 中，MSBuild 允許在 Project 屬性中使用萬用字元。 有萬用字元時，會排序所有找到的相符項目 (適用於重現性)，然後依該順序進行匯入，就像已明確設定順序一樣。

 如果您想要提供擴充點，讓其他人可以匯入檔案，而不需要您將檔案名稱明確地新增至匯入檔案，則這非常好用。 基於此目的，*Microsoft.Common.Targets* 會在檔案頂端包含下行。

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>範例

 下列範例示範具有數個項目和屬性並匯入一般專案檔的專案。

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>另請參閱

- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
- [如何：使用多個專案檔內相同的目標](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
