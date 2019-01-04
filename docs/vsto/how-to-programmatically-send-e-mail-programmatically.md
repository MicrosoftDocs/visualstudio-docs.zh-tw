---
title: HOW TO：以程式設計方式傳送電子郵件
ms.date: 02/02/2017
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
ms.openlocfilehash: 91e59cc8d7bd0115a59c71f13e8e2dc200336b29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840417"
---
# <a name="how-to-programmatically-send-email"></a>HOW TO：以程式設計方式傳送電子郵件  
  此範例會將電子郵件訊息傳送至擁有的網域名稱的連絡人**example.com**中電子郵件地址。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   擁有的網域名稱的連絡人**example.com**中電子郵件地址。  
  
## <a name="robust-programming"></a>穩固程式設計  
 請勿移除網域名稱的搜尋篩選條件程式碼**example.com**。 您的解決方案會傳送電子郵件給所有的連絡人，如果您移除篩選。  
  
## <a name="see-also"></a>另請參閱  
 [使用郵件項目](../vsto/working-with-mail-items.md)   
 [如何：以程式設計方式建立電子郵件項目](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [如何：以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
