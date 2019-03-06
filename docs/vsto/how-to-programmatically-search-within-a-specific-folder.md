---
title: HOW TO：以程式設計方式在特定資料夾中搜尋
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638006"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>HOW TO：以程式設計方式在特定資料夾中搜尋
  此程式碼範例會使用`Find`並`FindNext`方法來搜尋的電子郵件訊息的主旨欄位中的文字**收件匣**。 這個方法會使用字串篩選條件來檢查為起始的字母的字母 T`Subject`文字。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>範例
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>另請參閱
- [使用資料夾](../vsto/working-with-folders.md)
- [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)
- [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
