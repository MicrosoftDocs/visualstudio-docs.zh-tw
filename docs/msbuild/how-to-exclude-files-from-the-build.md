---
title: 如何：從組建中排除檔案 | Microsoft Docs
description: 瞭解如何明確地排除或有條件地將組建中的檔案包含在 MSBuild 專案檔案中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e838460f1e42f34e92a99198b9d4a0e34ce71dcd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914381"
---
# <a name="how-to-exclude-files-from-the-build"></a>如何：從組建中排除檔案

在專案檔中，您可以使用萬用字元，來包含一個目錄中的所有檔案或巢狀目錄集合做為組建的輸入。 不過，目錄中可能有一個您不想包含來建置輸入的檔案，或者巢狀目錄集合中可能有一個您不想包含的目錄。 您可以明確地從輸入清單中排除該檔案或目錄。 專案中也可能有一個您只想在符合特定條件的情況下包含的檔案。 您可以明確地宣告要在組建中包含檔案的條件。

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>從組建的輸入中排除檔案或目錄

 項目清單是組建的輸入檔。 您可以使用 `Include` 屬性，個別宣告或以群組方式宣告想要包含的項目。 例如：

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 如果您使用萬用字元來包含一個目錄中的所有檔案或巢狀目錄集合做為建置的輸入，則目錄中可能有一或多個您不想包含的檔案，或巢狀目錄集合中可能有一個您不想包含的目錄。 若要從項目清單中排除項目，請使用 `Exclude` 屬性。

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>包含 *Form2* 以外的所有 *.cs* 或 *.vb* 檔案

- 使用下列其中一個 `Include` 和 `Exclude` 屬性：

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    或

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>包含 *Form2* 和 *Form3* 以外的所有 *.cs* 或 *.vb* 檔案

- 使用下列其中一個 `Include` 和 `Exclude` 屬性：

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    或

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>包含 *Images* 目錄子目錄中的所有 *.jpg* 檔案，但 *Version2* 目錄中的檔案除外

- 使用下列 `Include` 和 `Exclude` 屬性：

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > 您必須指定這兩個屬性的路徑。 如果您使用絕對路徑，在 `Include` 屬性中指定檔案位置，也必須在 `Exclude` 屬性中使用絕對路徑。如果您在 `Include` 屬性中使用相對路徑，就必須在 `Exclude` 屬性中使用相對路徑。

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>使用條件來從組建的輸入中排除檔案或目錄

 例如，如果偵錯組建中 (但不在發行組建中) 有您想要包含的項目，您可以使用 `Condition` 屬性來指定要包含該項目的條件。

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>只在發行組建中包含檔案 *公式。 vb*

- 以如下方式使用 `Condition` 屬性：

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>範例

 下列程式碼範例會建立一個專案，其中包含目錄中的所有 *.cs* 檔案，但 *Form2.cs* 除外。

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" Exclude="Form2.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [項目](../msbuild/msbuild-items.md)
- [MSBuild](../msbuild/msbuild.md)
- [如何：選取要建置的檔案](../msbuild/how-to-select-the-files-to-build.md)
