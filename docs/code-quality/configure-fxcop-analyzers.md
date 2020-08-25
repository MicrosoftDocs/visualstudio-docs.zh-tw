---
title: 使用 editorconfig 設定 .NET 程式碼品質分析器
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800732"
---
# <a name="configure-net-code-quality-analyzers"></a>設定 .NET 程式碼品質分析器

針對特定的 .NET 程式碼品質分析器 (其規則識別碼以) 開頭的程式碼 `CA` ，您可以透過 [可](fxcop-analyzer-options.md)設定的選項，來精簡應套用程式碼基底的哪些部分。 每個選項都是藉由將機碼/值組新增至 [EditorConfig](https://editorconfig.org) 檔案來指定。 設定檔案、專案、解決方案或整個存放庫都有特定的設定檔。

> [!TIP]
> 以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**加入**  >  **新專案**]，將 editorconfig 檔案加入至專案。 在 [ **加入新專案** ] 視窗的 [搜尋] 方塊中，輸入 **editorconfig** 。 選取 **editorconfig 檔案 (預設) ** 範本，然後選擇 [ **新增**]。
>
> ![在 Visual Studio 中將 editorconfig 檔案新增至專案](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

如需設定規則嚴重性 (例如，是否為錯誤或警告) 的詳細資訊，請參閱 [在 EditorConfig 檔中設定規則嚴重性](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)。 或者，您可以選擇其中一個內建的 [EditorConfig 檔或規則集](analyzer-rule-sets.md) ，以快速啟用或停用規則的類別。

::: moniker-end

本文的其餘部分將討論適用于精簡套用 .NET 程式碼品質分析器之 [選項](fxcop-analyzer-options.md) 的一般語法。

## <a name="option-scopes"></a>選項範圍

您可以針對規則類別 (（例如，命名或設計) ）或特定規則，設定所有規則的每個精簡選項。

### <a name="all-rules"></a>所有規則

設定 *所有* 規則選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。選項名稱 = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>規則類別

為規則 *類別* 設定選項的語法 (例如 [命名]、[設計] 或 [效能) ]，如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleCategory. 選項名稱 = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>特定規則

設定 *特定* 規則選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleId. 選項名稱 = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>啟用以 Editorconfig 為基礎的設定

您可以針對下列範圍啟用以 EditorConfig 為基礎的分析器設定：

- 特定檔 (s) 
- 特定資料夾 (s) 
- 特定專案 (s) 
- 特定解決方案 (s) 
- 整個存放庫

若要啟用設定，請在對應的目錄中新增具有選項的*editorconfig 檔案。* 這個檔案也可以包含以 EditorConfig 為基礎的診斷嚴重性設定專案。 詳細資訊請看[這裡](use-roslyn-analyzers.md#rule-severity)。

## <a name="see-also"></a>另請參閱

- [.NET 程式碼品質分析器的規則範圍選項](fxcop-analyzer-options.md)
- [分析器設定](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [適用于 EditorConfig 的 .NET 編碼慣例](../ide/editorconfig-code-style-settings-reference.md)
