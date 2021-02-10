---
title: 如何：以程式設計方式依名稱取出資料夾
description: 瞭解如何使用 Visual Studio 以程式設計方式依名稱取出資料夾，然後顯示資料夾的內容。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c05f8bc0174807a5336a9d9f79ac3dc81e87476e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953873"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>如何：以程式設計方式依名稱取出資料夾
  這個範例會取得名為自訂資料夾的參考，然後顯示資料夾的內容。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 名為 >testfolder 的資料夾。

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以程式設計方式建立自訂資料夾專案](../vsto/how-to-programmatically-create-custom-folder-items.md)
