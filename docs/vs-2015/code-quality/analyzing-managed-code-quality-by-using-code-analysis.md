---
title: 使用程式碼分析，分析 Managed 程式碼品質 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e0538c47dec2dd11b9488a80dd4f71baddc487f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485516"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>使用程式碼分析進行 Managed 程式碼品質分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[分析 Managed 程式碼品質所使用的程式碼分析](https://docs.microsoft.com/visualstudio/code-quality/analyzing-managed-code-quality-by-using-code-analysis)。  
  
您可以使用 Visual Studio 中的程式碼分析工具找出程式碼中的潛在問題，例如不安全的資料存取、使用情況違規，以及設計問題。 程式碼分析適用於.NET Framework、 原生 （C 和 c + +） 和資料庫應用程式。 Managed 程式碼的程式碼分析組織中的規則*規則集*目標特定程式碼的問題。  
  
## <a name="common-tasks"></a>一般工作  
  
|一般工作|支援內容|  
|------------------|------------------------|  
|**進行實際操作練習：** 學習藉由修正缺失簡單的.NET Framework 應用程式中的程式碼分析的基本概念。|-   [逐步解說： 分析 Managed 程式碼的程式碼缺失](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**設定專案的程式碼分析：** 規則用於 managed 程式碼會組織成以特定方面，例如安全性和設計為目標的規則集。 您可以使用其中一個 Microsoft 標準規則設定，或建立您自己。|-   [程式碼分析 Managed 程式碼概觀](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**執行程式碼分析：** 您可以指定自動執行建置的專案組態時，每次程式碼分析，而且您可以在專案上，手動執行程式碼分析。|-   [如何： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [如何： 以手動方式執行程式碼分析](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**分析程式碼分析結果：** 程式碼分析 視窗中列出的程式碼分析警告和錯誤。 您可以選擇警告或錯誤標題以顯示其他資訊的相關警告，並顯示，並反白顯示引發此規則的原始程式的程式碼行。 您可以選擇警告識別碼，顯示在 MSDN Library，包含資訊和範例，示範如何解決此問題的詳細的資訊。|-   [如何： 檢視 Managed 程式碼的缺失](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Managed 程式碼警告的程式碼分析](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [依據 checkid 列出警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**整合您開發生命週期中的程式碼分析：** 中的簽入原則[!INCLUDE[esprscc](../includes/esprscc-md.md)]啟用開發小組必須確保所有程式碼簽入符合一組常用的程式碼分析的標準。 建立程式碼分析規則違規的工作項目是簡單的程序，您可以在 [錯誤清單] 視窗中執行。|-   [使用 Team 專案簽入原則的增強程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [如何： 同步處理與 Team 專案簽入原則的程式碼專案規則集](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [如何： 為 Managed 程式碼缺失建立工作項目](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|



