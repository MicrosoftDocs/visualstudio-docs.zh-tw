---
title: 以程式設計方式從 Outlook 電子郵件專案儲存附件
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9fbe6099a8928397a7d885ac72c4f34da2da6af0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545882"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>如何：以程式設計方式從 Outlook 電子郵件專案儲存附件

這個範例會在收件匣中收到郵件時，將電子郵件附件儲存至指定的資料夾。

> [!IMPORTANT]
> 只有當您在 C 目錄的根目錄新增名為**TestFileSave**的資料夾時，此範例才能運作。

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱

- [使用訊息項目](../vsto/working-with-mail-items.md)
- [如何：以程式設計方式依名稱取得資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [如何：以程式設計方式在特定資料夾內搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
