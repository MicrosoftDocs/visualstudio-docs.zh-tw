---
title: HOW TO：以程式設計方式傳送電子郵件
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72d033add2ba8320b14eebd5af700ab225d34410
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551763"
---
# <a name="how-to-programmatically-send-email"></a>作法：以程式設計方式傳送電子郵件
  這個範例會將電子郵件訊息傳送給在其電子郵件地址中有功能變數名稱**example.com**的連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 其電子郵件地址中有功能變數名稱**example.com**的連絡人。

## <a name="robust-programming"></a>穩固程式設計
 請勿移除搜尋功能變數名稱**example.com**的篩選器程式碼。 如果您移除篩選, 解決方案會將電子郵件訊息傳送給您的所有連絡人。

## <a name="see-also"></a>另請參閱
- [使用訊息項目](../vsto/working-with-mail-items.md)
- [如何：以程式設計方式建立電子郵件專案](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [如何：以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
