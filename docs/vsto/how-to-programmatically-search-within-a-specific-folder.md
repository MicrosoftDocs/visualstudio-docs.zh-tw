---
title: 如何：以程式設計方式在特定資料夾中搜尋
description: 瞭解如何使用 Visual Studio，以程式設計方式在特定的 Microsoft Outlook 資料夾內搜尋。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: fa569a2c301cb495f109a612d817937159c257c6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524543"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>如何：以程式設計方式在特定資料夾中搜尋
  這個程式碼範例 `Find` 會使用和方法，在 `FindNext` [ **收件** 匣] 中的電子郵件訊息的 [主旨] 欄位中搜尋文字。 這個方法會使用字串篩選來檢查字母 T 是否為文字的開頭字母 `Subject` 。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [Outlook 物件模型總覽](../vsto/outlook-object-model-overview.md)
- [如何：以程式設計方式依名稱取出資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
