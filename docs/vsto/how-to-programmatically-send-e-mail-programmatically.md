---
title: "如何： 以程式設計方式傳送電子郵件 |Microsoft 文件"
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
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39a0ebee37c57630649f680d14aa8fef22833225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-send-e-mail"></a>如何： 以程式設計方式傳送電子郵件  
  這個範例會將電子郵件訊息傳送至具有網域名稱的連絡人**example.com**在他們的電子郵件地址。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   有網域名稱的連絡人**example.com**在他們的電子郵件地址。  
  
## <a name="robust-programming"></a>穩固程式設計  
 請勿移除網域名稱中搜尋的篩選器程式碼**example.com**。您的方案會傳送電子郵件給所有的連絡人，如果移除篩選。  
  
## <a name="see-also"></a>請參閱  
 [使用郵件項目](../vsto/working-with-mail-items.md)   
 [如何： 以程式設計方式建立電子郵件項目](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [如何： 以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  