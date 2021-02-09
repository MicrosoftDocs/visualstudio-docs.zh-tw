---
title: 如何：建置包含資源的專案 | Microsoft Docs
description: 瞭解如何建立具有資源的專案，以及如何使用 MSBuild 編譯資源。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 195ef17e4770d7050bc3b10f11ca5530e5ca49cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914479"
---
# <a name="how-to-build-a-project-that-has-resources"></a>如何：建置包含資源的專案

如果您要建置專案的當地語系化版本，就必須將所有使用者介面項目分隔成適用於各種語言的資源檔。 如果專案只會使用字串，資源檔就能使用文字檔。 或者，您也可以使用 *.resx* 檔做為資源檔。

## <a name="compile-resources-with-msbuild"></a>使用 MSBuild 編譯資源

MSBuild 隨附的一般工作程式庫包含一 `GenerateResource` 項工作，您可以用來編譯 *.resx* 或文字檔中的資源。 此工作包含 `Sources` 參數來指定要編譯哪一個資源檔，以及 `OutputResources` 參數來指定輸出資源檔的名稱。 如需工作的詳細資訊 `GenerateResource` ，請參閱 [GenerateResource task](../msbuild/generateresource-task.md)。

#### <a name="to-compile-resources-with-msbuild"></a>使用 MSBuild 編譯資源

1. 識別出專案的資源檔，然後將其傳遞到 `GenerateResource` 工作以做為項目清單或做為檔案名稱。

2. 指定 `GenerateResource` 工作的 `OutputResources` 參數，可讓您設定輸出資源檔的名稱。

3. 使用工作的 `Output` 項目 (Element)，在項目 (Item) 中儲存 `OutputResources` 參數的值。

4. 使用從 `Output` 項目(Element) 建立的項目 (Item) 做為另一個工作的輸入。

## <a name="example-1"></a>範例 1

下列程式碼範例示範 `Output` 項目如何指定 `GenerateResource` 工作的 `OutputResources` 屬性將包含已編譯的資源檔 *alpha.resources* 和 *beta.resources*，而這兩個檔案會置於 `Resources` 項目清單中。 藉由將這些 *.resources* 檔案識別為相同名稱的專案集合，您可以輕鬆地使用它們做為另一項工作的輸入，例如 [Csc](../msbuild/csc-task.md) 工作。

此工作相當於使用 [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) 的 **/compile** 參數：

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example-2"></a>範例 2

下列範例專案包含兩個工作：`GenerateResource` (可編譯資源) 和 `Csc` (可編譯原始程式碼檔案和已編譯的資源檔案)。 `GenerateResource` 工作所編譯的資源檔會儲存在 `Resources` 項目中，然後傳遞到 `Csc` 工作。

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource 工作](../msbuild/generateresource-task.md)
- [Csc 工作](../msbuild/csc-task.md)
- [ 資源檔產生器Resgen.exe () ](/dotnet/framework/tools/resgen-exe-resource-file-generator)
