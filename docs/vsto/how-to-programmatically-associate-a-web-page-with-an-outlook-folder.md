---
title: 將網頁與 Outlook 資料夾產生關聯
description: 瞭解如何將網頁與 Microsoft Office Outlook 資料夾產生關聯。 此範例會檢查 Outlook 中名為 HtmlView 的資料夾。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 35fad43f78d654cfaf9e06c1f432c620da830dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885569"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>將網頁與 Outlook 資料夾產生關聯

  這個範例會檢查 Microsoft Office Outlook 中所指定的資料夾 `HtmlView` 。 如果資料夾不存在，則程式碼會建立資料夾，並將網頁指派給它。 如果資料夾存在，則程式碼會顯示資料夾內容。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [如何：以程式設計方式依名稱取出資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [如何：以程式設計方式建立自訂資料夾專案](../vsto/how-to-programmatically-create-custom-folder-items.md)
