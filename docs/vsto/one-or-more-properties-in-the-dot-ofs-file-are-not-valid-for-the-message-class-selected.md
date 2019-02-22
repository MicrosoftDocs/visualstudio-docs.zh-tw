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
ms.openlocfilehash: 6b13352ca54db84137e029aa126f1f174a1c80fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621470"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs 檔案的一個或多個屬性對於所選取的訊息類別是無效的
  當您匯入在 Outlook 中設計表單區域時，就會出現此錯誤，但表單區域上的一或多個欄位不是與您選取的最後一頁的訊息類別相容**新的表單區域**精靈。

例如，您可能會在 [新增表單區域精靈]  的最後一頁選取 [工作 (IPM.Task)]  。 如果表單區域**商務地址**欄位中，您會收到這個錯誤，因為工作沒有商務地址。 因此，**商務地址**欄位與不相容`IPM.Task`訊息類別。

 您可以選取**工作 (IPM。工作）** 上的最後一頁**新的表單區域**精靈。 如果表單區域**商務地址**欄位中，您會收到這個錯誤，因為工作沒有商務地址。 因此，**商務地址**欄位與不相容`IPM.Task`訊息類別。

## <a name="to-correct-this-error"></a>更正這個錯誤

-   在 [新增表單區域精靈]  的最後一頁，選取與表單區域上的欄位相容的訊息類別。

-   在表單設計工具在 Outlook 中，移除與訊息類別不相容的欄位。 移除您打算在最後一頁選取的欄位**新的表單區域**精靈。

## <a name="see-also"></a>另請參閱
- [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
