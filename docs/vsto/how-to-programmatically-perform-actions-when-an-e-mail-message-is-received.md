---
title: HOW TO：以程式設計方式在收到電子郵件訊息時執行動作
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], actions when e-mail is received
- NewMail event
- mail items [Office development in Visual Studio], custom actions
- e-mail [Office development in Visual Studio], custom actions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31f195d6b83a93363c3b2ef3bfa7d829f5fc822d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955936"
---
# <a name="how-to-programmatically-perform-actions-when-an-email-message-is-received"></a>HOW TO：以程式設計方式在收到電子郵件訊息時執行動作
  使用者會收到一封電子郵件時，此範例會執行自訂動作。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-vb[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_PerformActions/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_PerformActions/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [如何：建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [使用郵件項目](../vsto/working-with-mail-items.md)
- [開始進行程式設計 VSTO 增益集](../vsto/getting-started-programming-vsto-add-ins.md)
