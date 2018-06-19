---
title: 設定 Visual Studio 中的程式碼分析
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: afa7a75ae083133f2cff1197b2aa111a1d7bf719
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918752"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>如何：設定 Managed 程式碼專案的程式碼分析

在 Visual Studio 中，您可以從清單中選擇程式碼分析*規則集*套用至 managed 程式碼專案。 預設規則集是*Microsoft 最小建議規則*。 您可以套用另一個規則集對專案或方案中的所有專案。

> [!TIP]
> 如需如何設定 ASP.NET Web 應用程式設定的規則資訊，請參閱[How to： 設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)。

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>若要設定的規則集的.NET Framework 專案

1. 開啟**程式碼分析**專案屬性頁 索引標籤。 您可以透過下列方式之一：

   - 在**方案總管 中**，選取專案。 在功能表列上，選取**分析** > **設定程式碼分析** > **如\<projectname >**。

   - 中的專案上按一下滑鼠右鍵**方案總管 中**選取**屬性**，然後選取**程式碼分析** 索引標籤。

1. 在**組態**和**平台**清單中，選取組建組態和目標平台。

1. 若要每次使用選取的組態建置專案時執行程式碼分析，請選取**建置時啟用程式碼分析**核取方塊。 您也可以執行程式碼分析手動選取**分析** > **執行程式碼分析** > **上執行程式碼分析\<projectname >**.

1. 根據預設，程式碼分析不會報告從外部工具自動產生的程式碼警告。 若要檢視產生的程式碼的警告，請清除**隱藏來自產生的程式碼的結果**核取方塊。

    > [!NOTE]
    > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以檢視及維護表單或範本的原始程式碼，而不需要覆寫它。

1. 在**執行此規則集**清單中，執行下列其中一項：

    - 選取您想要使用的規則集。

    - 選取**\<瀏覽 >** ，尋找現有的自訂規則集不在清單中。

    - 定義[自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)。

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>在方案中指定多個專案的規則集

根據預設，會指派方案的所有 managed 的專案*Microsoft 最小建議規則*程式碼分析規則集。 您可以變更指派給專案的方案中的規則集**屬性**解決方案的對話方塊。

1. 在 Visual Studio 中開啟方案。

2. 在**分析**功能表上，選取**設定方案的程式碼分析**。

3. 如果有必要，請展開**通用屬性**，然後選取**程式碼分析設定**。

4. 您可以指定規則集的一個或多個專案：

    - 若要指定個別的專案中設定的規則，請選取專案名稱。

    - 若要指定規則集的多個專案，請按住**Ctrl**和選取的專案名稱。

    - 若要指定方案中的所有專案，請按住**Shift** ，然後按一下 [專案] 清單中。

5. 選取**規則集**專案時，欄位，然後選取設定您想要套用規則的名稱。

## <a name="see-also"></a>另請參閱

- [如何：設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)