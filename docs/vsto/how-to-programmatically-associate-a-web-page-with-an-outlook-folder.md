---
title: HOW TO：以程式設計方式使網頁與 Outlook 資料夾產生關聯
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6dc6bec7ecbf872d10045cb24e007edec893585
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089631"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>HOW TO：以程式設計方式使網頁與 Outlook 資料夾產生關聯
  這個範例會檢查名為的資料夾`HtmlView`在 Microsoft Office Outlook 中。 如果資料夾不存在，程式碼會建立資料夾，並指派給它的網頁。 如果資料夾存在，程式碼會顯示資料夾內容。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>另請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以程式設計方式建立自訂資料夾項目](../vsto/how-to-programmatically-create-custom-folder-items.md)  
