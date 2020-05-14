---
title: 配置代碼分析
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431348"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>如何：為託管代碼配置舊版分析

在 Visual Studio 中，您可以從代碼分析[規則集](../code-quality/rule-set-reference.md)清單中選擇以應用於託管代碼專案。 預設情況下，選擇**Microsoft 最小建議規則**集，但如果需要，可以應用其他規則集。 規則集可以應用於解決方案中的一個或多個專案。

> [!NOTE]
> 本文適用于舊分析，不適用於[基於 .NET 編譯器平臺的代碼分析器](use-roslyn-analyzers.md)。

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>為 .NET 框架專案配置規則集

1. 打開專案屬性頁上的代碼**分析**選項卡。 您可以使用下列其中一種方法執行這個動作：

   - 在**解決方案資源管理器中**，選擇專案。 在功能表列上，選擇 **"分析** > **配置代碼分析** > **"以進行\<專案名稱>**。

   - 按右鍵**解決方案資源管理器**中的專案並選擇 **"屬性**"，然後選擇 **"代碼分析**"選項卡。

2. 在 **"配置**和**平臺**"清單中，選擇組建組態和目標平臺。

::: moniker range="vs-2017"

3. 要每次使用所選配置生成專案時運行代碼分析，請選擇 **"在生成啟用代碼分析**"。 還可以通過在**專案\<名稱>上**選擇**分析** > **運行代碼分析** > 運行代碼分析來手動運行代碼分析。

::: moniker-end

::: moniker range=">=vs-2019"

3. 要在每次使用所選配置生成專案時運行代碼分析，請在**Binary 分析器**部分中選擇 **"在生成時運行**"。 您還可以手動運行舊代碼分析，[請參閱如何：為託管代碼手動運行舊代碼分析](how-to-run-legacy-code-analysis-manually-for-managed-code.md)，瞭解更多詳細資訊。

::: moniker-end

4. 要查看來自生成的代碼的警告，請清除 **"從生成的代碼中抑制結果**"核取方塊。

    > [!NOTE]
    > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以查看和維護表單或範本的原始程式碼，並且不會被覆蓋。

::: moniker range="vs-2017"

5. 在 **"運行此規則集**"清單中，執行以下操作之一：

::: moniker-end

::: moniker range=">=vs-2019"

5. 在 **"活動規則"** 清單中，執行以下操作之一：

::: moniker-end

   - 選擇要使用的規則集。

   - 選擇**\<"流覽>** 以查找不在清單中的現有自訂規則集。

   - 定義[自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)。

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>為解決方案中的多個專案指定規則集

預設情況下，解決方案的所有託管專案都分配了*Microsoft 最小建議規則*代碼分析規則集。 您可以在解決方案的 **"屬性"** 對話方塊中更改分配給解決方案專案的規則集。

1. 在 Visual Studio 中開啟解決方案。

2. 在 **"分析"** 功能表上，選擇 **"為解決方案配置代碼分析**"。

3. 如有必要，請展開**公共屬性**，然後選擇**代碼分析設置**。

4. 您可以為一個或多個專案指定規則集：

    - 要為單個專案指定規則集，請選擇專案名稱。

    - 要為多個專案指定規則集，請按住**Ctrl**並選擇專案名稱。

    - 要指定解決方案中的所有專案，請按住**Shift**並按一下專案清單中。

5. 選擇專案**的規則集**欄位，然後選擇要應用的規則集的名稱。

## <a name="see-also"></a>另請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)
