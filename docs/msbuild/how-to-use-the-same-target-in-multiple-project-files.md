---
title: 如何：在多個專案檔中使用相同的目標 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bc8f3c95c687244162cb3bd977ca40031cd8f39
ms.sourcegitcommit: ddd99f64a3f86508892a6d61e8a33c88fb911cc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82255568"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>如何：在多個專案檔中使用相同的目標

如果您已撰寫數個 MSBuild 專案檔，您可能會發現需要在不同的專案檔中使用相同的工作和目標。 您可以不在每個專案檔中包含這些工作或目標的完整描述，而是在一個個別的專案檔中儲存目標，然後將該專案匯入到任何其他需要使用該目標的專案中。

## <a name="use-the-import-element"></a>使用 Import 項目

使用 `Import` 元素可將一個專案檔插入到另一個專案檔中。 匯入的專案檔必須是有效的 MSBuild 專案檔，且包含格式正確的 XML。 `Project` 屬性會指定所匯入之專案檔的路徑。 如需元素的`Import`詳細資訊，請參閱[Import 元素（MSBuild）](../msbuild/import-element-msbuild.md)。

#### <a name="to-import-a-project"></a>匯入專案

1. 在匯入端專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。

2. 使用 `Import` 元素來匯入專案。 例如：

     `<Import Project="MyCommon.targets"/>`

3. 在 `Import` 元素之後，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。

## <a name="order-of-evaluation"></a>評估順序

 當 MSBuild 到達`Import`元素時，匯入的專案會有效地插入至匯入專案的`Import`元素位置。 因此，`Import` 元素的位置會影響屬性和項目的值。 請務必了解所匯入之專案所設定的屬性和項目，以及所匯入之專案所使用的屬性和項目。

 在組建專案時，會先評估所有屬性，然後才評估項目。 例如，下列 XML 會定義匯入的專案檔*mycommon.targets*：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 下列 XML 定義了*MyApp. proj*，它會匯入*mycommon.targets*：

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 在組建專案時，會顯示下列訊息：

 `Name="MyCommon"`

 因為專案是在*myapp. proj*中`Name`定義屬性之後匯入，所以*mycommon.targets* `Name`中的定義會覆寫*myapp. proj*中的定義。 如果是在定義 Name 屬性之前就匯入專案，組建就會顯示下列訊息：

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>匯入專案時，請使用下列方法

1. 在專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。

2. 匯入專案。

3. 在專案檔中，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。

## <a name="example"></a>範例

 下列程式碼範例顯示第二個程式碼範例匯入的*mycommon.targets*檔案。 *.Targets*檔案會評估來自匯入專案的屬性以設定組建。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example"></a>範例

 下列程式碼範例會匯入*mycommon.targets*檔案。

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>請參閱

- [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)
- [目標](../msbuild/msbuild-targets.md)
