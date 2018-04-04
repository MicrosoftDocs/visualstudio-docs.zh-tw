---
title: 如何： 設定 Managed 程式碼專案的程式碼分析 |Microsoft 文件
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 46d41b09f0f6639195613c8a4d9a08f952c79525
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
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

    - 定義自訂規則集。 如需詳細資訊，請參閱[建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：設定和使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
- [如何：設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)