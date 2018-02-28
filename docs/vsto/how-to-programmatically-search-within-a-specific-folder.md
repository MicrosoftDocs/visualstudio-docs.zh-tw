---
title: "如何： 以程式設計方式在特定資料夾中搜尋 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 71b9da77857bb82a27f6bd6ae057a1df1fca8a1d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>如何：以程式設計方式在特定資料夾中搜尋
  這個程式碼範例會使用`Find`和`FindNext`方法來搜尋文字的電子郵件訊息的主旨欄位正在**收件匣**。 這個方法會使用字串篩選條件來檢查為起始的字母的字母 T`Subject`文字。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)   
 [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  