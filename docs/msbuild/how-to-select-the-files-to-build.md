---
title: 如何：選取要建置的檔案 | Microsoft Docs
description: 瞭解如何藉由分別列出每個檔案或使用萬用字元，來選取要在 MSBuild 專案檔中建立的檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f324fb3999c94d8f26e329859e095f31740c76c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914239"
---
# <a name="how-to-select-the-files-to-build"></a>如何：選取要建置的檔案

建置包含數個檔案的專案時，您可以在專案檔中分別列出每個檔案，或是您可以使用萬用字元來包含一個目錄或巢狀目錄集合中的所有檔案。

## <a name="specify-inputs"></a>指定輸入

項目代表建置的輸入。 如需項目的詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

若要包含組建的檔案，這些檔案必須包含在 MSBuild 專案檔的專案清單中。 多個檔案可以新增至項目清單，方法是個別包含檔案，或是使用萬用字元來一次包含許多檔案。

#### <a name="to-declare-items-individually"></a>個別宣告項目

- 使用 `Include` 屬性，類似如下︰

    `<CSFile Include="form1.cs"/>`

    或

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > 如果項目集合中的項目不在與專案檔相同的目錄中，您必須指定項目的完整或相對路徑。 例如：`Include="..\..\form2.cs"`。

#### <a name="to-declare-multiple-items"></a>宣告多個項目

- 使用 `Include` 屬性，類似如下︰

    `<CSFile Include="form1.cs;form2.cs"/>`

    或

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>使用萬用字元指定輸入

您也可以使用萬用字元，以遞迴方式包含所有檔案，或只包含來自子目錄的特定檔案，作為建置的輸入。 如需萬用字元的詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)

下列範例所根據的專案，包含下列目錄和子目錄中的圖形檔案，且專案檔位於「專案」目錄中︰

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>包含 *Images* 目錄和子目錄中的所有 *.jpg* 檔案

- 使用下列 `Include` 屬性：

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>包含開頭為 *img* 的所有 *.jpg* 檔案

- 使用下列 `Include` 屬性：

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>包含目錄中名稱結尾為 *jpgs* 的所有檔案

- 使用下列其中一個 `Include` 屬性：

    `Include="Images\**\*jpgs\*.*"`

    或

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>將項目傳遞至工作

在專案檔案中，您可以在工作中使用 @() 標記法指定整個項目清單作為組置的輸入。 不論您分別列出所有檔案，還是使用萬用字元，都可以使用這個標記法。

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>使用所有 Visual C# 或 Visual Basic 檔案作為輸入

- 使用 `Include` 屬性，類似如下︰

    `<CSC Sources="@(CSFile)">...</CSC>`

    或

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> 您必須使用萬用字元搭配專案來指定組建的輸入;您無法使用 `Sources` MSBuild 或[Vbc](../msbuild/vbc-task.md)等 MSBuild 工作中的屬性來[](../msbuild/csc-task.md)指定輸入。 下列範例在專案檔案中無效︰
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example-1"></a>範例 1

下列程式碼範例會顯示個別包含所有輸入檔案的專案。

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

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

## <a name="example-2"></a>範例 2

下列程式碼範例會使用萬用字元來包含所有 *.cs* 檔。

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

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

- [如何：從組建中排除檔案](../msbuild/how-to-exclude-files-from-the-build.md)
- [項目](../msbuild/msbuild-items.md)
