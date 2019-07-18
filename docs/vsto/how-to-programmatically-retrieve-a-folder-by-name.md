---
title: HOW TO：以程式設計方式依名稱擷取資料夾
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a494f954f3f670fb796b33a0dbd01e2512ad1d26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955725"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>HOW TO：以程式設計方式依名稱擷取資料夾
  此範例會取得命名自訂資料夾的參考，並接著會顯示資料夾的內容。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

- 名為 TestFolder 的資料夾。

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以程式設計方式建立自訂資料夾項目](../vsto/how-to-programmatically-create-custom-folder-items.md)
