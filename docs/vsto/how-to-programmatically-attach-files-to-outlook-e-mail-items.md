---
title: HOW TO：以程式設計方式將檔案附加至 Outlook 電子郵件項目
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 707c3bb2b6bec9f8db1744d1f28acd4e90a45a57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575620"
---
# <a name="how-to-programmatically-attach-files-to-outlook-email-items"></a>HOW TO：以程式設計方式將檔案附加至 Outlook 電子郵件項目
  此範例會將檔案附加至新的郵件項目，並將它傳送至 Armando Pinto。 本範例假設名為 Armando Pinto 人員做為接收者。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_AttachFiles/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_AttachFiles/thisaddin.vb#1)]

## <a name="see-also"></a>另請參閱
- [使用郵件項目](../vsto/working-with-mail-items.md)
- [如何：以程式設計方式傳送電子郵件](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [如何：以程式設計方式儲存附件，從 Outlook 電子郵件項目](../vsto/how-to-programmatically-save-attachments-from-outlook-e-mail-items.md)
- [如何：以程式設計方式建立電子郵件項目](../vsto/how-to-programmatically-create-an-e-mail-item.md)
