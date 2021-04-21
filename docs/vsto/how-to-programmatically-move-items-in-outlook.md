---
title: 如何：以程式設計方式在 Outlook 中移動專案
description: 瞭解如何以程式設計方式在 Microsoft Outlook 中移動專案。 此範例會將未閱讀的電子郵件訊息從收件匣移至名為 Test 的資料夾。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8e951ab393d09506ad4f2d593962ea1826eff09
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826729"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>如何：以程式設計方式在 Outlook 中移動專案
  此範例會將未閱讀的電子郵件訊息從 **收件** 匣移至名為 **Test** 的資料夾。 此範例只會在欄位中移動有文字 **測試** 的訊息 `Subject` 。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 名為 **Test** 的 Outlook 郵件資料夾。

- 在欄位中以文字 **測試** 送達的電子郵件訊息 `Subject` 。

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [如何：以程式設計方式依名稱取出資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
