---
title: 如何：以程式設計方式建立自訂資料夾專案
description: 瞭解如何在 Microsoft Outlook 中使用 Visual Studio，以程式設計方式建立自訂資料夾專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], creating
- Outlook folders [Office development in Visual Studio], custom
author: John-Hart
ms.author: johnhart
ms.workload:
- office
ms.openlocfilehash: f149758665e5d7a7cdf7f4edd5d926e1de632dca
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527791"
---
# <a name="how-to-programmatically-create-custom-folder-items"></a>如何：以程式設計方式建立自訂資料夾專案
  此範例會在 Microsoft Office Outlook 中建立新資料夾。 用來登入的使用者名稱會用於資料夾名稱。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_CustFolderItem#1](../vsto/codesnippet/CSharp/Trin_OL_CustFolderItem/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [如何：以程式設計方式將專案新增至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [如何：以程式設計方式建立約會](../vsto/how-to-programmatically-create-appointments.md)
