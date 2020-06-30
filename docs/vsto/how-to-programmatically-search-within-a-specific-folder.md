---
title: 如何：以程式設計方式在特定資料夾內搜尋
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f5e0f098edcffce07eb2c3f243b994d1a53cdf9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547013"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>如何：以程式設計方式在特定資料夾內搜尋
  這個程式碼範例會使用和方法，在 [ `Find` `FindNext` **收件**匣] 中的電子郵件訊息的 [主旨] 欄位中搜尋文字。 這個方法會使用字串篩選來檢查字母 T 是否為文字的起始字母 `Subject` 。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [Outlook 物件模型總覽](../vsto/outlook-object-model-overview.md)
- [如何：以程式設計方式依名稱取得資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
