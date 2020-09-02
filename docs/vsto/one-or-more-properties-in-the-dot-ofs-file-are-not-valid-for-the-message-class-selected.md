---
title: .ofs 檔案的一個或多個屬性對於所選取的訊息類別是無效的
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977857"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs 檔案的一個或多個屬性對於所選取的訊息類別是無效的
  當您匯入在 Outlook 中設計的表單區域，但表單區域上的一或多個欄位與您在 [ **新表單區域** wizard] 的最後一頁選取的訊息類別不相容時，就會出現這個錯誤。

例如，您可能會在 [新增表單區域精靈] **** 的最後一頁選取 [工作 (IPM.Task)] **** 。 如果表單區域具有 [ **商務位址** ] 欄位，您將會收到此錯誤，因為工作沒有商務位址。 因此，[ **商務位址** ] 欄位與 `IPM.Task` 訊息類別不相容。

 您可以選取 [工作** (IPM]。****新表單區域**wizard 最後一頁的工作) 。 如果表單區域具有 [ **商務位址** ] 欄位，您將會收到此錯誤，因為工作沒有商務位址。 因此，[ **商務位址** ] 欄位與 `IPM.Task` 訊息類別不相容。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 在 [新增表單區域精靈] **** 的最後一頁，選取與表單區域上的欄位相容的訊息類別。

- 在 Outlook 的表單設計工具中，移除與訊息類別不相容的欄位。 在 **新的表單區域** wizard 的最終頁面上，移除您打算選取的欄位。

## <a name="see-also"></a>另請參閱
- [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
