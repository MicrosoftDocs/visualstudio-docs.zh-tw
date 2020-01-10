---
title: 使用 editorconfig 設定 FxCop 分析器
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b1d178adbbb847b2629ee785a7a0fa4e990a46dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587715"
---
# <a name="configure-fxcop-analyzers"></a>設定 FxCop 分析器

[FxCop 分析器封裝](install-fxcop-analyzers.md)是由舊版分析中最重要的 "FxCop" 規則所組成，轉換成以 .NET Compiler Platform 為基礎的程式碼分析器。 針對某些 FxCop 規則，您可以透過可設定的[選項](fxcop-analyzer-options.md)，精簡程式碼基底中應該套用的部分。 每個選項都是藉由將索引鍵/值組新增至[EditorConfig](https://editorconfig.org)檔來指定。 設定檔可以是[專案特有](#per-project-configuration)的，也可以在兩個或多個專案之間[共用](#shared-configuration)。

> [!TIP]
> 以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**加入** > **新專案**]，將 editorconfig 檔案新增至您的專案。 在 [**加入新專案**] 視窗的 [搜尋] 方塊中，輸入**editorconfig** 。 選取 [ **editorconfig 檔案（預設）** ] 範本，然後選擇 [**新增**]。
>
> ![在 Visual Studio 中將 editorconfig 檔案新增至專案](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

如需設定規則嚴重性（例如，其為錯誤或警告）的相關資訊，請參閱[在 EditorConfig 檔中設定規則嚴重性](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)。 或者，您可以選擇其中一個內建的[EditorConfig 檔案或規則集](analyzer-rule-sets.md)，以快速啟用或停用規則的類別。

::: moniker-end

本文的其餘部分[會討論精簡](fxcop-analyzer-options.md)套用 FxCop 規則之選項的一般語法。

> [!NOTE]
> 您不能使用 EditorConfig 檔來設定舊版 FxCop 規則。 如需舊版分析和 FxCop 分析器之間差異的詳細資訊，請參閱[FxCop 分析器常見問題](fxcop-analyzers-faq.md)。

## <a name="option-scopes"></a>選項範圍

每個精簡選項都可以針對所有規則、規則分類（例如，命名或設計），或針對特定規則進行設定。

### <a name="all-rules"></a>所有規則

為*所有*規則設定選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。選項名稱 = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>規則類別

為規則*分類*設定選項的語法（例如命名、設計或效能）如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleCategory. 選項名稱 = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>特定規則

針對*特定*規則設定選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleId. 選項名稱 = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="per-project-configuration"></a>每個專案的設定

若要針對特定專案啟用以 EditorConfig 為基礎的分析器設定，請將*EditorConfig*檔案新增至專案的根目錄。

目前不會對存在於不同目錄層級（例如方案和專案層級）的 editorconfig 檔案進行階層式支援。

## <a name="shared-configuration"></a>共用設定

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
> 此處所述之 EditorConfig 檔的任意共用位置，僅適用于設定特定 FxCop 分析器規則的範圍。 針對其他設定（例如規則嚴重性、一般編輯器設定和程式碼樣式），EditorConfig 檔案必須一律放在專案資料夾或父資料夾中。

## <a name="see-also"></a>請參閱

- [FxCop 分析器的規則範圍選項](fxcop-analyzer-options.md)
- [分析器設定](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop 分析器](install-fxcop-analyzers.md)
- [適用于 EditorConfig 的 .NET 編碼慣例](../ide/editorconfig-code-style-settings-reference.md)
