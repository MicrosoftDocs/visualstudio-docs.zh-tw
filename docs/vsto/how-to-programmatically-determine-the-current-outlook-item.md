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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10b8bd8103e80040519b9e3c5546f892da326202
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526794"
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
