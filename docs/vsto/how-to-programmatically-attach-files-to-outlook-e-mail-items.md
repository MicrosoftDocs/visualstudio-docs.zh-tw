---
title: 如何：以程式設計方式將檔案附加至 Outlook 電子郵件專案
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2427ffc634976462e27eb788259184ce69347769
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585323"
---
# <a name="how-to-programmatically-attach-files-to-outlook-email-items"></a>如何：以程式設計方式將檔案附加至 Outlook 電子郵件專案
  此範例會將檔案附加至新的訊息項目，並將其傳送至 Armando Pinto。 此範例假設有一個名為 Armando Pinto 的人員做為收件者。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_AttachFiles/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_AttachFiles/thisaddin.vb#1)]

## <a name="see-also"></a>另請參閱
- [使用訊息項目](../vsto/working-with-mail-items.md)
- [如何：以程式設計方式傳送電子郵件](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [如何：以程式設計方式從 Outlook 電子郵件專案儲存附件](../vsto/how-to-programmatically-save-attachments-from-outlook-e-mail-items.md)
- [如何：以程式設計方式建立電子郵件專案](../vsto/how-to-programmatically-create-an-e-mail-item.md)
