---
title: 如何：以程式設計方式搜尋特定的連絡人
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d8b2302586fc09fcfec6420d97374197eae7e67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547065"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>如何：以程式設計方式搜尋特定的連絡人
  下列範例會在 Outlook 的 [連絡人] 資料夾中，先依名字再依姓氏來搜尋特定連絡人。 該範例假設 [連絡人] 資料夾中有名為 **John Evans** 的連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>另請參閱
- [使用連絡人項目](../vsto/working-with-contact-items.md)
- [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)
