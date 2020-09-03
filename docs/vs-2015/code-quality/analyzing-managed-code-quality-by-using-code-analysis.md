---
title: 使用程式碼分析來分析 Managed 程式碼品質 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671109"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>使用程式碼分析進行 Managed 程式碼品質分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Visual Studio 中的程式碼分析工具找出程式碼中的潛在問題，例如不安全的資料存取、使用情況違規，以及設計問題。 程式碼分析適用于 .NET Framework、原生 (C 和 c + +) 和資料庫應用程式。 Managed 程式碼的程式碼分析會 *將規則集中* 的規則組織成特定的程式碼撰寫問題。

## <a name="common-tasks"></a>一般工作

|一般工作|支援內容|
|------------------|------------------------|
|**取得實際操作實務：** 藉由更正簡單 .NET Framework 應用程式中的瑕疵，瞭解程式碼分析的基本概念。|-   [逐步解說：針對程式碼缺失分析 Managed 程式碼](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|
|**設定專案的程式碼分析：** Managed 程式碼的規則會組織成以特定區域（例如安全性和設計）為目標的規則集。 您可以使用其中一個 Microsoft 標準規則集，或建立自己的規則集。|-   [適用于 Managed 程式碼的程式碼分析總覽](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**執行程式碼分析：** 您可以指定在每次建立專案設定時自動執行程式碼分析，也可以在專案上手動執行程式碼分析。|-   [如何：啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [如何：手動執行程式碼分析](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**分析程式碼分析結果：** 程式碼分析警告和錯誤會列在 [程式碼分析] 視窗中。 您可以選擇警告或錯誤標題來顯示警告的其他相關資訊，以及顯示並反白顯示引發規則的源程式碼。 您可以選擇警告識別碼以顯示 MSDN Library 中的詳細資訊，其中包含如何解決問題的資訊和範例。|-   [如何：查看 Managed 程式碼瑕疵](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Managed 程式碼的程式碼分析警告](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [依 CheckId 的警告](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)|
|**整合程式碼分析與您的開發生命週期：** 中的簽入原則 [!INCLUDE[esprscc](../includes/esprscc-md.md)] 可讓開發小組確保所有程式碼簽入都符合一組常見的程式碼分析標準。 您可以在 [錯誤清單] 視窗中執行簡單的程式，以建立程式碼分析規則違規的工作專案。|-   [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [如何：將程式碼專案規則集與 Team 專案簽入原則進行同步處理](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [如何：為 Managed 程式碼缺失建立工作專案](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
