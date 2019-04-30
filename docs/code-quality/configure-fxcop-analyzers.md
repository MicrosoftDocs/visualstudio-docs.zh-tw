---
title: 設定使用 editorconfig 的 FxCop 分析器
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816909"
---
# <a name="configure-fxcop-analyzers"></a>設定 FxCop 分析器

[FxCop 分析器](install-fxcop-analyzers.md)靜態程式碼分析，轉換為 Roslyn 分析器的最重要 」 FxCop 」 規則所組成。 您可以設定 FxCop 程式碼分析器，有兩種：

- 具有[規則集](#fxcop-analyzer-rule-sets)，可讓您啟用或停用規則，以及設定個別的規則違規的嚴重性。

- 從版本 2.6.3 [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 套件，透過[.editorconfig 檔案](#editorconfig-file)。 [可設定選項](fxcop-analyzer-options.md)精簡的哪些部分可讓您分析程式碼基底。

> [!TIP]
> FxCop 靜態程式碼分析和 FxCop 分析器之間差異的詳細資訊，請參閱[FxCop 分析器常見問題集](fxcop-analyzers-faq.md)。

## <a name="fxcop-analyzer-rule-sets"></a>FxCop 分析器規則集

若要設定 FxCop 分析器的一種方法是使用 XML*規則集*。 規則集是找出目標的問題及特定條件的程式碼分析規則的群組。 規則集可讓您啟用或停用規則及設定個別的規則違規的嚴重性。

FxCop 分析器 NuGet 套件包含下列規則類別的預先定義的規則集：

- 設計
- 文件
- 維護性維護性
- 命名
- 效能
- 可靠性
- 安全性
- 用法

如需詳細資訊，請參閱 < [Roslyn 分析器的規則集](analyzer-rule-sets.md)。

## <a name="editorconfig-file"></a>EditorConfig 檔案

您可以透過加入索引鍵 / 值組，以設定分析器規則[.editorconfig](https://editorconfig.org)檔案。 可以是組態檔[專案的特定](#per-project-configuration)也可以是[共用](#shared-configuration)兩個或多個專案之間。

### <a name="per-project-configuration"></a>每個專案組態

若要啟用特定專案的.editorconfig 為基礎的解析程式設定，請新增 *.editorconfig*檔案至專案的根目錄。

> [!TIP]
> 您可以新增.editorconfig 檔案至您的專案中的專案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新項目**。 在 [**加入新項目**] 視窗中，輸入**editorconfig**在搜尋方塊中。 選取  **editorconfig 檔案 （預設值）** 範本，然後選擇**新增**。
>
> ![將 editorconfig 項目新增至 Visual Studio 中的專案](media/add-editorconfig-file.png)

目前沒有任何階層式支援針對 「 結合 」.editorconfig 檔案，存在於不同的目錄層級，例如，方案和專案層級。

### <a name="shared-configuration"></a>共用的設定

您可以共用兩個或多個專案之間的分析器組態的.editorconfig 檔案，但需要一些額外的步驟。

1. 儲存 *.editorconfig*的常見的位置。

2. 建立 *.props*檔案使用下列內容：

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. 加入線條以您 *.csproj*或是 *.vbproj*要匯入檔案 *.props*您在上一個步驟中建立的檔案。 這一行必須放在匯入的 FxCop 分析器任何程式碼行之前 *.props*檔案。 例如，如果您的.props 檔案會命名為*editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. 重新載入專案。

> [!NOTE]
> 您無法使用.editorconfig 檔案來設定舊版 FxCop 規則 （靜態程式碼分析 FxCop）。

## <a name="option-scopes"></a>選項範圍

所有規則、 類別的規則 （例如，命名或設計），或特定的規則，可以設定每個選項。

### <a name="all-rules"></a>所有規則

設定所有規則的選項的語法如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>類別的規則

設定選項的語法*分類*的 （例如命名、 設計或效能） 的規則如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>特定的規則

設定特定規則的選項的語法如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>另請參閱

- [分析器組態](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop 分析器](install-fxcop-analyzers.md)
