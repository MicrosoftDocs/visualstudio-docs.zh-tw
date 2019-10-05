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
ms.openlocfilehash: 86aa308369ef93792126c7f8da5f59f94ef0c02a
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975108"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>HOW TO：設定 managed 程式碼的舊版分析

在 Visual Studio 中，您可以選擇要套用至 managed 程式碼專案的程式碼分析[規則集](../code-quality/rule-set-reference.md)清單。 根據預設， **Microsoft 最小建議規則**選取規則集，但您可以套用不同的規則集有需要。 規則集可以套用至解決方案中的一或多個專案中。

> [!NOTE]
> 本文適用于舊版分析，而不適用於以[.NET Compiler Platform 為基礎的程式碼分析器](use-roslyn-analyzers.md)。

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>為 .NET Framework 專案設定規則集

1. 開啟**程式碼分析**上專案屬性頁 索引標籤。 您可以下列兩種方法之一來這麼做：

   - 在 [**方案總管] 中**，選取專案。 在功能表列上選取**分析** > **設定程式碼分析** > **如\<專案名稱 >** 。

   - 中的專案上按一下滑鼠右鍵**方案總管**，然後選取**屬性**，然後選取**程式碼分析** 索引標籤。

2. 在 **組態**並**平台**清單中，選取組建組態和目標平台。

::: moniker range="vs-2017"

3. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [**在組建上啟用程式碼分析**]。 您也可以執行程式碼分析以手動方式選取**分析** > **執行程式碼分析** > **上執行程式碼分析\<專案名稱 >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [**二進位分析器**] 區段中的 [**在組建上執行**]。 您也可以執行程式碼分析以手動方式選取**分析** > **執行程式碼分析** > **上執行程式碼分析\<專案名稱 >** .

::: moniker-end

4. 若要檢視產生程式碼的警告，請清除**隱藏所產生的程式碼的結果** 核取方塊。

    > [!NOTE]
    > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時查看和維護表單或範本的原始程式碼，而不會覆寫它。

::: moniker range="vs-2017"

5. 在 **執行此規則集**清單中，執行下列其中之一：

::: moniker-end

::: moniker range=">=vs-2019"

5. 在 [作用中**規則**] 清單中，執行下列其中一項：

::: moniker-end

    - 選取您想要使用的規則集。

    - 選取 [ **\<Browse >** ]，尋找不在清單中的現有自訂規則集。

    - 定義[自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)。

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>在方案中指定多個專案的規則集

根據預設，指派方案的所有 managed 的專案*Microsoft 最小建議規則*程式碼分析規則集。 您可以變更指派給專案的方案中的規則集**屬性**解決方案的對話方塊。

1. 在 Visual Studio 中開啟方案。

2. 在上**分析**功能表上，選取**設定為方案的程式碼分析**。

3. 如果有必要，請依序展開**通用屬性**，然後選取**程式碼分析設定**。

4. 您可以指定規則集的一個或多個專案：

    - 若要指定的規則集的個別專案，選取 專案名稱。

    - 若要指定規則集的多個專案，請按住**Ctrl** ，然後選取 專案名稱。

    - 若要在方案中指定的所有專案，請按住**Shift** ，按一下 [專案] 清單中。

5. 選取 **規則集**欄位的專案，然後再選取設定您想要套用規則的名稱。

## <a name="see-also"></a>另請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)