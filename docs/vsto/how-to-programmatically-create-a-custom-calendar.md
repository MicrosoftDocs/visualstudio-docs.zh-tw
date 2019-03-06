---
title: HOW TO：以程式設計方式建立自訂行事曆
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom calendars [Office development in Visual Studio]
- calendars [Office development in Visual Studio], custom
- appointments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 653340d3a682664670998c874344bfc931105892
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624772"
---
# <a name="how-to-programmatically-create-a-custom-calendar"></a>HOW TO：以程式設計方式建立自訂行事曆
  這個範例會建立新行事曆 資料夾名為**PersonalCalendar**，然後建立新的約會項目，並將它新增至行事曆 資料夾。 程式碼接著會顯示行事曆 資料夾。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_CustomCalendar#1](../vsto/codesnippet/CSharp/Trin_OL_CustomCalendar/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用行事曆項目](../vsto/working-with-calendar-items.md)
- [如何：以程式設計方式建立約會](../vsto/how-to-programmatically-create-appointments.md)
- [如何：以程式設計方式建立會議邀請](../vsto/how-to-programmatically-create-a-meeting-request.md)
