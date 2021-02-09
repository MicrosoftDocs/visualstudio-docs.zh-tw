---
title: 設定程式碼分析
ms.date: 04/04/2018
description: 瞭解如何設定 Visual Studio 舊版程式碼分析使用的規則集。 瞭解如何將規則集套用至解決方案中的一或多個專案。
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
- vs.codeanalysis.propertypages.asp
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8b76678b1e5c0f53502e24f8baee87ede3bd3ef6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860174"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>如何：設定 managed 程式碼的舊版分析

在 Visual Studio 中，您可以從要套用至 managed 程式碼專案的程式碼分析 [規則集](../code-quality/rule-set-reference.md) 清單中進行選擇。 預設會選取 [ **Microsoft 最低建議規則** ] 規則集，但您可以視需要套用不同的規則集。 規則集可以套用至方案中的一個或多個專案。

> [!NOTE]
> 本文適用于舊版分析，而不是以 [.NET Compiler Platform 為基礎的程式碼分析器](use-roslyn-analyzers.md)。

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>設定 .NET Framework 專案的規則集

1. 開啟專案屬性頁上的 [程式 **代碼分析** ] 索引標籤。 您可以使用下列其中一種方法執行這個動作：

   - 在 **方案總管** 中，選擇專案。 在功能表列上，選取 [**分析**  >  **設定**  >  **程式 \<projectname>** 代碼分析]。

   - 以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [ **屬性**]，再選取 [程式 **代碼分析** ] 索引標籤。

2. 在 [設定] 和 [**平臺**] 清單中，選擇 [組建設定 **] 和 [** 目標平臺]。

::: moniker range="vs-2017"

3. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [ **在組建時啟用程式碼分析**]。 您也可以選取 [**分析**  >  **執行程式碼分析**  >  **\<projectname> 執行** 程式碼分析]，手動執行程式碼分析。

::: moniker-end

::: moniker range=">=vs-2019"

3. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [**二進位分析器**] 區段中的 [**在組建上執行**]。 您也可以手動執行舊版程式碼分析，請參閱 [如何：針對 Managed 程式碼手動執行舊版程式碼分析](how-to-run-legacy-code-analysis-manually-for-managed-code.md) ，以取得更多詳細資料。

::: moniker-end

4. 若要從產生的程式碼中查看警告，請清除 [ **隱藏產生** 的程式碼的結果] 核取方塊。

    > [!NOTE]
    > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時查看和維護表單或範本的原始程式碼，而不會覆寫該程式碼。

::: moniker range="vs-2017"

5. 在 [ **執行此規則集** ] 清單中，執行下列其中一項：

::: moniker-end

::: moniker range=">=vs-2019"

5. 在 [作用中 **規則** ] 清單中，執行下列其中一項：

::: moniker-end

   - 選取您要使用的規則集。

   - 選取 **\<Browse>** 以尋找不在清單中的現有自訂規則集。

   - 定義 [自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)。

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>為方案中的多個專案指定規則集

依預設，會將 *Microsoft 的最低建議規則* 程式碼分析規則集指派給解決方案的所有受管理專案。 您可以在方案的 [ **屬性** ] 對話方塊中，變更指派給方案專案的規則集。

1. 在 Visual Studio 中開啟解決方案。

2. 在 [ **分析** ] 功能表上，選取 [ **設定解決方案的程式碼分析**]。

3. 如有必要，請展開 [ **通用屬性**]，然後選取 [程式 **代碼分析設定**]。

4. 您可以為一或多個專案指定規則集：

    - 若要指定個別專案的規則集，請選擇專案名稱。

    - 若要指定多個專案的規則集，請選取 **Ctrl** 和專案名稱。

    - 若要指定方案中的所有專案，請選取 [下 **移** ] 和 [專案清單]。

5. 選取專案的 [ **規則集** ] 欄位，然後選取您想要套用之規則集的名稱。

## <a name="see-also"></a>另請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)
