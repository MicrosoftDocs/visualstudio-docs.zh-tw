---
title: 如何： 以程式設計方式在特定資料夾中搜尋
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64df4180e533f254927ae134ed005b0626dfdde8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671414"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>如何： 以程式設計方式在特定資料夾中搜尋
  此程式碼範例會使用`Find`並`FindNext`方法來搜尋的電子郵件訊息的主旨欄位中的文字**收件匣**。 這個方法會使用字串篩選條件來檢查為起始的字母的字母 T`Subject`文字。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>另請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)   
 [如何： 以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  