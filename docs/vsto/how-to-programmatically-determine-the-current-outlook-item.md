---
title: 如何：以程式設計方式判斷目前的 Outlook 專案
description: 瞭解如何以程式設計方式判斷目前的 Microsoft Outlook 專案。 此範例使用 SelectionChange 事件。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 720028528c036bf4485ca529f735fd26b1ff6e9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963831"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>如何：以程式設計方式判斷目前的 Outlook 專案
  這個範例會使用 `Explorer.SelectionChange` 事件來顯示目前資料夾的名稱，以及有關所選取專案的一些資訊。 然後，程式碼會顯示選取的專案。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- Microsoft Office Outlook 中的約會、連絡人和電子郵件專案。

## <a name="see-also"></a>另請參閱
- [Outlook 物件模型總覽](../vsto/outlook-object-model-overview.md)
- [如何：以程式設計方式依名稱取出資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
