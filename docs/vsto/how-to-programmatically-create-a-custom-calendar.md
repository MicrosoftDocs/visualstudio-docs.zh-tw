---
title: 如何：以程式設計方式建立自訂行事曆
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: aab9e14c7fa4b4c70b2e61eca382af2ce787148c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546051"
---
# <a name="how-to-programmatically-create-a-custom-calendar"></a>如何：以程式設計方式建立自訂行事曆
  這個範例會建立名為 **PersonalCalendar**的新行事曆資料夾，然後建立新的約會專案並將它加入行事曆資料夾中。 然後，程式碼會顯示行事曆資料夾。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_CustomCalendar#1](../vsto/codesnippet/CSharp/Trin_OL_CustomCalendar/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用行事曆專案](../vsto/working-with-calendar-items.md)
- [如何：以程式設計方式建立約會](../vsto/how-to-programmatically-create-appointments.md)
- [如何：以程式設計方式建立會議邀請](../vsto/how-to-programmatically-create-a-meeting-request.md)
