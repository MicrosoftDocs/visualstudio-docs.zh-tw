---
title: 使用程式碼分析來分析受控碼品質 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d5f0646f26226e9895414db512681e0a7a71faa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671109"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>使用程式碼分析進行 Managed 程式碼品質分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio 中的程式碼分析工具找出程式碼中的潛在問題，例如不安全的資料存取、使用情況違規，以及設計問題。 程式碼分析適用于 .NET Framework、原生（ C++C 和）和資料庫應用程式。 受控碼的程式碼分析會在以特定編碼問題為目標的*規則集中*，組織規則。

## <a name="common-tasks"></a>一般工作

|一般工作|支援內容|
|------------------|------------------------|
|**取得實際操作練習：** 藉由修正簡單 .NET Framework 應用程式中的瑕疵，來瞭解程式碼分析的基本概念。|-   [逐步解說：分析受控碼的程式碼](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)缺失|
|**設定專案的程式碼分析：** Managed 程式碼的規則會組織成以特定區域（例如安全性和設計）為目標的規則集。 您可以使用其中一個 Microsoft standard 規則集，或自行建立。|[適用于受控碼的 -    程式碼分析總覽](../code-quality/code-analysis-for-managed-code-overview.md)<br />[使用規則集來分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)-   <br />-   [使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**執行程式碼分析：** 您可以指定要在每次建立專案設定時自動執行程式碼分析，也可以在專案上手動執行程式碼分析。|-   [如何：啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [如何：手動執行程式碼分析](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**分析程式碼分析結果：** 程式碼分析警告和錯誤會列在 [程式碼分析] 視窗中。 您可以選擇警告或錯誤標題，以顯示警告的其他相關資訊，並顯示並反白顯示引發規則的源程式碼。 您可以選擇警告識別碼以顯示 MSDN Library 中的詳細資訊，其中包含如何解決問題的資訊和範例。|-   [如何：查看 Managed 程式碼](../code-quality/how-to-view-managed-code-defects.md)缺失<br />[適用于受控碼的 -    程式碼分析警告](../code-quality/code-analysis-for-managed-code-warnings.md)<br />[依 CheckId -    警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)|
|**將程式碼分析與您的開發生命週期整合：** @No__t_1 中的簽入原則可讓開發小組確保所有程式碼簽入都符合一組通用的程式碼分析標準。 建立程式碼分析規則違規的工作專案，是您可以在錯誤清單視窗中執行的簡單程式。|-   [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [如何：同步處理常式代碼專案規則集與 Team 專案簽入原則](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [如何：為 Managed 程式碼的缺失建立工作專案](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
