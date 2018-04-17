---
title: 如何： 以程式設計方式傳送電子郵件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3ee656a8a4965f01969bad19d66d0ea6215bcbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>另請參閱  
 [使用郵件項目](../vsto/working-with-mail-items.md)   
 [如何： 以程式設計方式建立電子郵件項目](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [如何： 以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  