---
title: 'How to: Programmatically Move Items in Outlook | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: d7cf56d5e351d045f213a254474e5c24bcd9e206
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-move-items-in-outlook"></a>How to: Programmatically Move Items in Outlook
  This example moves unread e-mail messages from the **Inbox** to a folder named **Test**. The example only moves messages that have the word **Test** in the `Subject` field.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Example  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This example requires:  
  
-   An Outlook mail folder named **Test**.  
  
-   An e-mail message that arrives with the word **Test** in the `Subject` field.  
  
## <a name="see-also"></a>See Also  
 [Working with Folders](../vsto/working-with-folders.md)   
 [How to: Programmatically Retrieve a Folder by Name](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [How to: Programmatically Search Within a Specific Folder](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [How to: Programmatically Perform Actions When an E-Mail Message Is Received](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  
