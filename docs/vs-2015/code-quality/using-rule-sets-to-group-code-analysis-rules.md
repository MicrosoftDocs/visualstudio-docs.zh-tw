---
title: 使用規則集分組程式碼分析規則 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a8af8cbc27a61369640a80dbccb4d99dd2466f3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220580"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>使用規則集分組程式碼分析規則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您設定中的程式碼分析[!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]， [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]，或[!INCLUDE[vsPro](../includes/vspro-md.md)]，您可以從 Microsoft 內建清單中選擇*規則集*。 規則集是找出目標的問題及特定條件的程式碼分析規則的邏輯群組。 比方說，您可以將套用的規則集是設計用來公開可用的 Api，掃描程式碼，或您可以套用包含只有最小建議規則規則集。 您也可以套用的規則集包含所有規則。  
  
 您可以自訂規則集新增或刪除規則，或變更規則才會出現在**錯誤清單**為警告或錯誤視窗。 自訂的規則集可滿足您特定的開發環境的需求。 當您自訂規則集時，[規則集] 頁面會提供搜尋和篩選工具，可協助您在程序。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**進行實際操作練習：** 使用程式碼分析工具，來指定自訂規則集中找出並修正簡單的.NET Framework 應用程式中的問題。|-   [逐步解說： 設定及使用自訂規則集](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**設定專案的程式碼分析：** 選擇現有規則集的專案、 Web 站台或方案。|-   [如何： 設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [使用規則集指定要執行的 c + + 規則](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [如何： 設定 ASP.NET Web 應用程式的程式碼分析](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [如何： 指定的方案中的多個專案規則集](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**自訂規則集：** 指定規則来套用至您的專案。|-   [建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**了解內建規則集：** 檢視內建規則集所組成的程式碼分析規則。|-   [程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)|  
|**與 Team Foundation Server 整合程式碼分析：** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]簽入原則可讓開發小組必須確保所有的程式碼簽入符合一組常用的程式碼分析的標準。|-   [如何： 同步處理與 Team 專案簽入原則的程式碼專案規則集](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|



