---
title: 如何：以程式設計方式存取 Outlook 連絡人
description: 瞭解如何以程式設計方式存取 Outlook 連絡人。 此範例會尋找姓氏包含指定之搜尋字串的所有連絡人。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 08e9d9ea69985a26a9688152f5c3b028caf75300
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828900"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>如何：以程式設計方式存取 Outlook 連絡人
  此範例會尋找姓氏包含指定之搜尋字串的所有連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb" id="Snippet1":::


## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 姓氏包含 "**Na"** 字串的連絡人 (例如，在 [ **連絡人** ] 資料夾中的 Tzipi Butnaru) 。

## <a name="see-also"></a>另請參閱
- [使用連絡人項目](../vsto/working-with-contact-items.md)
- [如何：以程式設計方式將專案新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以程式設計方式在連絡人中搜尋電子郵件地址](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [如何：以程式設計方式刪除 Outlook 連絡人](../vsto/how-to-programmatically-delete-outlook-contacts.md)
