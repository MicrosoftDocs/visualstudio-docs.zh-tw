---
title: 如何： 以程式設計方式在 Outlook 中移動項目
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257718"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>如何： 以程式設計方式在 Outlook 中移動項目
  此範例中移動的未閱讀的電子郵件訊息**收件匣**資料夾，名為**測試**。 此範例只會移動有這個字的訊息**測試**在`Subject`欄位。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Outlook 郵件資料夾名為**測試**。  
  
-   電子郵件訊息的文字**測試**在`Subject`欄位。  
  
## <a name="see-also"></a>另請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [如何： 以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何： 以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [如何： 以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  