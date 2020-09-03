---
title: 如何：設定 Managed 程式碼專案的程式碼分析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658851"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>如何：設定 Managed 程式碼專案的程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 和中 [!INCLUDE[vsPro](../includes/vspro-md.md)] ，您可以從要套用至 managed 程式碼專案的程式碼分析 *規則集* 清單中進行選擇。 預設規則集是 Microsoft 建議的最低規則。 您可以將另一個規則集套用至專案或方案中的所有專案。

> [!NOTE]
> 如需有關如何設定 ASP.NET Web 應用程式之規則集的詳細資訊，請參閱 how [to：設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)。

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>設定 .NET Framework 專案的規則集

1. 在 **方案總管**中，按一下專案。

2. 在 [**分析**] 功能表上，按一下 [設定*專案名稱***的程式碼分析**]。

3. **在 [設定**] 和 [**平臺**] 清單中，按一下 [組建設定] 和 [目標平臺]。

4. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [ **在組建上啟用程式碼分析] (定義 CODE_ANALYSIS 常數) ** 核取方塊。 您也可以開啟 [**分析**] 功能表，然後按一下 [在*專案名稱***上執行程式碼分析**]，手動執行程式碼分析。

5. 根據預設，程式碼分析不會報告從外部工具自動產生的程式碼警告。 若要從產生的程式碼中查看警告，請清除 [ **隱藏產生** 的程式碼的結果] 核取方塊。

    > [!NOTE]
    > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時檢視及維護表單或範本的原始程式碼。

6. 在 [ **執行此規則集** ] 清單中，執行下列其中一項：

    - 按一下您想要使用的規則集。

    - 按一下 **\<Browse...>** 以指定不在清單中的現有自訂規則集。

    - 定義自訂規則集。

         如需詳細資訊，請參閱 [建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。

## <a name="see-also"></a>另請參閱
 [逐步解說：設定和使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
