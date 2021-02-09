---
title: 如何：以程式設計方式傳送電子郵件
description: 使用 Visual Studio 以程式設計方式從 Microsoft Outlook 傳送電子郵件。 此範例會將電子郵件訊息傳送給名稱為 example.com 的連絡人。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c2b702d2986315ce32a9ab489db239f2c784f3e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877859"
---
# <a name="how-to-programmatically-send-email"></a>如何：以程式設計方式傳送電子郵件
  此範例會將電子郵件訊息傳送給其電子郵件地址中有功能變數名稱 **example.com** 的連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 其電子郵件地址中有功能變數名稱 **example.com** 的連絡人。

## <a name="robust-programming"></a>穩固程式設計
 請勿移除搜尋功能變數名稱 **example.com** 的篩選器程式碼。 如果您移除篩選準則，您的方案會將電子郵件訊息傳送給您的所有連絡人。

## <a name="see-also"></a>另請參閱
- [使用訊息項目](../vsto/working-with-mail-items.md)
- [如何：以程式設計方式建立電子郵件專案](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [如何：以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
