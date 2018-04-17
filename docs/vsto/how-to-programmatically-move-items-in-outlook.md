---
title: 如何： 以程式設計方式在 Outlook 中移動項目 |Microsoft 文件
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
ms.openlocfilehash: a9eca20d533ba429db8b4227d5620c507fd805a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>如何：以程式設計方式在 Outlook 中移動項目
  本範例將讀取的電子郵件訊息從**收件匣**到名為**測試**。 範例只會將郵件移，讓 word**測試**中`Subject`欄位。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 Outlook 郵件資料夾**測試**。  
  
-   電子郵件訊息到達的字**測試**中`Subject`欄位。  
  
## <a name="see-also"></a>另請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [如何： 以程式設計方式擷取名稱的資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何： 以程式設計方式搜尋特定的資料夾中](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  