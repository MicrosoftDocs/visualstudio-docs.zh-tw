---
title: 如何：以程式設計方式刪除約會
description: 瞭解如何在 Microsoft Outlook 中以程式設計方式刪除 apppointments。 本範例會刪除一個週期性約會執行個體。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- calendars [Office development in Visual Studio], deleting appointments
- deleting appointments
- appointments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0520014edc97f7517338652fa89e4c8269ba552c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963922"
---
# <a name="how-to-programmatically-delete-appointments"></a>如何：以程式設計方式刪除約會
  本範例會刪除一個週期性約會執行個體。 本範例假設有個週期性約會執行個體發生於 2006 年 6 月 28 日 08:00。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-vb[Trin_Outlook_RL_DeleteAppointment#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_DeleteAppointment/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_DeleteAppointment#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_DeleteAppointment/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用行事曆專案](../vsto/working-with-calendar-items.md)
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
- [如何：以程式設計方式建立約會](../vsto/how-to-programmatically-create-appointments.md)
- [如何：以程式設計方式建立自訂行事曆](../vsto/how-to-programmatically-create-a-custom-calendar.md)
- [如何：以程式設計方式建立會議邀請](../vsto/how-to-programmatically-create-a-meeting-request.md)
