---
title: 如何：將專案設定成以平台為目標
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cbe4bc3f982ae18b9f85fe8bf5c21495c98beee
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76112549"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>如何：將專案設定成以平台為目標

Visual Studio 可讓您將應用程式的目標設定為不同的平台，包括 64 位元的平台。 如需 Visual Studio 中 64 位元平台支援的詳細資訊，請參閱 [64 位元應用程式](/dotnet/framework/64-bit-apps)。

## <a name="target-platforms-with-the-configuration-manager"></a>使用組態管理員設定目標平台

[組態管理員] 可讓您快速加入新平台，以成為專案的目標。 如果您選取 Visual Studio 隨附的其中一個平台，您的專案屬性會經過修改，以針對選取的平台建置專案。

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>將專案設定成以 64 位元平台為目標

1. 在功能表列上，選擇 [建置] > [組態管理員]。

2. 在 [使用中的方案平台] 清單中，選擇 64 位元平台作為方案的目標，然後選擇 [關閉] 按鈕。

    1. 如果您想要的平台未出現在 [使用中的方案平台] 清單中，請選擇 [新增]。

         [新增方案平台] 對話方塊隨即出現。

    2. 在 [輸入或選取新平台] 清單中選擇 [x64]。

        > [!NOTE]
        > 如果您將組態改為新的名稱，則必須在 [專案設計工具] 中修改設定，才能以正確的平台為目標。

    3. 如果您想要從目前的平台組態複製設定，請選擇所需項目，然後選擇 [確定] 按鈕。

以 64 位元平台為目標的所有專案的屬性會進行更新，而專案的下一個組建會針對 64 位元平台進行最佳化。

## <a name="target-platforms-in-the-project-designer"></a>在專案設計工具中設定目標平台

**專案設計工具**也可供您將專案的目標設為不同的平台。 如果您在 [新增方案平台] 對話方塊清單中，選取了一個不適用於方案的平台，您可以建立自訂組態名稱並修改 [專案設計工具] 中的設定，以正確的平台為目標。

根據您所使用的程式設計語言而定，此工作的執行會有所不同。 請參閱下列連結以取得詳細資訊：

- 若是 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案，請參閱 [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform)。

- 若是 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案，請參閱[專案設計工具、建置頁 (C#)](../ide/reference/build-page-project-designer-csharp.md)。

- 若是 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案，請參閱 [/clr (Common Language Runtime 編譯)](/cpp/build/reference/clr-common-language-runtime-compilation)。

## <a name="manually-editing-the-project-file"></a>手動編輯專案檔

有時候，針對某些自訂組態您可能需要手動編輯專案檔。 其中一個範例是當您有無法在 IDE 中指定的條件時 (例如針對兩個不同平台使用不同的參考)，如下列範例所示。

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>範例：參考 x86 和 x64 元件和 Dll

您可能會擁有同時具備 x86 和 x64 版本的 .NET 組件或 DLL。 若要設定您的專案使用這些參考，請先新增參考，然後開啟專案檔並編輯它來新增 `ItemGroup`，其中包含同時參考兩個組態及目標平台的條件。  例如，假設您正在參考的二進位檔是 ClassLibrary1，且針對 Debug 和 Release 組態以及 x86 和 x64 版本有不同的路徑。  然後，請使用四個 `ItemGroup` 元素，其中包含所有設定組合，如下所示：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> 在 Visual Studio 2017 中，您需要先卸載專案，才能編輯專案檔。 若要卸載專案，請以滑鼠右鍵按一下專案節點，然後選擇 [卸載專案]。 完成編輯後，請儲存您的變更，然後以滑鼠右鍵按一下專案節點並選擇 [重新載入專案] 來重新載入專案。
::: moniker-end

如需專案檔的詳細資訊，請參閱 [MSBuild 專案檔結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)。

## <a name="see-also"></a>請參閱

- [了解建置平台](../ide/understanding-build-platforms.md)
- [/platform (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64 位元應用程式](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64 位元支援](../ide/visual-studio-ide-64-bit-support.md)
- [了解專案檔](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
