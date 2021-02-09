---
title: Message 類別的 .ofs 檔案中有不正確屬性 "
description: 瞭解如何修正當 .ofs 檔案中的一或多個屬性對選取的訊息類別無效時，所發生的錯誤。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b22870cdb038adee84adc0fd7a56c269cb048626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841909"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Message 類別的 .ofs 檔案中有不正確屬性

  當您匯入在 Outlook 中設計的表單區域，但表單區域上的一或多個欄位與您在 [ **新表單區域** wizard] 的最後一頁選取的訊息類別不相容時，就會出現「.ofs 檔案中的一或多個屬性對於所選取的訊息類別無效」的錯誤。

例如，您可能會在 [新增表單區域精靈]  的最後一頁選取 [工作 (IPM.Task)]  。 如果表單區域具有 [ **商務位址** ] 欄位，您將會收到此錯誤，因為工作沒有商務位址。 因此，[ **商務位址** ] 欄位與 `IPM.Task` 訊息類別不相容。

 您可以選取 [工作 **(IPM]。****新表單區域** wizard 最後一頁的工作) 。 如果表單區域具有 [ **商務位址** ] 欄位，您將會收到此錯誤，因為工作沒有商務位址。 因此，[ **商務位址** ] 欄位與 `IPM.Task` 訊息類別不相容。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 在 [新增表單區域精靈]  的最後一頁，選取與表單區域上的欄位相容的訊息類別。

- 在 Outlook 的表單設計工具中，移除與訊息類別不相容的欄位。 在 **新的表單區域** wizard 的最終頁面上，移除您打算選取的欄位。

## <a name="see-also"></a>另請參閱
- [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
