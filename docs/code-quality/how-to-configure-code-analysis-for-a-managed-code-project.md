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
ms.openlocfilehash: 466178015c725242b6bc4a28da1da6ded19b421f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916787"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>HOW TO：設定受控碼專案的程式碼分析

在 Visual Studio 中，您可以從清單中選擇的程式碼分析[規則集](../code-quality/rule-set-reference.md)) 套用至 managed 程式碼專案。 根據預設， **Microsoft 最小建議規則**選取規則集，但您可以套用不同的規則集有需要。 規則集可以套用至解決方案中的一或多個專案中。

> [!TIP]
> 如需如何設定 ASP.NET web 應用程式設定的規則的詳細資訊，請參閱[How to:設定 ASP.NET web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)。

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>若要設定的規則集的.NET Framework 專案

1. 開啟**程式碼分析**上專案屬性頁 索引標籤。 您可以下列兩種方法之一來這麼做：

   - 在 [**方案總管] 中**，選取專案。 在功能表列上選取**分析** > **設定程式碼分析** > **如\<專案名稱 >**。

   - 中的專案上按一下滑鼠右鍵**方案總管**，然後選取**屬性**，然後選取**程式碼分析** 索引標籤。

1. 在 **組態**並**平台**清單中，選取組建組態和目標平台。

1. 若要執行程式碼分析，每次使用選取的組態建置專案時，請選取**建置時啟用程式碼分析**核取方塊。 您也可以執行程式碼分析以手動方式選取**分析** > **執行程式碼分析** > **上執行程式碼分析\<專案名稱 >**.

1. 根據預設，程式碼分析不會報告從外部工具自動產生的程式碼警告。 若要檢視產生程式碼的警告，請清除**隱藏所產生的程式碼的結果** 核取方塊。

    > [!NOTE]
    > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以檢視和維護表單或範本的原始程式碼，而不需要覆寫它。

1. 在 **執行此規則集**清單中，執行下列其中之一：

    - 選取您想要使用的規則集。

    - 選取 [ **\<瀏覽] >** ，尋找現有的自訂規則集不在清單中。

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
- [如何：設定 ASP.NET web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)