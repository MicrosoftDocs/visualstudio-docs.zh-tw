---
title: .ofs 檔案的一個或多個屬性對於所選取的訊息類別是無效的
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692495"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs 檔案的一個或多個屬性對於所選取的訊息類別是無效的
  當您匯入在 Outlook 中設計的表單區域時，會出現這個錯誤，但在表單區域上的一個或多個欄位，與不相容的最後一頁選取的訊息類別**新表單區域**精靈。  

例如，您可能會在 [新增表單區域精靈]  的最後一頁選取 [工作 (IPM.Task)]  。 如果表單區域**商務地址**欄位，您會收到這個錯誤，因為工作沒有商務地址。 因此，**商務地址**欄位與不相容`IPM.Task`訊息類別。  
  
 您可能會選取**工作 (IPM。工作）** 的最後一頁上**新表單區域**精靈。 如果表單區域**商務地址**欄位，您會收到這個錯誤，因為工作沒有商務地址。 因此，**商務地址**欄位與不相容`IPM.Task`訊息類別。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   在 [新增表單區域精靈]  的最後一頁，選取與表單區域上的欄位相容的訊息類別。  
  
-   在表單設計工具在 Outlook 中，移除欄位，與訊息類別不相容。 移除您計劃的最後一頁選取的欄位**新表單區域**精靈。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  