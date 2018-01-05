---
title: "使用規則集分組程式碼分析規則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.rulesets.learnmore
helpviewer_keywords: code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 51b282cb86ca83ecf2ace1e4b12c8444928b15e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>使用規則集分組程式碼分析規則
當您設定中的程式碼分析[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]， [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]，或[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]，您可以從 Microsoft 內建的清單選擇*規則集*。 規則集是識別目標的問題和的特定狀況的程式碼分析規則的邏輯群組。 比方說，您可以將套用的規則集是設計用來掃描程式碼公開可用的應用程式開發介面，或您可以套用包含只有最小建議規則規則集。 您也可以套用的規則集包含的所有規則。  
  
 您可以自訂規則集中新增或刪除規則，或變更規則才會出現在**錯誤清單**為警告或錯誤視窗。 自訂的規則集可滿足特定的開發環境的需要。 當您自訂規則集時，規則設定頁面會提供搜尋和篩選工具，可協助您在程序中。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**進行實際操作練習：**使用程式碼分析工具，來指定自訂的規則已設定為找出並修正簡單的.NET Framework 應用程式中的問題。|-   [逐步解說： 設定及使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**設定專案的程式碼分析：**選擇現有規則設定的專案、 Web 站台或解決方案。|-   [如何： 設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [使用指定要執行的 c + + 規則規則集](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [如何： 設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [如何： 指定規則集的多個專案方案中](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**自訂規則集：**指定規則来套用至您的專案。|-   [建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**了解內建規則集：**檢視組成的內建規則集的程式碼分析規則。|-   [程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)|  
|**與 Team Foundation Server 整合程式碼分析：** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]簽入原則，可讓開發團隊，以確定所有的程式碼簽入符合一組常用的程式碼分析的標準。|-   [如何： 同步處理具有 Team 專案簽入原則的程式碼專案規則集](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|