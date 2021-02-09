---
title: MSBuild 轉換 | Microsoft Docs
description: 深入瞭解 MSBuild 如何使用轉換，將一個專案清單的一對一轉換轉換成另一個專案清單，以便更有效率地建立專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba6a71373026a5a41905efc7c91520a9f6b7c5c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878203"
---
# <a name="msbuild-transforms"></a>MSBuild 轉換

轉換是指某個項目清單和另一個項目清單的一對一轉換作業。 轉換作業除了可讓專案轉換項目清單，還能讓目標識別其輸入和輸出之間的直接對應。 本主題說明轉換，以及 MSBuild 如何使用它們來更有效率地建立專案。

## <a name="transform-modifiers"></a>轉換修飾詞

轉換不是任意的，但受限於特殊語法，其中所有轉換修飾詞的格式都必須是% (\<ItemMetaDataName>) 。 任何項目中繼資料均可作為轉換修飾詞。 這包括每個項目建立時指派給項目的已知項目中繼資料。 如需已知項目中繼資料的清單，請參閱[已知項目中繼資料](../msbuild/msbuild-well-known-item-metadata.md)。

下列範例會將一份 *.resx* 檔案清單轉換為 *.resources* 檔案清單。 %(filename) 轉換修飾詞會指定每個 *.resources* 檔案使用與對應 *.resx* 檔案相同的檔案名稱。

```xml
@(RESXFile->'%(filename).resources')
```

比方說，如果 @(RESXFile) 項目清單中的項目是 *Form1.resx*、*Form2.resx* 和 *Form3.resx*，已轉換清單中的輸出會是 *Form1.resources*、*Form2.resources* 和 *Form3.resources*。

> [!NOTE]
> 您可以為已轉換的項目清單指定自訂分隔符號 (方法與您為標準項目清單指定分隔符號的方式相同)。 例如，若要使用逗號 (,) 而不是預設的分號 (;) 來分隔已轉換的項目清單，請使用下列 XML： `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>使用多個修飾詞

 轉換運算式可包含多個修飾詞，其可依照任何順序合併，亦可以重複。 在下列範例中，含有檔案的目錄名稱已變更，但這些檔案會保留原始名稱和副檔名。

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 比方說，如果 `RESXFile` 項目清單中包含的項目是 *Project1\Form1.resx*、*Project1\Form2.resx* 和 *Project1\Form3.text*，已轉換清單中的輸出會是 *Toolset\Form1.resx*、*Toolset\Form2.resx* 和 *Toolset\Form3.text*。

## <a name="dependency-analysis"></a>相依性分析

 轉換作業可保證轉換後的項目清單與原始項目清單之間的一對一對應。 因此，如果目標建立的輸出是輸入的轉換，MSBuild 可以分析輸入和輸出的時間戳記，並決定要跳過、建立還是部分重建目標。

 在下列範例的 [Copy 工作](../msbuild/copy-task.md)中，`BuiltAssemblies` 項目清單中的每個檔案都會對應至工作目的地資料夾中的檔案 (透過在 `Outputs` 屬性中使用轉換來指定)。 如果 `BuiltAssemblies` 項目清單中的檔案有所變更，系統就只會針對已變更的檔案執行 `Copy` 工作，並略過所有其他檔案。 如需相依性分析以及如何使用轉換的詳細資訊，請參閱[如何：累加建置](../msbuild/how-to-build-incrementally.md)。

```xml
<Target Name="CopyOutputs"
    Inputs="@(BuiltAssemblies)"
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">

    <Copy
        SourceFiles="@(BuiltAssemblies)"
        DestinationFolder="$(OutputPath)"/>

</Target>
```

## <a name="example"></a>範例

### <a name="description"></a>描述

 下列範例顯示使用轉換的 MSBuild 專案檔。 這個範例假設 *c:\sub0\sub1\sub2\sub3* 目錄中只有一個 *.xsd* 檔案，而工作目錄是 *c:\sub0*。

### <a name="code"></a>程式碼

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Schema Include="sub1\**\*.xsd"/>
    </ItemGroup>

    <Target Name="Messages">
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>
        <Message Text="identity: @(Schema->'%(identity)')"/>
        <Message Text="filename: @(Schema->'%(filename)')"/>
        <Message Text="directory: @(Schema->'%(directory)')"/>
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>
        <Message Text="extension: @(Schema->'%(extension)')"/>
    </Target>
</Project>
```

### <a name="comments"></a>註解

 這個範例會產生下列輸出：

```
rootdir: C:\
fullpath: C:\sub0\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\sub0\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: sub0\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [如何：以累加方式建立](../msbuild/how-to-build-incrementally.md)
