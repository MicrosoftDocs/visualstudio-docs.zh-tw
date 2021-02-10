---
title: 嚮導 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中列出您的 wizard 和範本，以及您的 wizard 在 IDE 中必須符合的需求。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 828a08cfe2841595e0ed3a9f1e3d79973a6e6756
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943377"
---
# <a name="wizards"></a>精靈
建立嚮導之後，您通常會想要將它加入至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) ，讓其他人可以使用它。 加入的 wizard 接著會出現在 [ **加入新專案** ] 或 [ **加入新** 專案] 對話方塊中。 若要查看 [ **加入新專案** ] 或 [ **加入新** 專案] 對話方塊，請以滑鼠右鍵按一下 **方案總管** 中開啟的方案，指向 [ **加入**]，然後按一下 [ **新增專案** ] 或 [ **新增專案**]。

 您可以在中執行嚮導 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，讓使用者在開啟 [ **加入新專案** ] 對話方塊或 [ **加入新** 專案] 對話方塊，或在 **方案總管** 中的專案上按一下滑鼠右鍵時，從可用值的樹狀檢視中進行選取。

 在您的 wizard 中，您可以提供將新專案或 ites 的名稱當地語系化的選項，也可以決定使用者在選取嚮導時會看到的圖示。 您也可以控制新專案相對於其他可用專案的顯示順序;專案不需要依字母順序組織。

 您也可以根據在開啟時傳遞給 wizard 的自訂參數，提供以不同方式啟動的 wizard。

 本章節中的主題會討論您所執行的檔案，使 [ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **加入新專案** ] 和 [ **加入新專案** ] 對話方塊可在可用的嚮導和範本中列出您的 wizard，以及您的 WIZARD 必須符合才能在 IDE 中正確運作的需求。

## <a name="in-this-section"></a>本節內容
- [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 提供範本目錄描述檔案的總覽，並說明這些檔案在 IDE 中的運作方式，以顯示資料夾、wizard .vsz 檔案，以及與對話方塊中專案相關聯的範本檔案。

- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 說明 IDE 如何啟動嚮導，並列出 .vsz 檔案的三個部分。

- [精靈介面 (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 描述 `IDTWizard` 嚮導必須在 IDE 中執行才能運作的介面。

- [內容參數](../../extensibility/internals/context-parameters.md)

 說明如何執行嚮導，以及當 IDE 將內容參數傳遞至執行時，會發生什麼事。

- [自訂參數](../../extensibility/internals/custom-parameters.md)

 說明如何使用自訂參數，在啟動嚮導之後控制 wizard 的操作。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 提供其他主題的連結，這些主題提供如何設計新專案類型的相關資訊。

- [擴充專案](../../extensibility/extending-projects.md)

 描述如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案和解決方案組織程式碼檔案和資源檔，以及如何實作原始檔控制。
