---
title: 如何：以程式設計方式在 Outlook 中移動專案
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 97f686a47d18fa91909de489f12f9c7a8c1306d1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519908"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>如何：以程式設計方式在 Outlook 中移動專案
  這個範例會將未讀取的電子郵件訊息從**收件**匣移至名為**Test**的資料夾。 此範例只會在欄位中移動具有「**測試**」一詞的訊息 `Subject` 。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 名為**Test**的 Outlook 郵件資料夾。

- 在欄位中抵達「**測試**」一詞的電子郵件訊息 `Subject` 。

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [如何：以程式設計方式依名稱取得資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [如何：以程式設計方式在特定資料夾內搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
