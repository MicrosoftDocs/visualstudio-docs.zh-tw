---
title: 使用 editorconfig 設定 FxCop 分析器
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 68c175a55c9e60e870a5466a831aaae50d62dced
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293454"
---
# <a name="configure-fxcop-analyzers"></a>設定 FxCop 分析器

[FxCop 分析器](install-fxcop-analyzers.md)包含舊版分析中最重要的 "FxCop" 規則，轉換成以 .NET Compiler Platform 為基礎的程式碼分析器。 您可以透過兩種方式來設定 FxCop 程式碼分析器：

- 使用[規則集](#fxcop-analyzer-rule-sets)，可讓您啟用或停用規則，並設定個別規則違規的嚴重性。

- 從2.6.3 的[CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 套件的版本開始，透過[editorconfig](#editorconfig-file)檔案。 可設定的[選項](fxcop-analyzer-options.md)可讓您精簡程式碼基底中要分析的部分。

> [!TIP]
> 如需舊版分析和 FxCop 分析器之間差異的詳細資訊，請參閱[FxCop 分析器常見問題](fxcop-analyzers-faq.md)。

## <a name="fxcop-analyzer-rule-sets"></a>FxCop 分析器規則集

設定 FxCop 分析器的其中一種方式是使用 XML*規則集*。 規則集是一組程式碼分析規則，可識別目標問題和特定條件。 規則集可讓您啟用或停用規則，並設定個別規則違規的嚴重性。

FxCop 分析器 NuGet 套件包含下列規則類別的預先定義規則集：

- 設計
- 文件
- 維護性維護性
- 命名
- 效能
- 可靠性
- 安全性
- 用法

如需詳細資訊，請參閱[程式碼分析器的規則集](analyzer-rule-sets.md)。

## <a name="editorconfig-file"></a>EditorConfig 檔案

您可以將索引鍵/值組新增至[editorconfig](https://editorconfig.org)檔案，以設定 FxCop 分析器規則。 設定檔可以是[專案特有](#per-project-configuration)的，也可以在兩個或多個專案之間[共用](#shared-configuration)。

> [!NOTE]
> 您無法使用 editorconfig 檔案來設定舊版 FxCop 規則。

### <a name="per-project-configuration"></a>每個專案的設定

若要針對特定專案啟用以 editorconfig 為基礎的分析器設定，請將*editorconfig*檔案新增至專案的根目錄。

> [!TIP]
> 您可以在**方案總管**中以滑鼠右鍵按一下專案，然後選取 [**加入** > **新專案**]，將 editorconfig 檔案新增至專案。 在 [**加入新專案**] 視窗的 [搜尋] 方塊中，輸入**editorconfig** 。 選取 [ **editorconfig 檔案（預設）** ] 範本，然後選擇 [**新增**]。
>
> ![在 Visual Studio 中將 editorconfig 專案新增至專案](media/add-editorconfig-file.png)

目前不會對存在於不同目錄層級（例如方案和專案層級）的 editorconfig 檔案進行階層式支援。

### <a name="shared-configuration"></a>共用設定

您可以在兩個或多個專案之間共用 FxCop 分析器設定的 editorconfig 檔案，但它需要一些額外的步驟。

1. 將*editorconfig*檔案儲存到一般位置。

2. 使用下列內容建立 *.props*檔案：

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

3. 在您的 *.csproj*或 *. vbproj*檔案中新增一行，以匯入您在上一個步驟中建立的 *.props*檔案。 這一行必須放在匯入 FxCop 分析器 *. .props*檔案的任何行之前。 例如，如果您的 .props 檔案名為*editorconfig. .props*：

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. 重載專案。

> [!NOTE]
> 此處所述之 EditorConfig 檔的任意共用位置僅適用于設定 FxCop 分析器。 針對其他設定（例如縮排和程式碼樣式），EditorConfig 檔案必須一律放在專案資料夾或父資料夾中。

## <a name="option-scopes"></a>選項範圍

每個選項都可以針對 [所有規則]、[規則] 類別（例如 [命名] 或 [設計]），或針對特定規則進行設定。

### <a name="all-rules"></a>所有規則

為所有規則設定選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality.選項名稱 = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>規則類別

為規則*分類*設定選項的語法（例如命名、設計或效能）如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality.RuleCategory. 選項名稱 = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>特定規則

針對特定規則設定選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality.RuleId. 選項名稱 = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>另請參閱

- [分析器設定](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop 分析器](install-fxcop-analyzers.md)
- [適用于 EditorConfig 的 .NET 編碼慣例](../ide/editorconfig-code-style-settings-reference.md)
