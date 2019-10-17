---
title: 設定程式碼分析
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f1bfa8c6e5260fb4afd20b882e2bdfc718647f4b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448977"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>如何：設定 managed 程式碼的舊版分析

在 Visual Studio 中，您可以選擇要套用至 managed 程式碼專案的程式碼分析[規則集](../code-quality/rule-set-reference.md)清單。 根據預設，會選取 [ **Microsoft 最低建議規則**] 規則集，但您可以視需要套用不同的規則集。 規則集可以套用至方案中的一個或多個專案。

> [!NOTE]
> 本文適用于舊版分析，而不適用於以[.NET Compiler Platform 為基礎的程式碼分析器](use-roslyn-analyzers.md)。

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>為 .NET Framework 專案設定規則集

1. 開啟專案屬性頁上的 [程式**代碼分析**] 索引標籤。 您可以透過下列其中一種方式來執行這項操作：

   - 在 **方案總管**中，選取專案。 在功能表列上，選取 [**分析** > ] [**設定程式碼分析**]  > **以進行 @no__t 5projectname >** 。

   - 以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**屬性**]，再選取 [程式**代碼分析**] 索引標籤。

2. 在 [設定]**和 [** **平臺**] 清單中，選取 [組建設定] 和 [目標平臺]。

::: moniker range="vs-2017"

3. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [**在組建上啟用程式碼分析**]。 您也可以手動執行程式碼分析，方法是選取 [**分析**] [ > ] [**執行程式碼**分析]  > **在 \<Projectname > 上執行程式碼分析**。

::: moniker-end

::: moniker range=">=vs-2019"

3. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [**二進位分析器**] 區段中的 [**在組建上執行**]。 您也可以手動執行程式碼分析，方法是選取 [**分析**] [ > ] [**執行程式碼**分析]  > **在 \<Projectname > 上執行程式碼分析**。

::: moniker-end

4. 若要從產生的程式碼中查看警告，請清除 [**隱藏產生的程式碼的結果**] 核取方塊。

    > [!NOTE]
    > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時查看和維護表單或範本的原始程式碼，而不會覆寫它。

::: moniker range="vs-2017"

5. 在 [**執行此規則集**] 清單中，執行下列其中一項：

::: moniker-end

::: moniker range=">=vs-2019"

5. 在 [作用中**規則**] 清單中，執行下列其中一項：

::: moniker-end

    - 選取您想要使用的規則集。

    - 選取 [ **\<Browse >** ]，尋找不在清單中的現有自訂規則集。

    - 定義[自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)。

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>為方案中的多個專案指定規則集

根據預設，解決方案的所有 managed 專案都會被指派*Microsoft 最低建議規則*程式碼分析規則集。 您可以在方案的 [**屬性**] 對話方塊中，變更指派給方案專案的規則集。

1. 在 Visual Studio 中開啟方案。

2. 在 [**分析**] 功能表上，選取 [**設定方案的程式碼分析**]。

3. 如有必要，請展開 [**通用屬性**]，然後選取 [程式**代碼分析設定**]。

4. 您可以為一個或多個專案指定規則集：

    - 若要為個別專案指定規則集，請選取專案名稱。

    - 若要為多個專案指定規則集，請按住**Ctrl 鍵**並選取專案名稱。

    - 若要指定方案中的所有專案，請按住**Shift 鍵**，然後按一下專案清單。

5. 選取專案的 [**規則集**] 欄位，然後選取您想要套用之規則集的名稱。

## <a name="see-also"></a>請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)
