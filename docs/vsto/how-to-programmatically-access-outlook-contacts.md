---
title: 如何： 以程式設計方式存取 Outlook 連絡人 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c48a58a4215ce73bcc6e9f4593819cbbdbed1693
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>如何：以程式設計方式存取 Outlook 連絡人
  此範例會尋找所有的連絡人姓氏含有指定之搜尋字串。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   連絡人姓氏含有字串"**Na"** (例如，Tzipi Butnaru) 中**連絡人**資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [使用連絡人項目](../vsto/working-with-contact-items.md)   
 [如何： 以程式設計方式將項目加入 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [如何： 以程式設計方式搜尋特定連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [如何： 以程式設計方式在連絡人電子郵件地址搜尋](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [如何：以程式設計方式刪除 Outlook 連絡人](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  