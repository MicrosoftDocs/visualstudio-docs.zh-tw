---
title: 使用規則集將程式碼分析規則分組 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603472"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>使用規則集分組程式碼分析規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您在、或中設定程式碼分析時 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vsPro](../includes/vspro-md.md)] ，可以從 Microsoft 內建 *規則集*的清單中選擇。 規則集是程式碼分析規則的邏輯群組，用來識別目標問題和特定條件。 例如，您可以套用設計用來掃描公開可用 Api 程式碼的規則集，也可以套用只包含最低建議規則的規則集。 您也可以套用包含所有規則的規則集。

 您可以藉由新增或刪除規則來自訂規則集，或將規則變更為在 [ **錯誤清單** ] 視窗中顯示為警告或錯誤。 自訂規則集可以滿足您特定開發環境的需求。 當您自訂規則集時，[規則集] 頁面會提供搜尋和篩選工具，以協助您進行處理。

## <a name="common-tasks"></a>一般工作

|工作|相關內容|
|----------|---------------------|
|**取得實際操作實務：** 使用程式碼分析工具來指定自訂規則集，以找出並修正簡單 .NET Framework 應用程式中的問題。|-   [逐步解說：設定和使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**設定專案的程式碼分析：** 為專案、網站或方案選擇現有的規則集。|-   [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [使用規則集指定要執行的 c + + 規則](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [如何：設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [如何：為方案中的多個專案指定規則集](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**自訂規則集：** 指定要套用至專案的規則。|-   [建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**瞭解內建規則集：** 查看組成內建規則集的程式碼分析規則。|-   [程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)|
|**整合程式碼分析與 Team Foundation Server：** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] 簽入原則可讓開發小組確保所有程式碼簽入都符合一組常見的程式碼分析標準。|-   [如何：將程式碼專案規則集與 Team 專案簽入原則進行同步處理](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
