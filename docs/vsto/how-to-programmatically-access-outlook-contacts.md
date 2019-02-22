---
title: HOW TO：以程式設計方式存取 Outlook 連絡人
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c46df4218a12c0f9a155567aeee0c007d0a19c53
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598202"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>HOW TO：以程式設計方式存取 Outlook 連絡人
  此範例會尋找其最後一個的名稱包含指定之搜尋字串的所有連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

-   連絡人的姓氏包含字串"**Na 」** (例如 Tzipi Butnaru) 中**連絡人**資料夾。

## <a name="see-also"></a>另請參閱
- [使用連絡人項目](../vsto/working-with-contact-items.md)
- [如何：以程式設計方式將項目新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以程式設計方式在連絡人電子郵件地址搜尋](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [如何：以程式設計方式刪除 Outlook 連絡人](../vsto/how-to-programmatically-delete-outlook-contacts.md)
