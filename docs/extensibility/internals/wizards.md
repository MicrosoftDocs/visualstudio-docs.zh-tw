---
title: 嚮導 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703215"
---
# <a name="wizards"></a>精靈
創建精靈後,通常需要將其添加到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境(IDE),以便其他人可以使用它。 然後,添加的嚮導將顯示在「**添加新專案**」或 **「新增新專案」** 對話框中。 要檢視「**新增新專案**」 或 **「新增新專案」** 對話框,請右鍵單擊**解決方案資源管理器**中的打開解決方案,指向 **「新增**」,然後按一下新**專案**「或 **」新專案**」。

 嚮導可以實現,以便使用者[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在打開 **「添加新項目**」對話方塊或 **「新增新專案**」對話框時,或在**解決方案資源管理器**中右鍵單擊專案時,從可用值的樹視圖中選擇。

 在嚮導中,可以提供當地語系化新專案或 ites 名稱的選項,還可以確定使用者在選擇精靈時將看到的圖示。 您還可以控制新專案相對於其他可用項的顯示順序;專案不必按字母順序排列。

 還可以提供不同啟動的嚮導,該嚮導基於打開嚮導時傳遞給嚮導的自定義參數。

 本節中的主題討論您實現的檔,以便導致[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**「添加新專案和****添加新專案」** 對話方塊,以在可用的嚮導和範本中列出嚮導,以及嚮導必須滿足的要求才能在 IDE 中正常運行。

## <a name="in-this-section"></a>本節內容
- [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 提供哪些範本目錄描述檔的概述,並解釋它們如何在IDE中工作以顯示對話方塊中與專案關聯的資料夾、嚮導 .vsz 文件和範本檔。

- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 解釋 IDE 如何啟動精靈並列出 .vsz 檔的三個部分。

- [精靈介面 (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 描述精靈`IDTWizard`在 IDE 中工作時必須實現的介面。

- [內容參數](../../extensibility/internals/context-parameters.md)

 說明如何實現嚮導,以及當IDE將上下文參數傳遞給實現時會發生什麼。

- [自訂參數](../../extensibility/internals/custom-parameters.md)

 說明在嚮導啟動后如何使用自定義參數來控制嚮導的操作。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 提供指向其他主題的連結,這些主題提供有關如何設計新項目類型的資訊。

- [擴充專案](../../extensibility/extending-projects.md)

 描述如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案和解決方案組織程式碼檔案和資源檔，以及如何實作原始檔控制。
