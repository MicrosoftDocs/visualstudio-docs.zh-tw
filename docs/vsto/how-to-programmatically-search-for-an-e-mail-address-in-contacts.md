---
title: 以程式設計方式在連絡人中尋找電子郵件地址
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a4a9d52ae16b77b40461a314c6008f8cdd741bcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537640"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>如何：以程式設計方式在連絡人中搜尋電子郵件地址
  本範例會在 [連絡人] 資料夾中，搜尋其電子郵件地址中有網域名稱 **example.com** 的連絡人。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 其電子郵件地址中有網域名稱 **example.com** (例如 `somebody@example.com`)，並具有名字和姓氏的連絡人。

## <a name="see-also"></a>另請參閱
- [使用連絡人項目](../vsto/working-with-contact-items.md)
- [如何：以程式設計方式傳送電子郵件](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [如何：以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [如何：以程式設計方式將專案新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
