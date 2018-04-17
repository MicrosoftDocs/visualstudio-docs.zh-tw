---
title: 如何： 以程式設計方式使網頁與 Outlook 資料夾產生關聯 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5495066b05ded6fc49dfe92ed489932d8c75b24d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>如何：以程式設計方式使網頁與 Outlook 資料夾產生關聯
  這個範例會檢查名為的資料夾`HtmlView`Microsoft Office Outlook 中。 如果資料夾不存在，程式碼會建立資料夾，並指派給它的網頁。 如果資料夾已經存在，程式碼會顯示資料夾內容。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>另請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [如何： 以程式設計方式擷取名稱的資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以程式設計方式建立自訂資料夾項目](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  