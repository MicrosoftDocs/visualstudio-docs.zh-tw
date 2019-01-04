---
title: HOW TO：以程式設計方式在連絡人電子郵件地址搜尋
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 767c75bff42bc19b70d4b6dcd35da16c4bb4c099
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893350"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>HOW TO：以程式設計方式在連絡人電子郵件地址搜尋
  本範例會在 [連絡人] 資料夾中，搜尋其電子郵件地址中有網域名稱 **example.com** 的連絡人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   其電子郵件地址中有網域名稱 **example.com** (例如 `somebody@example.com`)，並具有名字和姓氏的連絡人。  
  
## <a name="see-also"></a>另請參閱  
 [使用連絡人項目](../vsto/working-with-contact-items.md)   
 [如何：以程式設計方式傳送電子郵件](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [如何：以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以程式設計方式將項目新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
