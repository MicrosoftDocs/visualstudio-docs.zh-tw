---
title: 以程式設計方式從收件匣取得未讀取的訊息
description: 瞭解如何使用 Visual Studio，以程式設計方式從 Microsoft Outlook 中的收件匣取出未讀取的訊息。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6dae629c008c04f7ee9fb66b9dbc5f8f31e53d4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528262"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>如何：以程式設計方式從收件匣取出未讀取的訊息
  此範例會從 Outlook **收件** 匣抓取未閱讀的電子郵件訊息，並顯示專案數。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用訊息項目](../vsto/working-with-mail-items.md)
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
- [如何：以程式設計方式建立電子郵件專案](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [如何：以程式設計方式傳送電子郵件](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
