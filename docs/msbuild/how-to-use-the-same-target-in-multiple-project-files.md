---
title: 如何：在多個專案檔中使用相同的目標 | Microsoft Docs
description: 瞭解如何將目標儲存在 MSBuild 專案檔中，然後將它匯入至任何其他需要使用目標的專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5c351b7f676dec678bd4f070a1f8fb9af97c5d28
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914116"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>如何：在多個專案檔中使用相同的目標

如果您已經撰寫數個 MSBuild 專案檔，您可能發現您需要在不同的專案檔中使用相同的工作和目標。 您可以不在每個專案檔中包含這些工作或目標的完整描述，而是在一個個別的專案檔中儲存目標，然後將該專案匯入到任何其他需要使用該目標的專案中。

## <a name="use-the-import-element"></a>使用 Import 項目

使用 `Import` 元素可將一個專案檔插入到另一個專案檔中。 正在匯入的專案檔必須是有效的 MSBuild 專案檔，並且包含格式正確的 XML。 `Project` 屬性會指定所匯入之專案檔的路徑。 如需專案的詳細資訊 `Import` ，請參閱 [ (MSBuild) 的匯入元素 ](../msbuild/import-element-msbuild.md)。

#### <a name="to-import-a-project"></a>匯入專案

1. 在匯入端專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。

2. 使用 `Import` 元素來匯入專案。 例如：

     `<Import Project="MyCommon.targets"/>`

3. 在 `Import` 元素之後，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。

## <a name="order-of-evaluation"></a>評估順序

 當 MSBuild 到達某個專案時 `Import` ，匯入的專案實際上會插入專案位置的匯入專案中 `Import` 。 因此，`Import` 元素的位置會影響屬性和項目的值。 請務必了解所匯入之專案所設定的屬性和項目，以及所匯入之專案所使用的屬性和項目。

 在組建專案時，會先評估所有屬性，然後才評估項目。 例如，下列 XML 定義匯入的專案檔 *>mycommon.targets*：

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

 下列 XML 定義 *MyApp*，它會匯入 *>mycommon.targets*：

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

 因為專案是在 Myapp 中定義屬性之後匯入 `Name` ， 所以 >mycommon.targets 中的定義會 `Name` 覆寫 *myapp* 中的定義。 如果是在定義 Name 屬性之前就匯入專案，組建就會顯示下列訊息：

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>匯入專案時，請使用下列方法

1. 在專案檔中，定義用來作為所匯入專案中屬性和項目之參數的所有屬性和項目。

2. 匯入專案。

3. 在專案檔中，定義必須覆寫所匯入專案中預設屬性和項目定義的所有屬性和項目。

## <a name="example-1"></a>範例 1

 下列程式碼範例顯示第二個程式碼範例匯入的 *>mycommon.targets .targets* 檔案。 *.Targets* 檔案會評估來自匯入專案的屬性以設定組建。

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

## <a name="example-2"></a>範例 2

 下列程式碼範例會匯入 *>mycommon.targets .targets* 檔案。

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
