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
ms.openlocfilehash: 1b7b36a829e2e406ecd3f10ba3a2b588c6f7df25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633755"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>如何：在多個專案檔中使用相同的目標

如果您已創作了多個 MSBuild 專案檔案，您可能發現需要在不同的專案檔案中使用相同的任務和目標。 您可以不在每個專案檔中包含這些工作或目標的完整描述，而是在一個個別的專案檔中儲存目標，然後將該專案匯入到任何其他需要使用該目標的專案中。
## <a name="use-the-import-element"></a>使用 Import 項目

 使用 `Import` 元素可將一個專案檔插入到另一個專案檔中。 正在導入的專案檔案必須是有效的 MSBuild 專案檔案，並且包含格式良好的 XML。 `Project` 屬性會指定所匯入之專案檔的路徑。 有關元素的詳細資訊，`Import`請參閱[導入元素 （MSBuild）。](../msbuild/import-element-msbuild.md)
使用 `Import` 元素可將一個專案檔插入到另一個專案檔中。 正在導入的專案檔案必須是有效的 MSBuild 專案檔案，並且包含格式良好的 XML。 `Project` 屬性會指定所匯入之專案檔的路徑。 有關元素的詳細資訊，`Import`請參閱[導入元素 （MSBuild）。](../msbuild/import-element-msbuild.md)

#### <a name="to-import-a-project"></a>匯入專案

1. 在匯入端專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。

2. 使用 `Import` 元素來匯入專案。 例如：

     `<Import Project="MyCommon.targets"/>`

3. 在 `Import` 元素之後，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。

## <a name="order-of-evaluation"></a>評估順序

 當 MSBuild`Import`到達元素時，導入的專案將有效地插入到`Import`元素位置的導入專案中。 因此，`Import` 元素的位置會影響屬性和項目的值。 請務必了解所匯入之專案所設定的屬性和項目，以及所匯入之專案所使用的屬性和項目。

 在組建專案時，會先評估所有屬性，然後才評估項目。 例如，以下 XML 定義導入的專案檔案*MyCommon.目標*：

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

 以下 XML 定義*MyApp.proj*，它導入*MyCommon.target：*

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

 由於專案是在`Name` *MyApp.proj*中定義該屬性後導入的，因此`Name`*MyCommon.target*中的定義將覆蓋*MyApp.proj*中的定義。 如果是在定義 Name 屬性之前就匯入專案，組建就會顯示下列訊息：

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>匯入專案時，請使用下列方法

1. 在專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。

2. 匯入專案。

3. 在專案檔中，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。

## <a name="example"></a>範例

 下面的代碼示例顯示了第二個代碼示例導入的*MyCommon.target*檔。 *.target*檔評估導入專案的屬性以配置生成。

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

 以下代碼示例導入*MyCommon.target*檔。

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>另請參閱

- [Import 項目 (MSBuild)](../msbuild/import-element-msbuild.md)
- [目標](../msbuild/msbuild-targets.md)
