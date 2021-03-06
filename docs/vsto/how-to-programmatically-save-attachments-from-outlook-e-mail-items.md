---
title: 以程式設計方式從 Outlook 電子郵件專案儲存附件
description: 瞭解如何使用 Visual Studio 以程式設計方式從 Microsoft Outlook 電子郵件專案儲存附件。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ad64593f91e14bcfd993929420764869a8359e3e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826690"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>如何：以程式設計方式從 Outlook 電子郵件專案儲存附件

這個範例會在收件匣中收到郵件時，將電子郵件附件儲存至指定的資料夾。

> [!IMPORTANT]
> 此範例僅適用于您在 C 目錄的根目錄下新增名為 **TestFileSave** 的資料夾。

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例

:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>另請參閱

- [使用訊息項目](../vsto/working-with-mail-items.md)
- [如何：以程式設計方式依名稱取出資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
