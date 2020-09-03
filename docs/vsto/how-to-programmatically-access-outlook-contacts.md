---
title: 如何：以程式設計方式存取 Outlook 連絡人
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 2f6d64512af660392c10082e3bcd3c26b6bc6885
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520090"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>如何：以程式設計方式存取 Outlook 連絡人
  此範例會尋找姓氏包含指定之搜尋字串的所有連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 姓氏包含 "**Na"** 字串的連絡人 (例如，在 [ **連絡人** ] 資料夾中的 Tzipi Butnaru) 。

## <a name="see-also"></a>另請參閱
- [使用連絡人項目](../vsto/working-with-contact-items.md)
- [如何：以程式設計方式將專案新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以程式設計方式在連絡人中搜尋電子郵件地址](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [如何：以程式設計方式刪除 Outlook 連絡人](../vsto/how-to-programmatically-delete-outlook-contacts.md)
