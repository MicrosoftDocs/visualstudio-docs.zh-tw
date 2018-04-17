---
title: 如何： 以程式設計方式儲存從 Outlook 電子郵件項目附件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b3ca0f8c86b31576fd5ce219a536725431b27007
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-attachments-from-outlook-e-mail-items"></a>如何：以程式設計方式從 Outlook 電子郵件項目儲存附件
  這個範例會在收件匣中收到郵件時，將電子郵件附件儲存至指定的資料夾。  
  
> [!IMPORTANT]  
>  這個範例只有在您加入名為的資料夾**TestFileSave** C 目錄的根目錄。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>另請參閱  
 [使用郵件項目](../vsto/working-with-mail-items.md)   
 [如何： 以程式設計方式擷取名稱的資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何： 以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  