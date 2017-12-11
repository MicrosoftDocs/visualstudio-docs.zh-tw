---
title: "自訂組建系統 | Microsoft Docs"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 2d17a952c58e5ef7e593ee7aeb1980e09a376800
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-build-system"></a>自訂組建系統

MSbuild 是 Microsoft 所開發的組建引擎，可用來建置主要的 .NET 應用程式。 而 Mono 架構也有它自己的 Microsoft 組建引擎實作，稱為 **xbuild**。 不過，xbuild 已遭淘汰，改為在所有作業系統上使用 MSBuild。

**MSbuild** 主要用作為 Visual Studio for Mac 中專案的組建系統。 

MSBuild 的運作方式為採用一組輸入 (例如來源檔案) 並將其轉換為輸出 (例如可執行檔)，然後藉由叫用編譯器等工具完成此輸出。 


## <a name="msbuild-file"></a>MSBuild 檔案

MSBuild 會使用稱為專案檔的 XML 檔案，以定義屬於專案一部分的「項目」 (例如影像資源)，以及建置專案所需的「屬性」。 這個專案檔一律是以副檔名 `proj` 結尾，例如 C# 專案的 `.csproj`。 

### <a name="viewing-the-msbuild-file"></a>檢視 MSBuild 檔案
您可以在專案名稱上按一下滑鼠右鍵，然後選取 [在尋找工具中顯示 ]，來找到這個檔案。 這會顯示與您專案相關的所有檔案和資料夾，包括 `.csproj` 檔案，如下所示：

![](media/customizing-build-system-image1.png)

您也可以在專案名稱上按一下滑鼠右鍵，並瀏覽至 [工具] > [編輯檔案]，以在 Visual Studio for Mac 中使用新的索引標籤顯示 `.csproj`：

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>組合 MSBuild 檔案

所有的 MSBuild 檔案包含必要的 `Project` 根項目，如下所示：

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

專案通常也會匯入 `.targets` 檔案，其中包含許多描述如何處理和建置各種檔案的規則。 這通常會顯示在 `proj` 檔案的底端，對於 C# 專案其內容如下所示：

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

目標檔案是另一個 MSBuild 檔案。 此檔案包含多個專案重複使用的 MSBuild 程式碼。 例如，在 `MSBuildBinPath` 屬性 (或變數) 所代表的目錄中找到的 `Microsoft.CSharp.targets` 檔案，包含從 C# 原始程式檔建置 C# 組件的邏輯。

### <a name="items-and-properties"></a>項目和屬性

MSBuild 中有兩種基本資料類型：「項目」和「屬性」，其詳細說明如下。

#### <a name="properties"></a>屬性

屬性是索引鍵/值組，用來儲存影響編譯的設定，例如編譯器選項。

它們將使用 PropertyGroup 設定，並且可以包含任意數目的 PropertiesGroups，而 PropertiesGroups 可以包含任意數目的屬性。 

例如，簡單主控台應用程式的 PropertyGroup 可能如下所示：

```
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

可以使用 `$()` 語法從運算式參考屬性。 例如，`$(Foo)` 會評估為 `Foo` 屬性的值。 如果尚未設定屬性，它會評估為空字串，而且不會產生任何錯誤。

#### <a name="items"></a>項目

項目提供一種以清單或集合輸入組建系統的處理方法，通常代表檔案。 每個項目都包含項目「類型」、項目「規格」和選擇性的任意「中繼資料」。 請注意，MSBuild 不會在個別項目上運作，而是對指定類型的所有項目 (稱為項目「集」) 執行

項目是藉由宣告 `ItemGroup` 來建立。 可以有任意數目的 ItemGroup，而 ItemGroup 可以包含任何數目的項目。 

例如，下列程式碼片段會建立 iOS 啟動畫面。 這些為 `BundleResource` 類型，並以影像的路徑作為其規格：

```
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```
 
 可以使用 `@()` 語法從運算式參考項目集。 例如，`@(BundleResource)` 會評估為 BundleResource 項目集，這表示所有 BundleResource 項目。 如果沒有此類型的項目，則其為空白，而且不會產生任何錯誤。

## <a name="resources-for-learning-msbuild"></a>用來學習 MSBuild 的資源

若要更詳細了解 MSBuild，可使用下列資源：

* [MSDN - 概觀](https://msdn.microsoft.com/library/dd393574.aspx)
* [MSDN - 概念](https://msdn.microsoft.com/library/dd637714.aspx)


