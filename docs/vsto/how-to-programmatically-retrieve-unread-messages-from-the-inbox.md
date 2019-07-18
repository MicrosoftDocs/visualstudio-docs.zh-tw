---
title: 以程式設計方式從收件匣取得未讀取的訊息
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: b9a718d6a8ee4eb633b34e1e12f85d578dc99fa6
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328933"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>作法：以程式設計方式從收件匣中擷取未讀取的訊息
  此範例會擷取未讀取電子郵件訊息從 Outlook**收件匣**和顯示的項目數目。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用郵件項目](../vsto/working-with-mail-items.md)
- [開始進行程式設計 VSTO 增益集](../vsto/getting-started-programming-vsto-add-ins.md)
- [如何：以程式設計方式建立電子郵件項目](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [如何：以程式設計方式傳送電子郵件](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
