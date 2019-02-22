---
title: HOW TO：以程式設計方式搜尋特定的連絡人
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: feff583d28bf53f4bffc9b425d52902688b80a4b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607157"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>HOW TO：以程式設計方式搜尋特定的連絡人
  下列範例會在 Outlook 的 [連絡人] 資料夾中，先依名字再依姓氏來搜尋特定連絡人。 該範例假設 [連絡人] 資料夾中有名為 **John Evans** 的連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>另請參閱
- [使用連絡人項目](../vsto/working-with-contact-items.md)
- [開始進行程式設計 VSTO 增益集](../vsto/getting-started-programming-vsto-add-ins.md)
