---
title: "如何： 以程式設計方式存取 Outlook 連絡人 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: contacts [Office development in Visual Studio], searching
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ee2c597c1a3b6a7c068c8206a87195779877461
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
  