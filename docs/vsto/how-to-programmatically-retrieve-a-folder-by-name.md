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
ms.openlocfilehash: 2c08f3d2f7ddcd3d9f1ad0eb0b937905d6449d00
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620885"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>HOW TO：以程式設計方式依名稱擷取資料夾
  此範例會取得命名自訂資料夾的參考，並接著會顯示資料夾的內容。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要：

-   名為 TestFolder 的資料夾。

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以程式設計方式建立自訂資料夾項目](../vsto/how-to-programmatically-create-custom-folder-items.md)
