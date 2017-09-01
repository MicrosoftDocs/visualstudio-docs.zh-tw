---
title: 'How to: Programmatically Search Within a Specific Folder | Microsoft Docs'
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
- Outlook folders [Office development in Visual Studio], searching
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: 30
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 92a7df7611d40f1fe9c332cc5795a23fc0f2efb5
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>How to: Programmatically Search Within a Specific Folder
  This code example uses the `Find` and `FindNext` methods to search for text in the subject field of e-mail messages that are in the **Inbox**. This method uses a string filter to check for the letter T as the starting letter of the `Subject` text.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Example  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>See Also  
 [Working with Folders](../vsto/working-with-folders.md)   
 [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)   
 [How to: Programmatically Retrieve a Folder by Name](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  
